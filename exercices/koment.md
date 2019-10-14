# Commentaire

## Les composants
- Comment.js
- CommentBox.js
- CommentForm.js

### Comment.js

La première étape consiste en un découpage de l'interface en HTML. Grâce au JSX, vous allez définir la structure de votre composant sans écrire de JavaScript.

On génère un class-based component avec le raccourci rcc et on découpe l'interface.

```JavaScript
import React, { Component } from 'react'

export default class CommentForm extends Component {
    render() {
        return (
            <article className="comment">
                <header className="comment-header">
                    <h2>
                        Nom de l'auteur
                    </h2>
                </header>
                <p className="comment-body">
                    Le commentaire
                </p>
                <footer className="comment-footer">
                    <a href="#" className="comment-footer-delete">
                        Supprimer le commentaire
                    </a>
                </footer>
            </article>               
        )
    }
}
``` 

Ensuite, on prépare la réception des données passées en props par le parent (CommentBox.js)

```JavaScript
import React, { Component } from 'react'

export default class Comment extends Component {
    
    render() {
        return (
            <article className="comment">
                <header className="comment-header">
                    <h2>
                        {this.props.author}
                    </h2>
                </header>
                <p className="comment-body">
                    {this.props.comment}
                </p>
                <footer className="comment-footer">
                    <a href="#" className="comment-footer-delete">
                        Supprimer le commentaire
                    </a>
                </footer>
            </article>
        )
    } 
} 
```
> N'oubliez pas que les classes en JSX s'écrivent `className`

## CommentBox.js

Ce composant est responsable de l'aggrégation des différents sous-composants qui constituent l'interface (Comment.js et CommentForm.js). Dans un premier temps, définissions la structure HTML de ce composant.

```JavaScript
import React, { Component } from 'react'

export default class CommentBox extends Component {
    
    render() {
        return (
            <React.Fragment>
                <header>
                    <h1 arialevel="1" role="heading">
                        Les commentaires
                    </h1>
                </header>
                <section>
                    <h2 arialevel="2" role="heading">
                        Il y a xx commentaire
                    </h2>
                    <button>
                        Afficher/Masquer les commentaires
                    </button>
                </section>
                <section>
                    <h2 arialevel="2" role="heading">
                        Ajouter un commentaire
                    </h2>
						<form method="get" action"#">
							
						</form>
                </section>
            </React.Fragment>
        )
    }
}
```

> On utilise React.Fragment car React n'accepte qu'un seul élément en return. On utilise cette technique plutôt que d'ajouter des `div` partout dans notre code.

Remarquez qu'il manque le contenu, ou plutôt le(s) composant(s) responsable(s) de l'affichage du contenu des commentaires. 

### Importer, utiliser le composant et lui passer des props
```JavaScript
import React, { Component } from 'react'
import Comment from './Comment'

export default class CommentBox extends Component {
    
    render() {
        return (
            <React.Fragment>
                <header>
                    <h1 arialevel="1" role="heading">
                        Les commentaires
                    </h1>
                </header>
                <section>
                    <h2 arialevel="2" role="heading">
                        Il y a xx commentaire
                    </h2>
                    <button>
                        Afficher/Masquer les commentaires
                    </button>
                    <Comment author="Nom auteur" comment="message à afficher">
                </section>
                <section>
                    <h2 arialevel="2" role="heading">
                        Ajouter un commentaire
                    </h2>
						<form method="get" action"#">
							
						</form>
                </section>
            </React.Fragment>
        )
    }
}
```

Maintenant, rendons notre application un brin plus dynamique en récupérant des données venant du state plutôt que de les passer en dur.

