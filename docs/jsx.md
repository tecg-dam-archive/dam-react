# Le JSX


Les éléments HTML sont traités comme des expressions JavaScript, elles peuvent donc être sauvées dans des variables, passées à une fonction, stockées dans un tableau ou un objet, etc..

```JavaScript
const test = <p> Hello World ! </p>
```


Si une expression JSX porte sur plus d'une ligne, il est impératif de l'imbriquer dans des `()` : 

```JavaScript
const myDiv = (
  <div>
    <h1>Hello world</h1>  
  </div>
);
```
La petite particularité du JSX c'est qu'il ne peut y avoir qu'un seul élément en sortie.

⛔ Ceci est n'est pas correct : 

```Javascript
const mesParagraphes = (
	<p> Paragraphe n°1 </>
	<p> Paragraphe n°2 </>
);
```
✅ Alors que ceci est correct : 

```JavaScript
const mesParagraphes = (
	<div>
		<p> Paragraphe n°1 </>
		<p> Paragraphe n°2 </>
	</div>
);
```