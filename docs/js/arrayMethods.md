# Les méthodes de Array
> Les sources pour cette documentation viennent de [javascript.info](https://javascript.ingo) et [MDN](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Instructions)
 
## Modifier un tableau

Vous connaissez probablement les méthodes suivantes : 

- [push()](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Objets_globaux/Array/push) : `tab.push(...items)` – ajoute un ou plusieurs éléments à la fin d'un tableau
- [pop()](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Objets_globaux/Array/pop) : `tab.pop()` – supprime le dernier élément d'un tableau 
- [shift()](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Objets_globaux/Array/shift) : `tab.shift()` – retirer le premier élément d'un tableau.
- [unshift()](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Objets_globaux/Array/unshift) : `tab.unshift(...items)` – ajoute un ou plusieurs éléments au début d'un tableau

### [Array.splice()](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Objets_globaux/Array/splice)
La méthode splice() modifie le contenu d'un tableau en retirant des éléments et/ou en ajoutant de nouveaux éléments à même le tableau.On peut ainsi vider ou remplacer une partie d'un tableau.

> var tabElementsSupprimes = array.splice(début, nbASupprimer[, élem1[, élem2[, ...]]])


```JavaScript
let arr = ["J'aime", "les", "pommes"];

arr.splice(1, 1); // depuis l'index 1 supprime 1 élément

alert(arr); // ["J'aime", "pommes"]
```

Dans l'exemple suivant, nous enlevons 3 éléments et les remplaçons par 2 autres.

```JavaScript
let arr = ["J'aime", "les", "pommes", "les", "poires"];

// Supprime les 3 premiers éléments et les remplace avec 2 nouveaux
arr.splice(0, 3, "Je n'aime", "pas");

alert( arr ) // ["Je n'aime", "pas", "les", "poires"]
```
Il est également possible de retourner un tableau hors des données supprimées/remplacées.

```JavaScript
let arr = ["J'aime", "les", "pommes", "les", "poires"];

// Supprime les 3 premiers éléments et les remplace avec 2 nouveaux
let deletedElement = arr.splice(0, 3, "Je n'aime", "pas");

alert( deletedElement ) // ["J'aime", "les", "pmmes"]
```

Enfin, on peut ajouter du contenu sans en retirer. Il suffit de préciser que l'on ne supprime rien en mettant deleteCount à 0:

```JavaScript
let arr = ["J'aime", "les", "pommes"];

// depuis l'index 3
// delete 0
// ensuite on ajoute "les" and "poires"
arr.splice(3, 0, "les", "poires");

alert( arr ); // "J'aime", "les", "pommes", "les", "poires"

```

### [Array.map()](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Objets_globaux/Array/map)

La méthode `map()` est une des méthodes les plus utilisées. Elle permet de crée un nouveau tableau avec les résultats de l'appel d'une fonction fournie sur chaque élément du tableau appelant.

```JavaScript
let longueurDesMots = ["Bilbo", "Gandalf", "Nazgul"].map(item => item.length);
alert(longueurDesMots); // 5,7,6
```

## Boucler sur un tableau

### [Array.forEach()](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Objets_globaux/Array/forEach)

La méthode `Array.forEach()` permet de boucler sur chacun des éléments du tableau. Cette méthode exécute la fonction callback une fois pour chaque élément du tableau, dans l'ordre croissant des indices. 


```JavaScript
const tab = ['a', 'b', 'c'];

tab.forEach(function(element) {
  console.log(element);
});

```

### [Array.for of()](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Instructions/for...of)

Cette méthode permet de créer une boucle Array qui parcourt un objet itérable (ce qui inclut les objets Array, Map, Set, String, TypedArray, l'objet arguments, etc.) 

```JavaScript
let tableauItérable = [1, 2, 3];

for (let valeur of tableauItérable) {
  console.log(valeur);
}

```
Mais également sur une chaîne de caractères

```JavaScript
let iterable = 'pixel';

for (let valeur of iterable) {
  console.log(valeur);
}
```

## Chercher dans un tableau


### [Array.find()](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Objets_globaux/Array/find)

Méthode pour trouver un élément dans un tableau à laquelle on passe une fonction test.

```JavaScript
let users = [
	{ Nom:"Paul", Prenom:"Dupont", age:42},
	{ Nom:"Jean", Prenom:"Bibou", age:17},
	{ Nom:"Edouard", Prenom:"Brodinski", age:35}
]; 

let adults = users.find( (user) => {
	return user.age>=18
});

```

### [indexOf](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Objets_globaux/Array/indexOf) / [lastIndexOf](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Objets_globaux/Array/lastIndexOf) / [includes](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Objets_globaux/Array/includes)

Les méthodes tab.indexOf, tab.lastIndexOf et tab.includes ont la même syntaxe et font essentiellement la même chose que leur équivalent pour les chaînes de caractères mais itèrent sur éléments et non sur des caractères.


- `tab.indexOf(item, from)` – Cherche l'élément `item` depuis l'index `from` et retourne l'index où il a été trouvé, sinon retourne -1.
- `tab.lastIndexOf(item, from)` – idem, de droite à gauche.
- `tab.includes(item, from)` – cherche après l'/les élément(s) depuis `from` et retourne `true ` si il existe dans le tableau.


```JavaScript
let tab = [1, 0, false];

alert( tab.indexOf(0) ); // 1
alert( tab.indexOf(false) ); // 2
alert( tab.indexOf(null) ); // -1

alert( tab.includes(1) ); // true
```


## Les autres méthodes

Il existe énormément de méthode pour les tableaux, je vous renvoie donc vers la documentation du [MDN](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Objets_globaux/Array) ou sur [javascript.info](https://javascript.info/array-methods)