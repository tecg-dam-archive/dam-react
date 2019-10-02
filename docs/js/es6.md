# ES6

## [Destructurer](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Op%C3%A9rateurs/Affecter_par_d%C3%A9composition) (un objet ou un tableau)

### Déstructurer un objet

En français, on appelle cela une affectation par décomposition (*destructuring*). La technique est assez simple. Considérons l'objet suivant :

```Javascript
const moi = {
	prenom:jean,
	nom:roger,
	age:3000
}
```

Traditionnellement, nous aurions utilisé la technique suivante pour récupérer le nom et le prénom :

```Javascript
const moi = {
	prenom:"jean",
	nom:"roger",
	age:"3000"
}

const prenom = moi.jean;
const nom = moi.roger;
```

Grâce aux nouveautés d'ES6, nous pouvons maintenant écrire ceci :

```Javascript
const moi = {
	prenom:"jean",
	nom:"roger",
	age:"3000"
}

const {prenom, nom} = moi;
```
On déstructure l'objet en deux nouvelles variables (`prenom` et `nom`).

#### Déstructurer et renommer

Dans la même logique, il est possible de déstructurer un objet et de le renommer en même temps.
Reprenons notre exemple précédent et ajoutons quelques éléments dans le tableau.

```Javascript
const moi = {
	prenom:"jean",
	nom:"roger",
	age:"3000",
	location: {
		adresseAuBoulot: "Rue de la poule",
		numeroAdresseBoulot:"43",
		adresseChezMoi:"Chaussée des vignes",
		numeroAdresseChezMoi:"25"
	}	
}

const {adresseChezmoi:adperso, numeroAdresseChezMoi:numperso } = moi.location;
```
#### Déstructurer avec des valeurs par défaut

Imaginons un nouvel objet qui contient les données CSS d'un objet à animer ou à afficher.

```Javascript
const monCSS = {
	height:"auto",
	width:"100%",
}

const {height = "23px", width = "100px", color="black" } = monCSS;
```
Ce qui se passe ici peut paraître bizarre de prime abord mais reste assez logique au final.
L'objet est déstructurer et **si il n'y a pas de valeur pour la clé recherchée**, alors la valeur par défaut est utilisée.

### Déstructurer un tableau

La technique est assez similaire, une seule petite différence, on utilise plus des `{}` mais `des []`.

```Javascript
const moi = [ Jean, Roger, 3000] 
const [nom, prenom, age] = moi;
```

Grâce à la méthode `split()`, il est également possible de déstructurer une chaîne de caractère — par exemple — et d'en créer un tableau immédiatement.

```Javascript
const moi = "Jean, Roger, 3000"; 
const [nom, prenom, age] = moi.split(",");
```
Si votre tableau contient plus d'éléments que ce que vous n'en déstructurez, ceux que vous avez omis seront simplement ignorés.

```Javascript
const moi = "Jean, Roger, 3000, rue des champs, 49, 4020, Liège"; 
const [nom, prenom, age] = moi.split(",");
```

Grâce à l'opérateur [rest](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Fonctions/param%C3%A8tres_du_reste) en ES6 (`...`), il est possible de récupérer la suite des éléments sous forme d'un (sous) tableau.

```Javascript
const moi = "Jean, Roger, 3000, rue des champs, 49, 4020, Liège"; 
const [nom, prenom, age, ...laSuite] = moi.split(",");
```

### Inverser des valeurs

Il est parfois nécessaire d'inverser les valeurs de deux variables. Afin d'éviter de recourir à une variable intermédiaire, il est possible de faire ceci :

```Javascript
let premier = "Jean";
let second = "Paul";

const [premier, second ] = [second, premier];
```

## Spread operator `...` ([syntaxe de décomposition](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Op%C3%A9rateurs/Syntaxe_d%C3%A9composition))

L'opérateur `...` permet d'étendre un itérable (tout ce qui est "bouclable" -> objets, tableaux, chaînes de caractères, noeuds du DOM, etc.).

Prenons l'exemple suivant de plusieurs tableaux contenant différentes informations sur un utilisateur à combiner en un seul tableau.

```Javascript
const basicInfos = ["Jean", "Dupont", "35"];
const adresse = ["Rue Louvrex", "15", "4000", "Liège"]
const business = ["Front-End Developer", "Best Web Comp", "Senior"]

const userInfo = [ ...basicInfos, ...adresse, ...business ];
```

### Conversion depuis une NodeList du DOM

Considérons le cas de figure suivant. Vous devez extraire du contenu hors d'une liste en HTML. Une fois récupérée dans une variable, la liste ne pourra être extraite via la méthode `.map()` car l'objet est une NodeList et non un tableau. Du coup, on utilisera l'opérateur `...` pour décomposer notre sélection en un tableau.

```JavaScript
const noeudHTML = [...document.querySelectorAll('.uneListe li')];
```
> Note:  on pourrait également utiliser la technique `Array.from()`.

### L'opérateur spread `...` dans une fonction

Un cas de figure assez courant est de recevoir une série d'éléments comme paramètres sous forme de tableau et de devoir les passer à une fonction.

```JavaScript
const params = [Jean, Dupont];

function faitCoucou(a,b){
	alert("Hello ${a} ${b}");
}

faitCoucou(...params);
```

## Rest operator `...` ([Paramètre du reste](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Fonctions/param%C3%A8tres_du_reste))

Le paramètre du reste sert à stocker une liste indéfinie de valeur sous forme de tableau.
Prenons l'exemple suivant, vous recevez des données d'un utilisateur sous forme d'un tableau avec au début son nom et son prénom.

```JavaScript
const userData = ["Jean", "Dupont", "score1", "score2", "score3", "score4", "score5"];
const [nom, prenom, ...scores] = userData;
```