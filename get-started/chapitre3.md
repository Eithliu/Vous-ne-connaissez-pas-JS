# Vous ne connaissez pas JS : Get Started - Traduction française de la 2e édition.
--

## Chapitre 3 : Creuser dans les racines de JS
--

Si vous avez lu les chapitres 1 et 2, et pris le temps de digérer sereinement, vous devriez commencer à comprendre JS un
peu mieux. Si vous les avez zappé ou survolé (en particulier le chapitre2), je vous recommande de passer plus de temps
sur ces chapitres.

Dans le chapitre 2, on a survolé la syntaxe, les schémas (ou patterns) et comportement en haut niveau. Dans ce chapitre,
on prêtera attention aux caractéristiques de plus bas niveau de JS qui régissent virtuellement chaque ligne de code
qu'on écrit.

Soyez avertis : Ce chapitre va creuser plus profondément que ce que vous être habitués à connaître à propos d'un langage
de
programmation. Mon but est de vous aider à comprendre le cœur de JS et son fonctionnent, ce qui le fait marcher. Ce
chapitre devrait commencer à répondre aux questions de type "pourquoi ?" qui peuvent vous venir en explorant JS.
Cependant, ce chapitre n'est pas, je le rappelle, une définition exhaustive du langage ; c'est le but de tous les autres
livres de cette série ! Notre but ici est juste de démarrer, et être de plus en plus confortable avec JS, ses flux et
reflux.

Ne vous précipitez pas dans une lecture diagonale, vous vous perdriez. Comme je l'ai déjà répété une douzaine de fois,
prenez votre temps. Même si vous finirez probablement ce chapitre avec encore d'autres questions. Ce n'est pas grave,
parce qu'une autre série de livres n'attends que vous pour être exploré !

### Itération
--

Puisque les programmes sont essentiellement _buildés_ pour traiter de la donnée (et prendre des décisions à propos de
ces données), les schémas/patterns utilisés pour avancer dans les données ont un impact énorme sur la lisibilité du
programme.

Le schéma d'itération existe depuis des décennies et suggère une approche "standardisée" de consommation de données à
partir d'une source, un paquet à la fois. L'idée sous-jacente, c'est que c'est plus facile d'itérer sur la donnée
source, pour progressivement gérer la collection de données en traitant la première partie, puis la suivante, etc.
plutôt qu'en gérant la totalité de la collection en une fois.

Imaginez une structure de données qui représente une requête de type `SELECT` sur une base de données relationnelle, wui
organise les données en suite de lignes. Si cette requête n'a qu'une ou deux lignes, vous pourriez gérer tous les
résultats en une seule fois et assigner chaque ligne à une variable local et réaliser n'importe quelle opération
appropriée sur cette donnée.

Mais si la requête a 100 ou 1000 (ou plus !) lignes, vous aurez besoin d'un traitement itératif pour gérer les
données (comme une boucle, par exemple).

Le schéma d'itération défini une structure de données appelée un "intérateur" qui a une référence à une source de
données sous-jacente (comme les lignes de résultat d'une requête), qui expose une méthode comme `next()`. Appeler
`next()` retourne la donnée suivante (ie, un "enregistrement" ou "ligne" d'une requête à une base de données).

Vous ne savez pas toujours sur combien de données vous allez devoir itérer, donc le schéma/pattern indique son
complétion grâce à une valeur spéciale ou une exception une fois que vous avez itéré sur toute la collection et êtes à
la fin.

L'importance du pattern d'itération 
The importance of the iterator pattern is in adhering to a standard way of processing data iteratively, which creates
cleaner and easier to understand code, as opposed to having every data structure/source define its own custom way of
handling its data.

After many years of various JS community efforts around mutually agreed-upon iteration techniques, ES6 standardized a
specific protocol for the iterator pattern directly in the language. The protocol defines a next() method whose return
is an object called an iterator result; the object has value and done properties, where done is a boolean that is false
until the iteration over the underlying data source is complete.