```JavaScript
import React, { Component } from 'react'
import Comment from './Comment'

export default class CommentBox extends Component {
	
	state={
		commentaires:[
            {id: 1, author:"Jean Dupont", comment:"C'est trop cool les props"},
            {id: 2, author:"Reply All", comment: "Bruh look at this rare Pepe I found specially for you. Top kek"}
        ]
	}
	    
    render() {
        return (
            <React.Fragment>
                <header>
                    <h1 arialevel="1" role="heading">
                        Les commentaires
                    </h1>
                </header>
                <section>
                    <h2 arialevel="2" role="heading">
                        Il y a xx commentaire
                    </h2>
                    <button>
                        Afficher/Masquer les commentaires
                    </button>
                    <Comment 	author={this.state.commentaires[0].author}
                    			comment{this.state.commentaires[0].comment}>
                </section>
                <section>
                    <h2 arialevel="2" role="heading">
                        Ajouter un commentaire
                    </h2>
						<form method="get" action"#">
							
						</form>
                </section>
            </React.Fragment>
        )
    }
}
```
Vous constaterez que ce n'est pas très pratique et pas très dynamique d'utiliser ce genre de syntaxe pour générer des commentaires. Nous allons donc créer une fonction qui se chargera de boucler sur le tableau de commentaire présent dans le state.

Nous utilisons la méthode [map()](../docs/js/map.md) sur le tableau de commentaire pour générer une liste de commentaire.

```JavaScript
getComments = () => {

    return this.state.comments.map((comment)=>{
        return(
            <Comment    key={comment.id} 
                        author={comment.author} 
                        comment={comment.comment}/>
        )
      })
}
```
Cette fonction est ensuite utilisée appelée dans le HTML à l'endroit où les commentaires doivent apparaître.

```JavaScript
import React, { Component } from 'react'
import Comment from './Comment'

export default class CommentBox extends Component {
	
	state={
		commentaires:[
            {id: 1, author:"Jean Dupont", comment:"C'est trop cool les props"},
            {id: 2, author:"Reply All", comment: "Bruh look at this rare Pepe I found specially for you. Top kek"}
        ]
	}
	
	getComments = () => {

        return this.state.comments.map((comment)=>{
            return(
                <Comment    key={comment.id} 
                            author={comment.author} 
                            comment={comment.comment}/>
            )
          })
    }
    toggleComment = () =>{
        this.setState({
            showComments: !this.state.showComments
        });
    }

	    
    render() {
    	const comments = this.getComments();
		return (
		    <React.Fragment>
		        <header>
		            <h1 arialevel="1" role="heading">
		                Les commentaires
		            </h1>
		        </header>
		        <section>
		            <h2 arialevel="2" role="heading">
		                Il y a xx commentaire
		            </h2>
		            <button>
		                Afficher/Masquer les commentaires
		            </button>
						{comments}
		        </section>
		        <section>
		            <h2 arialevel="2" role="heading">
		                Ajouter un commentaire
		            </h2>
						<form method="get" action"#">
							
						</form>
		        </section>
		    </React.Fragment>
		)
	}
}
```

### Afficher/masquer le(s) commentaire(s)

Sur le bouton, nous allons ajouter une fonction permettant d'afficher ou de masquer les commentaires. Grâce au [Synthetic Events](https://fr.reactjs.org/docs/events.html#supported-events), vous ne devez plus vous tracasser de la compatibilité entre les naviguateurs.

Ajoutons la fonction `toggleComment` :

```JavaScript
toggleComment = () =>{
    this.setState({
        showComments: !this.state.showComments
    });
}
```
> Utiliser `setState()` permet non seulement de communiquer proprement les changements d'états à React mais également de mettre à jour uniquement la propriété passée en paramètre et non tout l'objet.

Et utilisons là dans notre fonction `render()` :

```JavaScript
<button onClick={this.toggleComment} 
		className="toggleComment">
{this.state.showComments === true ? "Afficher les commentaires" : "Masquer les commentaires"}
</button>
```

## CommentForm.js

Le formulaire dont nous aurons besoin pour cet exercice est structuré de la sorte :

