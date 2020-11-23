# Les Hooks

## Rappel

React propose deux types de composants. 

### Les composants fonctionels 
- une fonction en javascript;
- peu recevoir des props lors de l'appel;
- retourne du JSX;
- souvent utilisé pour afficher du contenu;
- ne contient pas d'état (l'état ou state est ce qui déclenche un nouveau rendu lorsque l'état est modifié);

### les composants à base de classes 
- Peut recevoir des props;
- contient un état/state;
- contient souvent de la logique lié au changement d'état;
- évolue selon un cycle de vie que l'on peut intercepter à des moments précis via ce que l'on appelle des Lifecycle Methods.


## Donc, c'est quoi un Hook ?

Les Hooks sont des fonctions qui permettent de « se brancher » sur la gestion d’état local et de cycle de vie de React depuis des composants fonctionnels. 

Les Hooks ne fonctionnent pas dans des classes : ils vous permettent d’utiliser React sans classes. Dans la documentation de React, il est recommandé un composant à base de classe uniquement s'il n'y a pas d'alternatives.

Les hooks permettent de bénéficier d’un état local et d’autres fonctionnalités de React sans avoir à écrire une classe.

### Hook d'effet ou Hook d'état ?

React fournit quelques Hooks prédéfinis comme `useState` qui est un hook d'état et vous permet d'obtenir un état local pour un composant fonctionnel.

Le Hook d’effet, `useEffect`, permet aux fonctions composants de gérer des effets de bord. Il joue le même rôle que `componentDidMount`, `componentDidUpdate`, et `componentWillUnmount` dans les classes React.


## Mais en pratique ?

En pratique, nous allons faire deux exercices simples pour les deux cas de figures les plus courants : 
- [useState](./usestate.md) qui imite le state des classes
- [useEffect](./useeffect.md) qui permet aux composants de gérer des effets de bord.


## Deux règles

Elles viennent directement de la [documentation React](https://fr.reactjs.org/docs/hooks-rules.html)

- Appelez les Hooks uniquement au niveau racine
	- N’appelez pas de Hooks à l’intérieur de boucles, de code conditionnel ou de fonctions imbriquées.
- Appelez les Hooks uniquement depuis des fonctions React