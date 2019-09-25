# The Mighty Lexicon 📖
L'idée est de mettre à jour ce lexique régulièrement en fonction de vos besoins.

## [Arrow Function](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Fonctions/Fonctions_fl%C3%A9ch%C3%A9es)
Une expression de fonction fléchée (arrow function en anglais) permet d’avoir une syntaxe plus courte que les expressions de fonction et ne possède pas ses propres valeurs pour `this`, `arguments`, `super`, ou `new.target`. Les fonctions fléchées sont souvent anonymes et ne sont pas destinées à être utilisées pour déclarer des méthodes.

Avantages :

- Syntaxe concise
- Return implicite (sans les {})
- Pas de Rebind du this

```JavaScript
const maFonction = (arguments) => { 
	// corps de la fonction
}
```
À la place de : 

```JavaScript
function maFonction(arguments){ 
	// corps de la fonction
}
```

## Automatic Semicolon Insertion (ASI)
Certaines instructions JavaScript doivent finir par un point-virgule et sont donc concernées par l'insertion automatique de points-virgules (ASI pour automatic semicolon insertion en anglais) :

* Instruction vide
* instruction de variable, let, const
* import, export, déclaration de module
* Instruction d'expression
* debugger
* continue, break, throw
* return

## Callback function
Une fonction qui est envoyé dans une autre fonction est appelée une callback function.

## Composing 
À définir 

## Fetch
À définir 	

## Hoisting
https://developer.mozilla.org/fr/docs/Glossaire/Hoisting

## Immediately invoked function expression (IIFE)
Est une une fonction qui est exécutée dès la fin de sa déclaration.

## Promises

## Scope
En ES5 la portée d’une variable était uniquement limitée à l’intérieure d’une fonction. Autrement dit, seules les fonctions étaient capables de créer des scopes. maintenant avec let

## Subset
Est un sous ensemble d’élément. Lorsque l’on modifie le contenu d’un tableau ou ses valeurs, l’ensemble des valeurs retournées sont appelées un “subset” ou sous-ensemble;

## This
À définir

## Use strict
“use strict” est un mode strict de javascript qui permet d’éliminer quelques erreurs silencieuses de JavaScript en les changeant en erreurs explicites 

