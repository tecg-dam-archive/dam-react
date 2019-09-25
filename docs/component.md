# Les composants

Historiquement (avant ES6/ES2015), le seul moyen de créer un composant dans React était `React.createClass()`. Avec l'[introduction des classes](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Classes) (qui sont des fonctions spéciales), les développeurs ont dérivé cette unique déclaration.

Aujourd'hui, il existe plusieurs façons de déclarer un composant. Il est important de noter que ces méthodes sont plus ou moins identiques à quelques détails près bien qu'elles ne soient pas 100% interchangeables.

* `React.createClass`: syntaxe historique, supportée par ES5. Avec cette syntaxe il est possible d'accéder aux méthodes telles que `getDefaultProps` et `componentDidMount`.


* `class ClassName extends React.Component` : réclame moins de code, mais nécessite d'étendre la class Component de React. Cette syntaxe ne dispose pas des mixins. Comme toute classe, elle possède un constructeur (qui appelle le constructeur de la classe dont elle hérite via la méthode super).

On assigne en effet à this, notre objet courant (le composant React que l’on est en train de créer), un attribut que l’on nomme state. Dans le cadre de notre exemple, on l’initialise en créant une clé happy ayant la valeur false.

> Ce state correspond à l’état interne de notre composant, contrairement au props venant du composant parent. Ces deux éléments sont essentiels en React.

Ensuite, on trouve la méthode `render()` (qui ne peut rendre qu'un composant), méthode **indispensable** dans tout composant React stateful. C’est cette fonction qui sera appelée pour rendre le composant. (Pour faire une lien avec la première partie, on peut dire qu’un composant fonctionnel ne se définit que par sa méthode render).

La fonction `getInitialState()` permet de déclarer les données par défault à l'initialisation du composant. On peut ensuite les récupérer via `this.state`.

* **the stateless functional component** : Ce composant est une fonction (_function -> functional component_) dont on ne peut pas changer l'état depuis l'extérieur. Pour le modifier il faut lui passer un objet en paramètre : un objet `props`.

> Toujours utiliser une **lettre majuscule** nommer vos composants. `<div />` est un élément du DOM, `<Formulaire />` est un composant.


### Ressources
* [React on ES6+](https://babeljs.io/blog/2015/06/07/react-on-es6-plus)
* [super et constructor](http://cheng.logdown.com/posts/2016/03/26/683329)


## FAQ
* **Pourquoi `super()` ?**

* **Dans une promise est-ce que `data =>` est obligatoire ou peut-on nommer ce paramètre autrement ?**

* **Pourquoi les composants débutent-ils par une majuscule ?**

  En JSX, les noms en bas-de-casse sont considérés comme des balises HTML. Par contre, les mots-clés en bas-de-casse avec un `.` ne sont pas des balises.

  Voici quelques exemples :
  
  ```javascript
  <component /> compile en React.createElement('component') (balise html)

  <Component /> compile en React.createElement(Component)

  <obj.component /> compile en React.createElement(obj.component)
  ```

* **ReactDOM.render vs render() LifeCycle ?** 