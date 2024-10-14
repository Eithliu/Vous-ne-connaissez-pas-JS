# Vous ne connaissez pas JS : Get Started - Traduction française de la 2e édition.
--

## Chapitre 2 : Une enquête sur JS
--

La meilleure façon d'apprendre JS est de commencer à écrire du JS.

Pour ce faire, vous avez besoin de comprendre comment le langage fonctionne, et c'est ce sur quoi on va se focaliser ici. Même si vous avez programmé dans d'autres langages auparavant, prenez le temps d'être confortable avec le JS, et assurez-vous de pratiquer en profondeur.

Ce chapitre n'est pas une référence exhaustive de chaque petit bout de syntaxe du langage JS. Ce n'est pas non plus l'amorce d'un "intro complète en JS". Ce n'est pas le but.

En réalité, on va juste survoler quelques-uns des domaines principaux du langage. Notre but ici est de mieux sentir le langage, afin qu'on puisse avancer dans l'écriture de nos propres programmes avec plus d'assurance et de confiance. On va revisiter plusieurs de ces sujets plus en détails au fur et à mesure que vous avancerez dans ce livre et dans le reste de la série.

Ne vous attendez pas à ce que ce chapitre soit un résumé rapide à lire. C'est long et il y a une foule de détails à parcourir. Prenez votre temps.

|ASTUCE:|
|--|
|Si vous êtes encore en train de vous familiariser avec JS, je vous suggère de planifier beaucoup de temps pour travailler au cours de ce chapitre. Prenez chaque section et analysez et explorez le sujet un petit temps. Regardez des programmes conçus en JS et comparez ce que vous voyez au code et explications (et opinions !) qui vous sont présentés ici. Vous tirerez bien plus de cette série de livres avec une solide base en JS. |

## Chaque fichier est un programme.
--

Presque tous les sites web (les applications web) que vous utilisez est la somme de plusieurs fichiers JS (typiquement avec l'extension .js). C'est tentant d'imaginer le truc (l'application) comme un seul programme. Mais JS voit les choses différemment.

En JS, chaque fichier est son propre programme isolé.

La raison pour laquelle c'est important tourne autour de la gestion des erreurs. Puisque JS traite les fichiers comme des programmes, un fichier peut ne pas marcher (durant le traitement/compilation ou l'exécution) et ça ne va pas nécessairement empêcher le fichier suivant d'être exécuté. Evidemment, si votre application comporte 5 fichiers .js, et que l'un d'entre eux ne marche pas, l'application ne fonctionnera probablement qu'en partie, au mieux. C'est important de s'assurer que chaque fichier fonctionne correctement, et que peu importe l'ampleur, ils gèrent les erreurs dans les autres fichiers avec autant de grâce que possible.

C'est peut-être surprenant de considérer chaque fichiers .js comme des programmes JS différents. Du point de vue de l'usage d'une application, ça ressemble à un seul gros programme. C'est parce que l'exécution de l'application permet à chacun de ces programmes individuels de coopérer et agir comme un seul et même programme.

|NOTE :|
|--|
|Beaucoup de projets utilisent des outils de build qui finissent par combiner tous ces fichiers d'un projet en un seul fichier afin de délivrer la page web. Quand cela se produit, JS considère ce fichier combiné comme le programme tout entier.|

La seule façon pour que plusieurs fichiers .js se comportent comme un seul programme, c'est de partager leur état (et accéder à leur fonctionnalité publique) via le "scope global". Ils se mélangent dans ce scope globale afin qu'à l'exécution ils agissent comme un entier.

Depuis ES6, JS a aussi supporté un format module en plus du format de programme JS unitaire. Les modules sont aussi basés sur le système de fichier. Si un fichier est chargé via le chargement de module comme une importation ou un tag `<script type=module>`, tout son code est considéré comme un module unitaire.

Bien que vous ne considéreriez pas un module, -une collection d'états et de méthodes exposées pour opérer dans cet état-, comme un programme unitaire, JS, en réalité, traite chaque module séparément. Similaire au fonctionnement du "scope global" qui permet à chaque fichier de se mélanger à l'exécution, importer un module dans un autre permet des opérations entre eux à l'exécution.

Peu importe le pattern d'organisation du code (et les mécanismes de chargement) utilisé pour un fichier (seul ou un module), vous devriez penser chaque fichier comme un (mini) programme, qui peuvent coopérer avec les autres (mini) programmes pour réaliser les fonctions de toute votre application.

### Valeurs
--

L'information atomique la plus fondamentale dans un programme, c'est la valeur. Les valeurs sont de la donnée. Ils sont la raison pour laquelle le programme maintient les états. Les valeurs prennent 2 formes en JS : des primitives et des objets.

Les valeurs sont embarquées dans les programmes grâce à des littéraux.

```javascript
greeting("My name is Kyle.");
```

