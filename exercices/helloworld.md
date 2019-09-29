# Hello World 👋

Avant même de lancer la commande magique de Create-react-app, nous allons observer la structure d'une application.

Notre premier rendez-vous se trouve du coté de [BabelJS](https://babeljs.io). Afin de comprendre comment le **JSX** est compiler en JavaScript classique nous aller créer notre premier composant.

Pour se faire nous allons écrire une [Arrow Function](../docs/lexicon.md) (ou Fat Arrow Function).

```javascript
const myApp = () => {
    return(<p> Hello World </p>);
};
```

Babel compile le code en :

```javascript
var myApp = function myApp() {
  return React.createElement("p", null, " Hello World ");
};
```

## [Create-react-app](https://fr.reactjs.org/docs/create-a-new-react-app.html#create-react-app)

Lorsque vous exécutez la commande pour générer un projet via :

`npm create-react-app monApp`

La structure générée comporte 3 dossiers

- **node_modules** qui contient l'ensemble des libraires
- **public** qui contient les assets publiques de notre application
- **src** qui contient les composants et la partie logique de notre application

Une fois l'application executée et ouverte sur le port 3000, le template suggère de modifier le fichier `App.js`. Dans ce fichier, vous trouverez votre premier composant ainsi que d'autres informations vitales à l'éxecution de l'application. 



## Créer un composant

Un composant (React) est un Object (dans ce cas-ci une fonction) qui produit du contenu à afficher sur l'écran. Pour définir notre objet, nous allons créer une fonction. Cette fonction doit retourner un objet qui décrit ce qui doit apparaître sur l'écran. Cette fonction accepte l'injection de données arbitraires via des propriétés ([props](../docs/props.md)).

> Allez Hop ! On supprime tout le contenu du dossier **src** 🗑️ et on crée un fichier index.js vide !

Pour commencer nous allons d'abord créer un composant qui sera un simple élément JSX stocké dans une `const` 

```javascript
const myApp = <h1>Hello World !</h1>;
```

C'est bien beau tout ça mais ça ne fonctionne pas ! C'est parfaitement normal. Pour que le composant soit rendu (à l'affichage), il faut importer les bibliothèques de React nécessaires au fonctionnement et à l'enregistrement du composant. Nous allons donc : 

* Importer les libraires nécessaires

```javascript
	import React from 'react';
	import ReactDOM from 'react-dom';
```
	
* Afficher (render) le composant

```javascript
	ReactDOM.render(myApp, document.getElementById('root'));
```

La librairie **React** décrit comment un composant doit se comporter, comment les assembler et les faire travailler ensemble.

`Import` fait partie d'ES6. Par défaut, les fichiers n'ont pas accès aux variables globales contenues dans d'autres fichiers. Il faut donc les importer.

L'élément que nous avons créé n'est pas réellement un composant. Nous allons donc transformer cette `const` en une fonction.

```javascript
	const myApp = () =>{
		return <h1>Hello World !</h1>;
	}
```

Une autre possibilité et de créer un Class-based component.

```javascript
	class MonPremierComposant extends React.Component {
	  render() {
	    return (
	      <h1>
		Hello world
	      </h1>
	    );
	  }
	};
```

## Déstructurer l'`import` et refactorisation du code
Pour la réalisation de ce composant, nous avons mobilisé deux éléménts provenant de la librairie React (React et Component). Cependant, nous importons toujours l'entièreté de la librairie. Dans un souci d'optimisation, nous allons déstructurer notre `import` pour ne garder que les éléments dont nous avons besoin. Déstructurer est une technique qui permet d'extraire du contenu d'un `Array` ou `Object` vers une nouvelle variable.

```javascript
import React, {Component} from 'react';
```

## Modularisation
Un des gros avantages de React est de décomposer une application en une série de composants qui pourront être réassembler selon différentes configurations. Nous allons donc modulariser notre code afin que notre composant ne se trouvent plus directement dans le fichier d'index.

* Créer un nouveau fichier JavaScript : `nom_du_composant.js`
* Importer les librairies et les déstructurer.
* Créer le composant
* Exporter le composant : `export default nom_du_composant`
* Importer `nom_du_composant` `from` `'chemin_relatif_vers_le_fichier_js`
* Insérer le composant à l'endroit voulu
