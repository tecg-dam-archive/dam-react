#Le Virtual DOM 

Le DOM virtuel est une représentation en mémoire du DOM qui est réellement présenté à l’utilisateur. Un composant React ne crée pas de HTML mais une représentation sous forme d’objets et de nœuds de ce à quoi le HTML final doit ressembler.

Le virtual-dom va prendre en compte cette représentation, la comparer au DOM réel et en déduire les opérations minimales à exécuter pour que le DOM réel soit conforme au virtuel. C’est grâce à cet outil que React peut partir du principe qu’il est plus simple de “remplacer” toute l’interface quand elle doit être modifiée plutôt que de modifier au fur et à mesure le DOM comme jQuery ou AngularJS pouvaient le faire.

L’intérêt de cette approche est assez simple. On reproche souvent à JavaScript d’être lent alors que c’est DOM qui l’est. Avoir une représentation sous forme d’arbre en JavaScript permet de réaliser beaucoup plus d’opérations, d’utiliser les meilleurs algorithmes de comparaison d’arbres et, cerise sur le gâteau, de faire toutes les modifications du DOM en une opération plutôt qu’au fur et à mesure. Virtual-dom est également bien plus facile à mettre à jour et à améliorer que les différentes implémentations de DOM dans les navigateurs.


## Docs
- [Browser DOM vs Virtual DOM](https://reactkungfu.com/2015/10/the-difference-between-virtual-dom-and-dom/)
- [Comprendre le Dom Virtuel](https://la-cascade.io/comprendre-le-virtual-dom/)
- [https://www.youtube.com/watch?v=Iw2BLUjQo1E](https://www.youtube.com/watch?v=Iw2BLUjQo1E)