#<img src="./img/reactjs.svg" alt="ReactJS, une introduction à la création d'applications mobiles" style="max-width: 100%; height:auto" />

> ReactJS Lesson given at [HEPL](http://www.provincedeliege.be/hauteecole)



## Introduction

### Qu’est-ce qu’est [React](https://fr.reactjs.org/) ?
React est une bibliothèque JavaScript développée par Facebook depuis 2013.

React a d’abord été utilisé par Facebook (sur la plateforme mère), puis sur Instagram avant d’être ouvert au public et utilisé dans des applications telles que Airbnb, Netflix ou encore Dropbox.

React a été pensé pour créer des (grosses) applications avec une quantité importante de données évoluant dans le temps.

### Pourquoi React ?

La question que l'on doit se poser ici est pourquoi cette technologie par rapport à une autre. React est en concurence directe avec d'autres technologiques telles que [Vue](https://vuejs.org/) ou [Angular](https://angular.io/). 

La première chose à retenir est que React est une **bibliothèque** et non un framework (comme Angular). React et Angular répondent donc à des besoins différents. 

L'objectif premier de React est de gérer l'interface utilisateur (évènements, modifications du DOM, envoie des données via formulaires, évolution de ces données dans le temps etc.). 

React est souvent considéré comme le V de [MVC](https://www.codecademy.com/articles/mvc). De ce fait, les autres couches applicatives (routes, stockages, etc.) sont mobilisées en fonction des besoins du projets ([Express](https://expressjs.com/fr), [Firebase](https://firebase.google.com/), [React-Router](https://reacttraining.com/react-router/web/guides/quick-start), [Redux](https://redux.js.org/), [Redux-Offline](https://github.com/redux-offline/redux-offline), etc.).

L'approche adoptée par React pour gérer l'interface utilisateur consiste à diviser les gros blocs logiques en petits **composants**. Il est recommandé de coder les composants afin qu'ils soient **réutilisables** et donc "interfacables". En gros, on vient connecter le parent sur l'enfant. Nous verrons plus en détail comment ce système les composants fonctionnent dans un [chapitre dédié](./docs/component.md).

> Cette architecture implique une gestion particulière du flux des données. Les données descendent vers les composants et l'état remonte vers le(s) parent(s).

Code once, use Everywhere. Grâce à cette philosophie, vous n'allez plus recoder 100x les mêmes composants comme un calendrier, un formulaire de contact, etc.. D'ailleurs, Airbnb, qui utilise React, a mis [son calendrier](https://github.com/airbnb/react-dates) en OpenSource, sympa non ?

L'approche par composant n'est pas nouvelle et elle se heurte à un DOM (coté naigateur) pas très rapide. Pour pallier à ce problème, React utilise un **DOM virtuel** ([Virtual DOM](./docs/vdom.md)) qui est une copie en mémoire du DOM réel.

Enfin, avec React, il est possible d'écrire du html directement dans un fichier JavaScript. Pour se faire, React utilise une surcouche JavaScript, du sucre syntaxique en quelque sorte, appelée [JSX](https://reactjs.org/docs/glossary.html#jsx). Imaginez la puissance de JavaScript et du HTML combinés 😎!

Évidemment, il y a plein d'autres raisons d'utiliser (ou pas) React !
Rappelez vous qu'un projet doit toujours être analysé et ensuite être servi par la/les technologie(s) la/les plus adéquate(s).

## La structure du cours

### En théorie 
- Les pré-requis
	- const/let
	- Object
	- Classes
	- Scope
	- Arrow functions
	- Modules (import/export)
	- ... (spread/rest)
	- Template Literals
	- Destructurer
	- map


- React
	- [Le JSX](./docs/jsx.md)
	- [Les composants](./docs/component.md)
	- [Le Virtual Dom](./docs/vdom.md)
	- [LifeCycle Methods](./docs/lcmethods.md)

### En pratique
- [Hello World !](./exercices/helloworld.md)
- [Compteur](./exercices/counter.md)


### Divers 
- [Les outils](./docs/tools.md)
- [Les liens utiles](./docs/links.md)
- [Aller plus loin](./docs/beyond.md)