Dans ce programme, la valeur `"My name is Kyle"` est une primitive de type chaîne de caractères ; les chaînes de catactères sont des collections ordonnées de caractères, habituellement utilisées pour représenter les mots et les phrases.

J'ai utilisé le caractère spécial `"` des guillemets doubles pour délimiter (enrouter, séparer, définir) la valeur de la chaîne. Mais j'aurais tout aussi bien pu utiliser les guillemets simples `'`. Le choix de guillemets est de purement cosmétique. Ce qui est important, pour la bonne lecture et maintenabilité du code, c'est de faire un choix et de s'y tenir tout au long du programme.

Une autre option pour délimiter une chaîne de caractère est d'utiliser le _back-tick_ `` ` ``. Cependant, ce choix n'est plus vraiment cosmétique ; il y a aussi un comportement différent. Par exemple :

```javascript
console.log("My name is ${ firstName }.");
// My name is ${ firstName }.

console.log('My name is ${ firstName }.');
// My name is ${ firstName }.

console.log(`My name is ${ firstName }.`);
// My name is Kyle.
```

Considérons que ce programme a déjà défini une variable `firstName` avec comme valeur la chaîne de caractères `"Kyle"`, le back-tick `` ` `` résoud la variable (indiquée avec `${...}`) en affichant sa valeur. Cela s'appelle **l'interpolation**.

La chaîne de caractère délimitée par des back-ticks `` ` `` peut-être utilisé sans avoir d'interpolation d'expression, mais ce serait perdre le but premier de cette syntaxe alternative d'affichage des chaînes de caractères :

```javascript
console.log(
    `Am I confusing you by omitting interpolation ?`
);
// Am I confusing you by omitting interpolation?
// ndlt : Vous ai-je perdu en omettant l'interpolation ?
```

La meilleure approche reste d'utiliser `"` ou  `'` (Encore une fois, en choisir un et s'y tenir !) pour les chaînes de caractères à moins que vous ayez besoin d'utliser des interpolations ; n'utilisez le `` ` `` que pour les chaînes de caractères qui vont inclure des expressions interpolées.

En dehors des chaînes de caractères, les programmes JS contiennent souvent d'autres types de primitives, comme les booléens et les nombres (numbers) :

```javascript
while (false) {
    console.log(3.141592);
}
```

`while` représente un type de boucle, une façon de répéter des opérations _tant que_ sa condition est vraie.

Dans ce cas, la boucle ne va jamais s'exécuter (et rien ne sera imprimée), parce que nous avons utilisé le booléen _false_ (faux) comme condition pour la boucle. _true_ (vrai) aurait provoqué une boucle infinie, alors, attention !

Le nombre `3.141592` est, comme vous le savez sans doute, une approximation du nombre PI arrondi à 6 chiffres après la virgule. Plutôt que d'embarquer une telle valeur, cependant, vous pourriez utiliser la valeur prédéfinie `Math.PI` prévue à cet effet. Une autre variation des nombres est le type primitif `bigint` (big integer) qui est utilisé pour stocker de très grands nombres.

Les nombres sont souvent utilisés dans les programmes pour compter des étapes, comme des itérations de boucles, et accéder à des informations à des positions numériques (ie un index de tableau). On va s'intéresser aux tableaux/objets dans peu de temps, mais pour exemple, s'il y avait un tableau appelé `names`, on pourrait accéder à l'élement en seconde position comme ceci :

```javascript
console.log(`My name is ${ names[1] }.`);
// My name is Kyle.
```

On a utilisé `1` pour l'élément en deuxième position, au lieu de `2`, parce que, comme dans la plupart des langages de programmation, les indices des tableaux en JS commencent à 0 (`0` étant la première position).

En plus des chaînes de caractères, nombres et booléens, il existe deux autres valeurs de _primitives_ en JS, `null` et `undefined`. Bien que des différences existent entre les deux (certaines historiques, d'autres comtemporaines), ces 2 valeurs ont pour but d'indiquer le _vide_ (ou l'absence) d'une valeur.

Beaucoup de développeurs et développeurs préfèrent les traiter tous les deux de cette façon, c'est-à-dire que les valeurs sont indistinctes l'une de l'autre. Si on fait attention, c'est tout de même possible. Cependant, c'est plus sûr d'utiliser seulement `undefined` comme valeur vide, même si `null` semble plus attirant, parce que c'est plus court !

```javascript
while (value != undefined) {
    console.log("Still got something!");
}
```

La dernière valeur de primitive à connaître est le symbole, qui est une valeur à but bien précis, et se comporte comme une valeur cachée impossible à deviner. Les symboles sont quasi exclusivement utilisée comme des clés spéciales dans des objets :

```javascript
hitchhikersGuide[ Symbol("meaning of life") ];
// 42
```

Vous ne rencontrerez pas souvent un usage direct des symboles dans des programmes JS typiques. Ils sont le plus souvent utilisés dans du code bas niveau comme des bibliothèques et des frameworks.

### Tableaux et objets
--

