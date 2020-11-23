# `useState`

`useState` est un Hook qui permet d’ajouter l’état local React à des fonctions composants.

Il retourne une paire : 

- a valeur de l’état actuel
- une fonction qui vous permet de la mettre à jour. Cette fonction est similaire à `this.setState` dans une classe, à ceci près qu’elle ne fusionne pas l’ancien état et le nouveau.

## Exemple

Reprenons le compteur que nous avons réalisé lors des premiers cours.

Nous avions écrit ceci via un composant à base de classe :

```
export default class ChildCounter extends Component {
	
	state = {
		count = 0
	}

    render() {
        return (
            <p>
               {this.state.count} 
            </p>
        )
    }
}
```

Avant l'arrivée des Hooks, il n'était pas possible de faire référence à un état local via `this.state` puisqu’il n’y a pas de `this`.

Avec le hook `useState`, il est possible de créer un état local et de le modifier.

```
// on déstructure useState de React.
import React, { useState } from 'react';


unComposant = () => {
  // Déclare une nouvelle variable d'état, que nous appellons « count »
  // initialisons l'état de count à 0
  const [count, setCount] = useState(0);
  
  return(
  		<p>
  			{count}
  		</p>
  )
}
```

Si vous vous demandez ce `const [count, setCount] = useState()` veut dire c'est ce qu'on appelle la « [déstructuration positionnelle](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Op%C3%A9rateurs/Affecter_par_d%C3%A9composition#D%C3%A9composition_d'un_tableau) ». 

Cela signifie que nous créons deux nouvelles variables `count` et `setCount`, avec `count` qui reçoit la première valeur renvoyée par `useState`, et `setFruit` qui reçoit la deuxième. 

### Appeler useState, qu’est-ce que ça fait ? 

Ça déclare une « variable d’état ». Notre variable est appelée `count` mais nous aurions pu l’appeler n’importe comment, par exemple `banane`.

`useState` est une nouvelle façon d’utiliser exactement les mêmes possibilités qu’offre `this.state` dans une classe. Normalement, les variables « disparaissent » quand la fonction s’achève mais les variables d’état sont préservées par React.

### Qu’est-ce qu’on passe à useState comme argument ? 
- Le seul argument à passer au Hook useState() est l’état initial.
- Contrairement à ce qui se passe dans les classes, l’état local n’est pas obligatoirement un objet. 


### Que renvoie useState ? 
Elle renvoie une paire de valeurs : 

- l’état actuel
- une fonction pour le modifier. 

C’est pourquoi nous écrivons `const [count, setCount] = useState()`.

C’est semblable à `this.state.count` et `this.setState` dans une classe, mais ici nous les récupérons en même temps.

## En pratique

### comment lire l’état ?

Dans une classe nous ferions ceci :

```
export default class ChildCounter extends Component {
	
	state = {
		count = 0
	}

    render() {
        return (
            <p>
            		{this.state.count} 
            </p>
        )
    }
}
```


Et dans notre fonction actuelle nous faisons simplement ceci :


```
import React, { useState } from 'react';


unComposant = () => {
  const [count, setCount] = useState(0);
  
  return(
  	<p>
  		{count}
  	</p>
  )
}
```

### Comment mettre à jour l'état
Dans une classe nous ferions ceci :

```
export default class ChildCounter extends Component {
	
	state = {
		count = 0
	}
	
	handleClick () => {
		this.setState({ count: this.state.count + 1 })
	}
	
    render() {
        return (
            <p>
            		{this.state.count} 
            </p>
            <button onClick={handleClick}>
					Incrémenter
	        </button>
        )
    }
}
```


Et dans notre fonction actuelle nous faisons simplement ceci :


```
import React, { useState } from 'react';


unComposant = () => {
	const [count, setCount] = useState(0);
  
	handleClick () => {
		setCount(count + 1))
	}
  
	return (
		<p>
			{count} 
		</p>
		<button onClick={handleClick}>
			Incrémenter
		</button>
	)
}
```


## Annexes, aides et liens

- https://fr.reactjs.org/docs/hooks-state.html
- https://rednet.io/2020-05-04-les-hooks-la-base.html