```HTML
<form method="get" action="#">
    <label htmlFor="nom">
        Nom&nbsp;:
    </label>
    <input  type="text" 
            id="nom" 
            name="name" 
            placeholder="Ex:Billy" 
            />
    <label htmlFor="message">
        Message&nbsp;:
    </label>
    <textarea   id="message"
                name="message" 
                placeholder="Ex: C'est vraiment top Kek React">
    </textarea>
    <input type="submit" value="Envoyer" />
</form>
```
Pour qu'il fonctionne il est nécessaire d'ajouter un Synthetic Event, qui, lors de la soumission passe les données au parent pour les ajouter au state.

Cet évènement renvoit vers une fonction qui se charge de la gestion des données.

```JavaScript
import React, { Component } from 'react'

export default class CommentForm extends Component {
    
    handleSubmit = (event) =>{
        event.preventDefault();

        let author = this.author;
        let comment = this.comment;

        this.props.addComment(author.value, comment.value);
    }

    render() {
        return (
            <form method="get" action="#" onSubmit={this.handleSubmit}>
                <label htmlFor="nom">
                    Nom&nbsp;:
                </label>
                <input  type="text" 
                        id="nom" 
                        name="name" 
                        placeholder="Ex:Billy" 
                        ref={(input) => this.author = input}
                        />
                <label htmlFor="message">
                    Message&nbsp;:
                </label>
                <textarea   id="message"
                            name="message" 
                            placeholder="Ex: C'est vraiment top Kek React"
                            ref={(textearea) => this.comment = textearea}>
                </textarea>
                <input type="submit" value="Envoyer" />
            </form>
        )
    }
}
```

Certains d'entre vous sont peut-être perturbé par la syntaxe bizarre utilisée pour les `refs`, arrêtons nous deux minutes et observons cette callback function.

```JavaScript
ref={(input) => this.author = input}
```
On passe une arrow function avec input en paramètre (le noeud HTML) qui est ensuite associée à une nouvelle propriété de la classe (`this.author`). Grâce à cela, nous pouvons accéder au noeud HTML n'importe où dans la classe.

> Cette fonction callback est appelée par React lorsque l'élément est rendu.

La fonction `handleSubmit()` comporte 3 points important. 

Le premier est une méthode qui intercepte la soumission du formulaire. Pour rappel, la méthode  `preventDefault()` de l 'interface `Event` indique à l'agent utilisateur que si l'événement n'est pas traité explicitement, son action par défaut ne doit pas être prise en compte comme elle le serait normalement. En d'autres termes, la soumission du formulaire sera interrompue et la page ne sera pas rafraichie.

Le deuxième est assez simple à comprendre, il s'agit simplement de récupérer les données des inputs via les refs et de les stockées dans des variables.

Le troisième est plus perturbant car il fait référence à une fonction qui n'as pas encore été définie. Il s'agit de la fonction `addComment()` qui est passée en props depuis le parent. C'est un comportement très courant avec React, les parents gèrent les données et les enfants remontent ces données via des callback function passées en props depuis le parent.

Dans le fichier CommentBox.js, nous allons créer la fonction `addComment()` qui prendra deux paramètres :

```JavaScript
addComment = (author, comment) =>{
	// contenu de la fonction
}
```
La fonction prend deux arguments qui serviront à constuire un objet intermédiaire avant de mettre à jour le state.

L'id n'étant pas récupéré depuis le formulaire, nous récupérons la longueur du tableau déjà présent dans le state auquel nous ajoutons 1.

Enfin, on utilise la méthode `concat()` (plutôt que `push()`) car elle retourne un nouveau tableau et permet à React de détecter plus rapidement les changements.

```JavaScript
addComment = (author, comment) =>{
    const newComment = {
        id:this.state.comments.length +1,
        author,
        comment,
    }
    this.setState(
        {
            comments: this.state.comments.concat([newComment])
        }
    );
}
```

On peut enfin passer cette fonction au composant à l'endroit où il est utilisé.

```JavaScript
<CommentForm addComment={this.addComment}/>
```


 