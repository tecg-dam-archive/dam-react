# `useEffect`

Vous avez surement déjà réalisé un chargement de données distantes, depuis une API ou autre. Ces opérations s'appellent des « effets de bord » (ou effets pour faire court) parce qu’elles peuvent affecter d’autres composants et ne peuvent être réalisées pendant l’affichage.

Il existe deux grands types d’effets de bord dans les composants React : ceux qui ne nécessitent pas de nettoyage, et ceux qui en ont besoin. 

##

Le Hook d’effet, `useEffect`, permet aux fonctions composants de gérer des effets de bord. Il joue le même rôle que `componentDidMount`, `componentDidUpdate`, et `componentWillUnmount` dans les classes React.

## Comment cela fonctionne ?

Lorsque vous appelez `useEffect`, vous dites à React de lancer votre fonction d’« effet » après qu’il ait mis à jour le DOM. Les effets étant déclarés au sein du composant, ils ont accès à ses props et son état. Par défaut, React exécute les effets après chaque affichage, y compris le premier. 

### Sans nettoyage 

Parfois, nous souhaitons exécuter du code supplémentaire après que React a mis à jour le DOM. Les requêtes réseau, les modifications manuelles du DOM, et la journalisation sont des exemples courants d’effets qui ne nécessitent aucun nettoyage. Cela s’explique par le fait qu’ils peuvent être oubliés immédiatement après leur exécution.

#### Exemple

```
import React, { useState, useEffect } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    document.title = `Vous avez cliqué ${count} fois`;
  });

  return (
    <div>
      <p>Vous avez cliqué {count} fois</p>
      <button onClick={() => setCount(count + 1)}>
        Cliquez ici
      </button>
    </div>
  );
}
```

On utilise ce Hook (`useState`) pour indiquer à React que notre composant doit exécuter quelque chose après chaque affichage. React enregistre la fonction passée en argument (que nous appellerons « effet »), et l’appellera plus tard, après avoir mis à jour le DOM

L’effet ci-dessus met à jour le titre du document, mais il pourrait aussi bien charger des données distantes, ou appeler n’importe quelle autre API.

Le fait d’appeler `useEffect` à l’intérieur de notre composant nous permet d’accéder à la variable d’état count (ou à n’importe quelle prop) directement depuis l’effet

`useEffect` est appelée après chaque affichage. La fonction est exécutée par défaut après le premier affichage et après chaque mise à jour. Au lieu de penser en termes de « montage » et de « démontage », pensez plutôt que les effets arrivent tout simplement « après l’affichage ». React garantit que le DOM a été mis à jour avant chaque exécution des effets.

Examinons plus en détail cette partie de code : 

```
function Example() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    document.title = `Vous avez cliqué ${count} fois`;
  });
}
```

1. Nous déclarons la variable d’état `count`, puis indiquons à React que nous avons besoin d’utiliser un effet (`useEffect()`). 
2. Nous passons alors une fonction au Hook `useEffect( () => {...} )`. Cette fonction est notre effet. 
3. À l’intérieur de celui-ci, nous mettons à jour le titre du document en utilisant l’API du navigateur `document.title`.


### Avec nettoyage

Nous avons vu précédemment comment écrire des effets de bord ne nécessitant aucun nettoyage. Toutefois, quelques effets peuvent en avoir besoin. Par exemple, nous pourrions souhaiter nous abonner à une source de données externe. Dans ce cas-là, il est impératif de nettoyer par la suite pour éviter les fuites de mémoire ! Comparons les approches à base de classe et de Hooks pour y arriver.

```
import React, {useState, useEffect} from 'react'

export default function Example() {

    const [users, setUsers] = useState([]);

    useEffect(() =>{
        fetch("https://jsonplaceholder.typicode.com/users")
        .then(res => data.json)
        .then(lesData => setUsers(lesData))
    });
    
    return (
        <div>
            
        </div>
    )
}
```

1. Nous importons et déstructurons les éléments dont nous avons besoin depuis la bibliothèque de React.
2. Nous déclarons une nouvelle fonction et l'exportons
3. Nous déstructurons les deux fonctions de notre useState et on l'initialise à un tableau vide puisque ce sont les données que l'on va obtenir de l'API.
4. Nous utilisons `useEffect()` (qui se comporte actuellement comme un `componentDidUpdate()` qui sera donc éxécuté après chaque mise à jour du composant, causant ainsi une boucle infinie)

Heureusement pour nous, il est possible d’indiquer à React de sauter l’exécution d’un effet si certaines valeurs n’ont pas été modifiées entre deux affichages. Pour cela, il suffit de passer une liste comme second argument optionnel à 
useEffect :

```
import React, {useState, useEffect} from 'react'

export default function Example() {

    const [users, setUsers] = useState([]);

    useEffect(() =>{
        fetch("https://jsonplaceholder.typicode.com/users")
        .then(res => data.json)
        .then(lesData => setUsers(lesData))
    },[]);
    
    return (
        <div>
            
        </div>
    )
}
```

Le fait de passer un tableau vide après l'effet bloquera la boucle infinie (car React attend une variable pour comparer les valeurs qui auraient potentiellement changé entre deux affichage, mais ici il n'a rien à comparer, donc il s'arrête) et transformera le comportement de `useEffect()` en un `componentDidMount()`.

