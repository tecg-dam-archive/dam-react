# Props

Dans React, il est possible de passer des données du parents vers l'enfant.
La technique est différente selon le type de composants.

## Stateless component (functional component)

La façon la plus simple de passer des informations à un composant stateless est de les passers en  argument (`props` / propriétés). Dans l'exemple suivant, `props` est passé en argument et utilisé à l'endroit voulu. 

```JavaScript
const Menu = (props) =>{
    return (
        <p>
            {props.message}
        </p>
    )
}
```

Lors de l'appel de ce composant par son parent, considérons `index.js`.

```JavaScript
export default class Home extends Component {
	render() {
		return (
				<div>
					<p> 
						Simple paragraphe inutile
					</p>
					<Menu message={"coucou"} />
				</div>
			)
		}
	}
```


## Statefull component (Class component)

Dans le cas d'un composant statefull, il est possible de récupérer/passer des données de différents manières (state, requêtes, props, ...). Dans notre example nous passons simplement des données en `props`. 

###  Pourquoi this ?
Wes Bos passing dynamica data with props 6min -> This = référence au composant instancié.

```JavaScript
export default class Menu extends Component {
    render() {
        return (
            <div>
                {this.props.message}
            </div>
        )
    }
}
```


### Les refs

On utilise `ref` sur un élément que l'on veut référencer et on passe une callback function pour rendre son contenu accessible ailleurs. Le contenu de la fonction callback est assez simple, on passe l'élément en paramètre, on défini une valeur grâce à `this.unReferenceAuChoix` et on lui affecte l'élément passé en paramètre.

```JavaScript
class Parent extends React.Component {
  render() {
    return (
      <input
        ref={(input) => this.notreReferencePourLaSuite = input}
      />
    );
  }
}
```