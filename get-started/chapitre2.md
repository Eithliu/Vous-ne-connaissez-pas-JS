# Vous ne connaissez pas JS : Get Started - Traduction française de la 2e édition.
--

## Chapitre 2 : Une enquête sur JS
--

La meilleure façon d'apprendre JS est de commencer à écrire du JS.

Pour ce faire, vous avez besoin de comprendre comment le langage fonctionne, et c'est ce sur quoi on va se focaliser
ici. Même si vous avez programmé dans d'autres langages auparavant, prenez le temps d'être confortable avec le JS, et
assurez-vous de pratiquer en profondeur.

Ce chapitre n'est pas une référence exhaustive de chaque petit bout de syntaxe du langage JS. Ce n'est pas non plus l'
amorce d'un "intro complète en JS". Ce n'est pas le but.

En réalité, on va juste survoler quelques-uns des domaines principaux du langage. Notre but ici est de mieux sentir le
langage, afin qu'on puisse avancer dans l'écriture de nos propres programmes avec plus d'assurance et de confiance. On
va revisiter plusieurs de ces sujets plus en détails au fur et à mesure que vous avancerez dans ce livre et dans le
reste de la série.

Ne vous attendez pas à ce que ce chapitre soit un résumé rapide à lire. C'est long et il y a une foule de détails à
parcourir. Prenez votre temps.

| ASTUCE:                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Si vous êtes encore en train de vous familiariser avec JS, je vous suggère de planifier beaucoup de temps pour travailler au cours de ce chapitre. Prenez chaque section et analysez et explorez le sujet un petit temps. Regardez des programmes conçus en JS et comparez ce que vous voyez au code et explications (et opinions !) qui vous sont présentés ici. Vous tirerez bien plus de cette série de livres avec une solide base en JS. |

## Chaque fichier est un programme.
--

Presque tous les sites web (les applications web) que vous utilisez est la somme de plusieurs fichiers JS (typiquement
avec l'extension .js). C'est tentant d'imaginer le truc (l'application) comme un seul programme. Mais JS voit les choses
différemment.

En JS, chaque fichier est son propre programme isolé.

La raison pour laquelle c'est important tourne autour de la gestion des erreurs. Puisque JS traite les fichiers comme
des programmes, un fichier peut ne pas marcher (durant le traitement/compilation ou l'exécution) et ça ne va pas
nécessairement empêcher le fichier suivant d'être exécuté. Evidemment, si votre application comporte 5 fichiers .js, et
que l'un d'entre eux ne marche pas, l'application ne fonctionnera probablement qu'en partie, au mieux. C'est important
de s'assurer que chaque fichier fonctionne correctement, et que peu importe l'ampleur, ils gèrent les erreurs dans les
autres fichiers avec autant de grâce que possible.

C'est peut-être surprenant de considérer chaque fichiers .js comme des programmes JS différents. Du point de vue de
l'usage d'une application, ça ressemble à un seul gros programme. C'est parce que l'exécution de l'application permet à
chacun de ces programmes individuels de coopérer et agir comme un seul et même programme.

| NOTE :                                                                                                                                                                                                                                             |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Beaucoup de projets utilisent des outils de build qui finissent par combiner tous ces fichiers d'un projet en un seul fichier afin de délivrer la page web. Quand cela se produit, JS considère ce fichier combiné comme le programme tout entier. |

La seule façon pour que plusieurs fichiers .js se comportent comme un seul programme, c'est de partager leur état (et
accéder à leur fonctionnalité publique) via le "scope global". Ils se mélangent dans ce scope globale afin qu'à l'
exécution ils agissent comme un entier.

Depuis ES6, JS a aussi supporté un format module en plus du format de programme JS unitaire. Les modules sont aussi
basés sur le système de fichier. Si un fichier est chargé via le chargement de module comme une importation ou un tag
`<script type=module>`, tout son code est considéré comme un module unitaire.

Bien que vous ne considéreriez pas un module, -une collection d'états et de méthodes exposées pour opérer dans cet
état-, comme un programme unitaire, JS, en réalité, traite chaque module séparément. Similaire au fonctionnement du "
scope global" qui permet à chaque fichier de se mélanger à l'exécution, importer un module dans un autre permet des
opérations entre eux à l'exécution.

Peu importe le pattern d'organisation du code (et les mécanismes de chargement) utilisé pour un fichier (seul ou un
module), vous devriez penser chaque fichier comme un (mini) programme, qui peuvent coopérer avec les autres (mini)
programmes pour réaliser les fonctions de toute votre application.

### Valeurs
--

L'information atomique la plus fondamentale dans un programme, c'est la valeur. Les valeurs sont de la donnée. Ils sont
la raison pour laquelle le programme maintient les états. Les valeurs prennent 2 formes en JS : des primitives et des
objets.

Les valeurs sont embarquées dans les programmes grâce à des littéraux.

```javascript
greeting("My name is Kyle.");
```

Dans ce programme, la valeur `"My name is Kyle"` est une primitive de type chaîne de caractères ; les chaînes de
catactères sont des collections ordonnées de caractères, habituellement utilisées pour représenter les mots et les
phrases.

J'ai utilisé le caractère spécial `"` des guillemets doubles pour délimiter (enrouter, séparer, définir) la valeur de la
chaîne. Mais j'aurais tout aussi bien pu utiliser les guillemets simples `'`. Le choix de guillemets est de purement
cosmétique. Ce qui est important, pour la bonne lecture et maintenabilité du code, c'est de faire un choix et de s'y
tenir tout au long du programme.

Une autre option pour délimiter une chaîne de caractère est d'utiliser le _back-tick_ `` ` ``. Cependant, ce choix n'est
plus vraiment cosmétique ; il y a aussi un comportement différent. Par exemple :

```javascript
console.log("My name is ${ firstName }.");
// My name is ${ firstName }.

console.log('My name is ${ firstName }.');
// My name is ${ firstName }.

console.log(`My name is ${firstName}.`);
// My name is Kyle.
```

Considérons que ce programme a déjà défini une variable `firstName` avec comme valeur la chaîne de caractères `"Kyle"`,
le back-tick `` ` `` résoud la variable (indiquée avec `${...}`) en affichant sa valeur. Cela s'appelle *
*l'interpolation**.

La chaîne de caractère délimitée par des back-ticks `` ` `` peut-être utilisé sans avoir d'interpolation d'expression,
mais ce serait perdre le but premier de cette syntaxe alternative d'affichage des chaînes de caractères :

```javascript
console.log(
    `Am I confusing you by omitting interpolation ?`
);
// Am I confusing you by omitting interpolation?
// ndlt : Vous ai-je perdu en omettant l'interpolation ?
```

La meilleure approche reste d'utiliser `"` ou  `'` (Encore une fois, en choisir un et s'y tenir !) pour les chaînes de
caractères à moins que vous ayez besoin d'utliser des interpolations ; n'utilisez le `` ` `` que pour les chaînes de
caractères qui vont inclure des expressions interpolées.

En dehors des chaînes de caractères, les programmes JS contiennent souvent d'autres types de primitives, comme les
booléens et les nombres (numbers) :

```javascript
while (false) {
    console.log(3.141592);
}
```

`while` représente un type de boucle, une façon de répéter des opérations _tant que_ sa condition est vraie.

Dans ce cas, la boucle ne va jamais s'exécuter (et rien ne sera imprimée), parce que nous avons utilisé le booléen
_false_ (faux) comme condition pour la boucle. _true_ (vrai) aurait provoqué une boucle infinie, alors, attention !

Le nombre `3.141592` est, comme vous le savez sans doute, une approximation du nombre PI arrondi à 6 chiffres après la
virgule. Plutôt que d'embarquer une telle valeur, cependant, vous pourriez utiliser la valeur prédéfinie `Math.PI`
prévue à cet effet. Une autre variation des nombres est le type primitif `bigint` (big integer) qui est utilisé pour
stocker de très grands nombres.

Les nombres sont souvent utilisés dans les programmes pour compter des étapes, comme des itérations de boucles, et
accéder à des informations à des positions numériques (ie un index de tableau). On va s'intéresser aux tableaux/objets
dans peu de temps, mais pour exemple, s'il y avait un tableau appelé `names`, on pourrait accéder à l'élement en seconde
position comme ceci :

```javascript
console.log(`My name is ${names[1]}.`);
// My name is Kyle.
```

On a utilisé `1` pour l'élément en deuxième position, au lieu de `2`, parce que, comme dans la plupart des langages de
programmation, les indices des tableaux en JS commencent à 0 (`0` étant la première position).

En plus des chaînes de caractères, nombres et booléens, il existe deux autres valeurs de _primitives_ en JS, `null` et
`undefined`. Bien que des différences existent entre les deux (certaines historiques, d'autres comtemporaines), ces 2
valeurs ont pour but d'indiquer le _vide_ (ou l'absence) d'une valeur.

Beaucoup de développeurs et développeurs préfèrent les traiter tous les deux de cette façon, c'est-à-dire que les
valeurs sont indistinctes l'une de l'autre. Si on fait attention, c'est tout de même possible. Cependant, c'est plus sûr
d'utiliser seulement `undefined` comme valeur vide, même si `null` semble plus attirant, parce que c'est plus court !

```javascript
while (value != undefined) {
    console.log("Still got something!");
}
```

La dernière valeur de primitive à connaître est le symbole, qui est une valeur à but bien précis, et se comporte comme
une valeur cachée impossible à deviner. Les symboles sont quasi exclusivement utilisée comme des clés spéciales dans des
objets :

```javascript
hitchhikersGuide[Symbol("meaning of life")];
// 42
```

Vous ne rencontrerez pas souvent un usage direct des symboles dans des programmes JS typiques. Ils sont le plus souvent
utilisés dans du code bas niveau comme des bibliothèques et des frameworks.

### Tableaux et objets
--

En dehors des primitives, l'autre type de valeur en JS est une valeur d'objet.

Commen mentionné précédemment, les tableaux sont un type spécial d'objet qui comprend une liste indexée, ordonnée et
numérotée de données :

```javascript
var names = ["Frank", "Kyle", "Peter", "Susan"];

names.length;
// 4

names[0];
// Frank

names[1];
// Kyle
```

Les tableaux en JS peuvent contenir n'importe quel type de valeur, primitive ou objet (dont d'autres tableaux). Comme
nous le verrons en avançant vers la fin du chapitre 3, même les fonctions sont des valeurs qui peuvent passer dans un
tableau ou un objet.

| NOTE :                                                                                                                                            |
|---------------------------------------------------------------------------------------------------------------------------------------------------|
| Les fonctions, comme les tableaux, sont une sorte spéciale d'objet (ie un sous-type). On va détailler un peu plus les fonctions un peu plus loin. |

Les objets sont plus généraux : une collection de pairs clé-valeur de n'importe quel type. En d'autres termes, vous
accédez aux éléments par un nom de leur emplacement sous forme de chaîne de caractère (la "clé" ou "propriété") plutôt
que par sa position numérique (comme avec les tableaux). Par exemple :

```javascript
var me = {
    first: "Kyle",
    last: "Simpson",
    age: 39,
    specialties: ["JS", "Table Tennis"]
};

console.log(`My name is ${me.first}.`);
```

Ici, on représente un objet, et `first` représente le nom de l'emplacement de l'information dans cet objet (de valeur
collection). Une autre syntaxe possible pour accéder à l'information dans un objet à partir de sa propriété/clé, c'est
d'utiliser les crochet `[ ]`, comme dans `me["first"]`.

### Détermination du type de valeur.

Pour dinstinguer les différentes valeur, l'opérateur `typeof` vous dit son type, si c'est primitif ou un "objet":

```javascript
typeof 42;                  // "number"
typeof "abc";               // "string"
typeof true;                // "booléen"
typeof undefined;           // "undefined"
typeof null;                // "object" -- oups, bug!
typeof {"a": 1};          // "object"
typeof [1, 2, 3];             // "object"
typeof function hello() {
};  // "function"
```

| ATTENTION:                                                                                                                                                                                                   |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `typeof null` retourne malheureusement `"object"`  au lieu de `"null"`. `typeof` retourne également le très spécifique `function` pour les fonctions, mais pas `array` qu'on pourrait attendre d'un tableau. |

Convertir une valeur d'un type à un autre, comme passer d'une chaîne de caractères à un nombre, porte le nom de "
coercion" en JS. On en parlera plus en détails plus loin dans ce chapitre.

Les valeurs primitives et objets se comportent différemment lors de leur assignation ou lorsqu'elles sont passées. On
détaille ceci dans l'Annexe A, "Valeurs vs Références."

### Déclarer et utiliser des variables.
--

Pour bien expliciter ce qui n'est peut-être pas forcément évident dans la section précédente : dans les programmes JS,
les valeurs peuvent être littérales (comme la plupart des exemples précédents), ou peuvent être contenues dans des
variables ; pensez aux variables comme des boîtes qui contiennent des valeurs.

Les variables doivent être déclarées (créées) pour être utilisées. Il existe plusieurs formes de syntaxes possibles qui
déclarent des variables (ie des "identifiants"), et chaque forme a des comportements implicites différents.

Par exemple voyons la déclaration avec `var` :

```javascript
var myName = "Kyle";
var age;
```

Le mot clé `var` déclare une variable qui peut être utilisée dans cette partie du programme, et optionnellement
autoriser une assignation initiale d'une valeur.

Un mot clé similaire est le `let` :

```javascript
let myName = "Kyle";
let age;
```

Le mot-clé `let` a quelques différences avec `var`, avec notamment la plus évidente, le fait que `let` autorise un accès
plus limité à la variable que `var`. Cela s'appelle le "scope d'un bloc", en opposition au scope classique ou celui
d'une fonction.

Regardons ce code :

```javascript
var adult = true;

if (adult) {
    var myName = "Kyle";
    let age = 39;
    console.log("Shhh, this is a secret!");
}

console.log(myName);
// Kyle

console.log(age);
// Error!
```

La tentative d'accéder à `age` en dehors du `if` renvoie une erreur, parce que `age` est scopé dans le bloc du `if`,
tandis que ce n'est pas le cas pour `myName`.

Le scope d'un bloc est très utile pour limiter l'étendue des déclarations de variable dans nos programmes, ce qui
prévient la réassignation accidentelle de leurs noms.

Mais `var` est toujours utile dans ce que ça sous-entend "cette variable sera visible dans un scope plus large (de la
fonction entière)". Les deux formes de déclarations peuvent être approrpiées dans n'importe quel endroit du code, en
fonction des circonstances.

| NOTE :                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| C'est très courant de lire que `var` devrait être évité en faveur du `let` (ou du `const`), notamment à cause de la confusion autour du comportement de `var` et de son scope, depuis les débuts de JS. Je crois que c'est un conseil un peu trop restrictif et finalement inutile. C'est considérer que vous êtes incapable d'apprendre et d'utiliser correctement une fonctionnalité combinée à d'autres. Je pense que vous pouvez et devez apprendre toutes les fonctionnalités disponibles et les utiliser là où c'est approprié ! |

Une 3e forme de déclaration est le `const`. C'est comme `let` mais avec une limitation supplémentaire : il doit lui être
assigné une valeur au moment de sa déclaration, et ne peut pas être ré-assigné avec une valeur différente plus tard.

Par exemple :

```javascript
const myBirthday = true;
let age = 39;

if (myBirthday) {
    age = age + 1;    // OK!
    myBirthday = false;  // Error!
}
```

La constante `myBirthday` ne peut pas être ré-assignée.

Les variables déclarées en `const` ne sont pas "inchangeables", elles ne peuvent juste pas être ré-assignées. C'est
malvenu d'utiliser `const` avec des valeurs objet parce que ces valeurs peuvent quand même être changées même si la
variable ne peut pas être ré-assignée. Cela mène à une potentiel confusion, au final, donc, je pense qu'il est sage d'
éviter ce genre de situation :

```javascript
const actors = [
    "Morgan Freeman", "Jennifer Aniston"
];

actors[2] = "Tom Cruise";   // OK :(
actors = [];                // Error!
```

Le meilleur usage sémantique d'une `const` est quand vous avez une simple valeur primitive à laquelle vous allez donner
un nom utile, comme utiliser `myBirthday` au lieu de `true`. Cela rend le programme plus facile à lire.

| ASTUCE :                                                                                                                                                                                                                                   |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Si vous vous contentez d'utiliser `const` seulement avec des valeurs primitives, vous éviterez la confusion d'un ré-assignement (interdit), vs la mutation (autorisée) ! C'est la meilleure façon et la plus sécurisée d'utiliser `const`. |

En dehors de `var` / `let` / `const`, il y a d'autres formes syntaxiques qui déclarent des identifiants (variables) dans
des scopes variables. Par exemple :

```javascript
function hello(myName) {
    console.log(`Hello, ${myName}.`);
}

hello("Kyle");
// Hello, Kyle.
```

L'identifiant `hello` est créé en dehors du scope, et c'est automatiquement associé pour référencer la fonction. Mais le
paramètre nommé `myName` est créée seulement à l'intérieur de la fonction, et donc seulement accessible à l'intérieur de
ladite fonction. `hello` et `myName` se comporte comme une variable `var`.

Une autre syntaxe pour déclarer une variable est un `catch` :

```javascript
try {
    someError();
} catch (err) {
    console.log(err);
}
```

`err` est une variable scopée uniquement dans le bloc `catch`, un peu à la mnière d'un `let`.

### Les fonctions
--

Le mot "fonction" a plusieurs sens dans la programmation. Par exemple, dans le monde de la programmation fonctionnelle,
la "fonction" a une définition mathématique très précise et implique une série de règles strictes à suivre.

En JS, on devrait considérer le sens du mot "fonction" comme celui d'un autre terme approchant : "la procédure". Une
procédure est une collection de déclarations qui peuvent être invoquées une ou plusieurs fois, à qui on peut fournir des
inputs (des données entrantes) et qui peut retourner un ou plusieurs outputs (des données de sortie).

Depuis les débuts de JS, une fonction ressemble à ceci :

```javascript
function awesomeFunction(coolThings) {
    // ..
    return amazingStuff;
}
```

On appelle ceci une déclaration de fonction parce que c'est une déclaration en soi, pas une expression dans une autre
déclaration. L'association entre l'identifiant `awesomeFunction` et la valeur fonction se produit durant la phase de
compilation du code, avant qu'il soit exécuté.

Au contraire d'une déclaration de fonction, une expression de fonction peut être définie et assignée comme suit :

```javascript
// let awesomeFunction = ..
// const awesomeFunction = ..
var awesomeFunction = function (coolThings) {
    // ..
    return amazingStuff;
};
```

Cette fonction est une expression qui est assignée à la variable `awesomeFunction`. Différente de la forme déclaration
d'une fonction, une expression de fonction n'est pas associée à son identifiant jusqu'à cette déclaration pendant
l'exécution.

C'est très important de noter qu'en JS, les fonctions sont des valeurs qui peuvent être assignées (comme montré dans cet
exemple) et passée ailleurs. En fait, les fonctions JS sont un type spécial du type valeur d'objet. Tous les langages ne
traitent pas les fonctions comme des valeurs, mais c'est capital pour un langage de supporter le pattern de
programmation fonctionnelle, comme JS le fait.

Les fonctions JS peuvent recevoir un paramètre d'entrée :

```javascript
function greeting(myName) {
    console.log(`Hello, ${myName}!`);
}

greeting("Kyle");   // Hello, Kyle!
```

Dans ce bout de code, `myName` est appelé un paramètre et se comporte comme une variable locale à l'intérieur de la
fonction. Les fonctions peuvent être définies pour recevoir des paramètres, de zéro à ce que vous voulez. À chaque
paramètre est assigné la valeur de l'argument que vous passez dans la position de l'appel ("Kyle" ici).

Les fonctions peuvent aussi retourner des valeurs avec le mot clé `return` :

```javascript
function greeting(myName) {
    return `Hello, ${myName}!`;
}

var msg = greeting("Kyle");

console.log(msg);   // Hello, Kyle!
```

Vous ne pouvez `return` qu'une seule valeur, mais si vous avez plus d'une valeur à retourner, vous pouvez les wrapper
dans un unique objet/tableau.

Puisque les fonctions sont des valeurs, elles peuvent être assignées comme des propriétés d'un objet :

```javascript
var whatToSay = {
    greeting() {
        console.log("Hello!");
    },
    question() {
        console.log("What's your name?");
    },
    answer() {
        console.log("My name is Kyle.");
    }
};

whatToSay.greeting();
// Hello!
```

Dans cet exemple, les références aux 3 fonctions (`greeting()`, `question()` et `answer()`) sont incluses dans l'objet
contenu dans `whatTosSay`. Chaque fonction peut être appelée en accédant à la propriété qui récupère la valeur de la
référence de la fonction. Comparez le ce style très clair de définition des fonctions d'un objet à la façon plus
sophistiquée de la syntaxe d'une classe dont nous parlerons plus tard dans ce chapitre.

Il y a plusieurs formes variées qu'une fonction peut prendre en JS. Nous détaillons ces variations dans l'annexe A "Tant
de formes de fonctions".

### Comparaisons
---

Prendre des décisions dans un programme implique de comparer des valeurs pour déterminer leur identité et la relation
avec les autres valeurs. JS a plusieurs mécanismes de comparaisons de valeurs, regardons cela de plus près.

#### équalité... à peu près.

La comparaison la plus commune en JS pose la question suivante "Est-ce que la valeur X est la même que la valeur Y ?".
Mais que signifie exactement "la même que" en JS ?

Pour des raisons historiques et ergonomiques, la signification est plus compliquée que l'évidente identité exacte de la
correspondance. Parfois, une comparaison d'égalité sous-entend une correspondance exacte, mais parfois, la comparaison
désirée est un peu plus vaste, permettant une correspondante similaire ou interchangeable. En d'autres termes, nous
devons faire attention aux différences nuancées entre une comparaison d'**égalité** et une comparaison d'**équivalence
**.

Si vous avez déjà passé un peu de temps à écrire et lire du JS, vous avez déjà vu l'opérateur de "triple égalité" `===`,
aussi définie comme un opérateur d'"égalité stricte". Ça semble plutôt simple, non ? "stricte" signifie bien stricte,
c'est-à-dire _exact_.

Pas _exactement_.

Oui, la plupart des valeurs comparées dans une égalité `===` va fonctionner comme dans notre intuition. Par exemple :

```javascript
3 === 3.0;              // true
"yes" === "yes";        // true
null === null;          // true
false === false;        // true

42 === "42";            // false
"hello" === "Hello";    // false
true === 1;             // false
0 === null;             // false
"" === null;            // false
null === undefined;     // false
```

| Note                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| La comparaison d'égalité avec `===` est souvent décrit d'une autre façon, "vérifier la valeur et le type". Dans beaucoup des exemples que nous avons vu jusque là, comme `42 === "42"`, le type des deux valeurs (nombre, chaîne de caractères etc) ont l'air d'être des facteurs de distinction. Mais il y a plus que cela, malgré tout. En JS, **toutes** les valeurs de comparaisons considèrent le type des valeurs comparées, pas _juste_ l'opérateur `===`. De façon plus spécifique, `===` n'autorise pas toute sorte de conversion de type (ie la "coercition") dans sa comparaison, là où d'autres comparaisons JS autorisent la coercition. |

Mais l'opérateur `===` a tout de même certaines nuances, un fait que beaucoup de développeurs et développeuses JS
semblent oublier, à leur dépend. L'opérateur `===` est designé pour _mentir_ dans deux cas précis : `NaN` et `-0`.
Regardez ce code :

```javascript
NaN === NaN;            // false
0 === -0;               // true
```

Dans le cas de `NaN`, l'opérateur `===` nous ment et nous affirme qu'une occurence de `NaN` n'est pas égale à un autre
`NaN`. Dans le cas de `-0` (oui, c'est une valeur distincte que vous pouvez utiliser intentionnellement dans vos
programmes !), l'opérateur `===` nous ment et nous dit que c'est égal à la valeur `0`.

Puisque le mensonge sur ces comparaisons peut être ennuyeux, c'est mieux d'éviter d'utiliser `===` pour celles-ci. Pour
des comparaisons de `NaN`, il vaut mieux utiliser l'utilitaire `Number.isNaN(..)` qui ne ment pas. Pour la comparaison
avec `-0`, utilisez l'utilitaire `Object.is(..)`, qui ne ment pas non plus. `Object.is(..)` peut aussi être utilisé pour
des vérifications du `NaN` qui ne mentent pas, si vous préférez. On pourrait dire que `Object.is(..)` est une "quadruple
égalité" `====`, une comparaison vraiment vraiment très stricte !

Il y a des raisons historiques et techniques très profondes pour ces _mensonges_, mais ça ne change pas le fait que
`===` n'est pas vraiment une comparaison de _stricte égalité_, dans le sens _le plus stricte_ du terme.

L'histoire est même plus compliquée quand on s'attarde sur les comparaisons de valeurs d'objets (non-primitives). Par
exemple :

```javascript
[1, 2, 3] === [1, 2, 3];    // false
{
    a: 42
}
===
{
    a: 42
}         // false
(x => x * 2) === (x => x * 2)   // false
```

Il se passe quoi, la ?

Il pourrait paraître raisonnable de penser qu'une vérification d'égalité considère la _nature_ ou le _contenu_ de la
valeur ; après tout, `42 === 42` considère la valeur `42`et la compare. Mais lorsqu'il s'agit d'objets, une comparaison
dont on connaît le contenu, c'est ce qu'on appelle une "égalité structurelle".

JS ne défini pas `===` comme une égalité structurelle pour la valeur objet. En réalité, `===` utilise l'égalité d'
identité pour les valeurs objet.

En JS, toutes les valeurs d'objets sont des références (voir "Valeurs vs Références" dans l'Annexe A), elles sont
assignées et passées dans une copie-référence, et pour en revenir à notre discussion, sont comparées par égalité de
référence (identité). Par exemple :

```javascript
var x = [1, 2, 3];

// L'assignation est une copie-référence,
// y est une référence du *même* tableau que x,
// pas une autre copie.
var y = x;

y === x;              // true
y === [1, 2, 3];    // false
x === [1, 2, 3];    // false
```

Dans ce code, `y === x` est vraie parce que les deux variables pointent vers une référence du même tableau initial. Mais
les comparaisons `=== [1, 2, 3]` ne fonctionnent pas parce que y et x, sont respectivement comparés à un nouveau tableau
différent `[1, 2, 3]`. La structure du tableau et son contenu n'ont pas d'importance dans cette comparaison, seulement
l'identité de la référence.

JS ne fournit pas de mécanisme pour une comparaison d'égalité structurelle de valeurs d'objet, seulement des comparaison
d'identité par référence. Pour faire une comparaison d'égalité structurelle, il faudra implémenter les vérifications
vous-même.

Mais attention, c'est plus compliqué que vous ne l'imaginez. Par exemple, comment déterminer si deux références d'une
fonction sont "structurellement équivalentes" ? Même en _stringyfiant_ le texte du code source pour les comparer ne
prendrait pas en compte des éléments comme la fermeture (ou _closure_). JS ne fournit pas de comparaison d'égalité
structurelle parce que c'est quasiment impossible de gérer chaque cas !

### Comparaisons coercitives

La coercition consiste en la conversion de la valeur d'un type vers une représentation d'un autre type (dans la mesure
du possible). Comme nous l'évoquerons dans le chapitre 4, la coercition est un pilier du cœur du langage JS, et non une
fonctionnalité optionnelle qu'on pourrait éviter d'utiliser facilement.

Mais là où la coercition rencontre les opérateurs de comparaison (comme l'égalité), la confusion et la frustration nous
rattrapent plus souvent qu'on ne le voudrait.

Peu de fonctionnalités JS soulève autant de colère dans la vaste communauté JS que l'opérateur `==`, appelé souvent
opérateur "d'égalité non stricte" (ou "molle"). La grande majorité des écrits et des discours publics à propos de JS
considèrent cet opérateur comme une erreur, et pourvoyeur de bugs voire dangereux quand il est utilisé dans des
programmes JS. Même le créateur du langage, Brendan Eich, s'est plaint de cette grossière erreur.

De ce que je peux en dire, la plupart de ces frustrations viennent d'une petite liste de cas particuliers qui troublent,
mais un problème plus profond est la très large diffusion de l'idée reçue comme quoi cet opérateur réalise une
comparaison sans considération des types des valeurs qu'il compare.

L'opérateur `==` réalise une comparaison d'égalité similaire à `===`. En fait, les deux opérateurs prennent en compte le
type des valeurs comparées. Et si la comparaison est entre deux mêmes types, alors `==` et `===` feront exactement la
même chose, sans aucune différence.

Si le type des valeurs comparé est différent, alors le `==` diffèrera du `===` puisqu'il va permettre une coercition
avant la comparaison. En d'autres termes, les deux veulent comparer des valeurs de types similaires, mais `==` permet
une conversion de type en premier lieu, et une fois le type converti et les deux étant les mêmes des deux côtés, alors
`==` fera la même chose que `===`. Au lieu d'une "égalité non stricte", l'opérateur `==` devrait être décrit comme
opérant une "égalité coercitive".

Par exemple :

```javascript
42 == "42";             // true
1 == true;              // true
```

Dans ces 2 comparaisons, les types sont différents, donc le `==` provoque une conversion des valeurs qui ne sont pas des
nombres (`"42"` et `true`) en des nombres (respectivement `42` et `1`) avant d'effectuer la comparaison.

Avoir conscience de la nature de `==` -le fait qu'il préfère des comparaisons de primitive de type numérique- vous
aidera à éviter la plupart des soucis de quelques cas particuliers, comme rester éloigner de bizarreries comme `"" == 0`
ou `0 == false`.

Vous vous dites peut-être "Oh bon, je vais juste continuer à éviter la comparaison d'égalité coercitive (et utiliser
plutôt `===` pour éviter ces cas particuliers" ! Désolé, il y a peu de chance que ça se passe comme vous l'auriez
espéré.

Il y a de fortes chances que vous utilisiez des opérateurs de comparaison relationnels comme `<`, `>` (et même `<=` et
`>=`).

Et comme `==`, ces opérateurs vont fonctionner comme s'ils étaient "stricts" si les types comparés sont identiques, mais
réaliserons d'abord une coercition (généralement en nombre) si les types diffèrent.

Par exemple :

```javascript
var arr = ["1", "10", "100", "1000"];
for (let i = 0; i < arr.length && arr[i] < 500; i++) {
    // va s'exécuter 3 fois
}
```

La comparaison `i < arr.length` est "sauvée" de la coercition parce que `i` et `arr.length` sont toujours des nombres.
Le `arr[i] < 500` en revanche, invoque une coercition, parce que les valeurs de `arr[i]` sont toutes des chaînes de
caractères. Ces comparaisons ainsi deviennent `1 < 500`, `10 < 500`, `100 < 500` et `1000 < 500`. Puisque cette 4e
comparaison est fausse (`false`), la boucle s'arrête à la 3e itération.

Ces opérateurs relationnels utilisent typiquement des comparaisons numériques, excepté dans le cas où les 2 valeurs
comparées sont déjà des chaînes de caractères ; dans ce cas-là, ils utilisent la comparaison des chaînes de caractères
par ordre alphabétique (comme un dictionnaire) :

```javascript
var x = "10";
var y = "9";

x < y;      // true, watch out!
```

Il n'y a aucun moyen d'éviter la coercition avec ces opérateurs relationnels, autre que juste éviter d'utiliser des
types qui ne correspondent pas dans les comparaison. C'est peut-être un but admirable, mais il y a des chances que vous
tombiez sur un cas où les types risquent d'être différents.

L'approche la plus sage n'est pas d'éviter les comparaisons de coercition, mais d'apprendre les tenants et les
aboutissants de ces comportements.

Les comparaisons coercitives apparaissent dans d'autres endroits en JS, comme les conditions (`if`, etc.) que nous
détaillerons dans l'Annexe A, "Comparaison conditionnelle Coercitive".

### Comment s'organise-t-on en JS ?
--

Deux schémas d'organisation du code (données et comportement) sont largement utilisés dans l'écosystème JS : les classes
et les modules. Ces schémas ne sont pas mutuellement exclusifs ; beaucoup de programmes utilisent les deux. D'autres
programmes vont se limiter à un schéma, ou même aucun !

A certains égards, ces schémas ou patterns sont très différents. Mais étonnamment, d'une certaine façon, ils ne sont que
deux faces d'une même pièce. Être efficace en JS nécessite de comprendre les 2 schémas et où il est approprié de les
utiliser (ou non !)

#### Les classes

Les termes "orienté objet", "orienté classe" et "classes" sont chargés de détails et de nuances ; ils ne sont pas
universels par définition.

Nous utiliseront une définition plutôt traditionnelle, commune, l'une des plus familière pour celles et ceux qui ont une
expérience dans les langages orientés objets tels que C++ et Java.

Une classe dans un programme est la définition d'un "type" de structure de données personnalisée (_custom_) qui inclus à
la fois les données et les comportements qui se produisent sur lesdites données. Les classes définissent comment
fonctionne une structure de données, mais les classes ne sont pas à proprement parler des valeurs concrètes. Pour
récupérer une valeur concrète utilisable dans votre programme, une classe doit être _instanciée_ (avec le mot-clé `new`)
une ou plusieurs fois.

Par exemple :

```javascript
class Page {
    constructor(text) {
        this.text = text;
    }

    print() {
        console.log(this.text);
    }
}

class Notebook {
    constructor() {
        this.pages = [];
    }

    addPage(text) {
        var page = new Page(text);
        this.pages.push(page);
    }

    print() {
        for (let page of this.pages) {
            page.print();
        }
    }
}

var mathNotes = new Notebook();
mathNotes.addPage("Arithmetic: + - * / ...");
mathNotes.addPage("Trigonometry: sin cos tan ...");

mathNotes.print();
// ..
```

Dans la classe `Page`, la donnée est une chaîne de caractères, un texte stocké dans une propriété `this.text`. Le
comportement est `print()`, une méthode qui renvoit le texte dans la console.

Pour la classe `Notebook`, la donnée est un tableau d'instances de `Page`. Le comportement est `addPage(..)`, une
méthode qui instancie des pages `new Page` et les ajoute à la liste et les `print()` (ce qui affiche toutes les pages
dans le carnet de note _notebook_).

La déclaration `mathNotes = new Notebook()` créé une instance de la classe `Notebook`, et `page = new Page(text)` est là
où les instances de la classe `Page` sont créés.

Les comportements (méthodes) ne peuvent être appelés que sur les instances (et non les classes), tels que
`mathNotes.addPage(..)` et `page.print()`.

Le mécanisme d'une classe permet de créer un paquet de données (texte et pages) pour être organisés ensemble avec leurs
comportements (ie `addPage(..)` et `print()`). Le même programme aurait pu être écrit sans la moindre classe, mais ça
aurait été probablement bien moins organisé, plus difficile à lire et à comprendre, et plus susceptible de comporter des
bugs et rendre la maintenabilité plus difficile.

#### Héritage de classe

Un autre aspect inhérent au design orienté classe traditionnel, bien que moins communément usité en JS est "
l'héritage" (et le "polymoprhisme"). Par exemple :

```javascript
class Publication {
    constructor(title, author, pubDate) {
        this.title = title;
        this.author = author;
        this.pubDate = pubDate;
    }

    print() {
        console.log(`
            Title: ${this.title}
            By: ${this.author}
            ${this.pubDate}
        `);
    }
}
```

Cette classe `Publication` défini une collection de comportements communs dont tout type de publication pourrait avoir
besoin.

Maintenant, considéront des publications plus spécifiques comme des livres `Book` et des post de blog `BlogPost` :

```javascript
class Book extends Publication {
    constructor(bookDetails) {
        super(
            bookDetails.title,
            bookDetails.author,
            bookDetails.publishedOn
        );
        this.publisher = bookDetails.publisher;
        this.ISBN = bookDetails.ISBN;
    }

    print() {
        super.print();
        console.log(`
            Publisher: ${this.publisher}
            ISBN: ${this.ISBN}
        `);
    }
}

class BlogPost extends Publication {
    constructor(title, author, pubDate, URL) {
        super(title, author, pubDate);
        this.URL = URL;
    }

    print() {
        super.print();
        console.log(this.URL);
    }
}
```

Les deux classes `Book` et `BlogPost` utilise la clause `extends` pour étendre la définition générale de `Publication`
afin d'inclure des comportements supplémentaires. L'appel `super(..)` dans chaque constructeur `constructor` délègue au
constructeur de la classe parente de `Publication` le travail d'initialisation, et ensuite, ils font des choses plus
spécifiques en fonction de leur type respectif de publication (ie des "sous-classes" ou "classes enfant").

Maintenant, imaginons utiliser ces classes enfants :

```javascript
var YDKJS = new Book({
    title: "You Don't Know JS",
    author: "Kyle Simpson",
    publishedOn: "June 2014",
    publisher: "O'Reilly",
    ISBN: "123456-789"
});

YDKJS.print();
// Title: You Don't Know JS
// By: Kyle Simpson
// June 2014
// Publisher: O'Reilly
// ISBN: 123456-789

var forAgainstLet = new BlogPost(
    "For and against let",
    "Kyle Simpson",
    "October 27, 2014",
    "https://davidwalsh.name/for-and-against-let"
);

forAgainstLet.print();
// Title: For and against let
// By: Kyle Simpson
// October 27, 2014
// https://davidwalsh.name/for-and-against-let
```

Notez que les deux instances de la classe enfant ont une méthode `print()` qui surcharge la méthode héritée `print()`de
la classe parente `Publication`. Chacune de ces méthodes `print()` surchargées de la classe enfant appelle
`super.print()` pour invoquer la version héritée de la méthode `print()`.

Le fait que les deux héritent et surchargent des méthodes qui peuvent avoir le même nom et co-exister est appelé le
_polymorphisme_.

L'héritage est un outil puissant pour organiser les données/comportement dans des unités logiques séparées (des
classes), mais permettant aux classes enfants de coopérer avec le parent en accédant/utilisant ses comportements et
données.

#### Les modules

Le schéma des modules a globalement le même but que le schéma des classes, qui est de grouper des données et des
comportements ensemble en des unités logiques. Comme avec les classes, les modules peuvent "inclure" ou "accéder" aux
données et comportements d'autres modules, pour une bonne coopération.

Mais les modules ont des différences importantes avec les classes. La plus notable étant que la syntaxe est totalement
différente.

*Les modules classiques*

ES6 a ajouté la syntaxe des modules à la syntaxe native de JS, qu'on détaillera dans un moment. Mais depuis les débuts
de JS, les modules étaient un schéma important et commun qui a été utilisés dans un nombre incalculable de programmes
JS, même sans syntaxe dédiée.

Les caractéristiques principales d'un module classique sont une fonction externe (qui s'exécute au moins une fois), et
qui retourne une "instance" du module avec une ou plusieurs fonctions exposées qui peuvent opérer dans les données
internes (cachées) d'une instance du module.

Parce qu'un module de cette forme est une fonction, et que l'appeler produit une "instance" de ce module, une autre
description de ces fonctions est "des usines de modules" (_module factories_).

Regardons la forme classique d'un module des classes précédemment définies `Publication`, `Book` et `BlogPost` :

```javascript
function Publication(title, author, pubDate) {
    var publicAPI = {
        print() {
            console.log(`
                Title: ${title}
                By: ${author}
                ${pubDate}
            `);
        }
    };

    return publicAPI;
}

function Book(bookDetails) {
    var pub = Publication(
        bookDetails.title,
        bookDetails.author,
        bookDetails.publishedOn
    );

    var publicAPI = {
        print() {
            pub.print();
            console.log(`
                Publisher: ${bookDetails.publisher}
                ISBN: ${bookDetails.ISBN}
            `);
        }
    };

    return publicAPI;
}

function BlogPost(title, author, pubDate, URL) {
    var pub = Publication(title, author, pubDate);

    var publicAPI = {
        print() {
            pub.print();
            console.log(URL);
        }
    };

    return publicAPI;
}
```

Comparons ces formes à la version classe, il y a plus de similitudes que de différences.

Le format classe stocke des méthodes et données dans une instance d'objet, auxquels on ne peut accéder qu'avec le
préfixe `this.`. Avec les modules, les méthodes et données sont accessibles comme des identifiants qui sont des
variables dans le scope sans le préfixe `this.`.

Avec une classe, l'"API" d'une instance est implicite dans la définition d'une classe, et aussi, toutes les données et
méthodes sont publiques. Avec la fonction usine de modules, vous créez explicitement etretournez un objet avec toutes
les méthodes exposées publiquement, et toutes les données ou méthodes non-référencées restent privées à l'intérieur de
la fonction-usine.

Il existe d'autres variations autour de la forme fonction-usine qui sont plutôt communes en JS, même en 2020 : vous avez
peut-être déjà croisé ces formes dans d'autres programmes JS : AMD (Définition de Module Asynchrone - _Asynchronous
Module Definition_), UMD (Définition de Module Universel -  _Universal Module Definition_), et CommonJS. (des modules
classiques dans le style de Node.js). Les variations sont mineures (pas vraiment compatibles). Cependant, toutes ces
formes reposent sur les mêmes principes basiques.

Regardons l'usage (ie "l'instanciation") de ces fonctions usine de modules :

```javascript
var YDKJS = Book({
    title: "You Don't Know JS",
    author: "Kyle Simpson",
    publishedOn: "June 2014",
    publisher: "O'Reilly",
    ISBN: "123456-789"
});

YDKJS.print();
// Title: You Don't Know JS
// By: Kyle Simpson
// June 2014
// Publisher: O'Reilly
// ISBN: 123456-789

var forAgainstLet = BlogPost(
    "For and against let",
    "Kyle Simpson",
    "October 27, 2014",
    "https://davidwalsh.name/for-and-against-let"
);

forAgainstLet.print();
// Title: For and against let
// By: Kyle Simpson
// October 27, 2014
// https://davidwalsh.name/for-and-against-let
```

La seule différence observable ici, est l'absence du mot clé `new`, en appelant l'usine à modules comme des fonctions
normales.

*Modules ES*

Les modules ES (ESM), introduits dans le langage JS avec ES6, ont été créés dans le même esprit et le même objectif que
les modules classiques décrits plus haut, en prenant en compte les variations importantes et les cas d'usages de AMD,
UMD et de CommonJS.

L'approche de l'implémentation, en revanche, diffère significativement.

D'abord, il n'y a pas de fonction enveloppante pour définir un module. Le contexte d'enveloppement est un fichier. ESM
est toujours à base de fichier ; un fichier égal un module.

Ensuite, vous n'interagissez pas avec l'"API" d'un module explicitement, mais vous utilisez le mot clé `export` pour
ajouter une variable ou une méthode dans sa définition d'API publique. Si quelque chose est défini dans un module mais
pas exporté, alors, ça reste caché (comme avec les modules classiques).

Troisièmement, et probablement la différence la plus notable comparés aux schémas précédemment discutés, vous "
n'instanciez" pas un module ES, vous ne faitesque l'importer pour utiliser son instance unique. les ESM sont des "
singletons", dans le sens où il n'y a qu'une instance unique qui est créée, au premier import dans voter programme, et
chaque autre import reçoit une référence à cette même instance unique. Si votre module a besoin de plusieurs
instanciations, il vous faudra fournir une fonction d'usine de modules de type classique dans votre définition ESM pour
obtenir ce que vous voulez.

Dans notre exemple en cours, on réalise plusieurs instancitations, donc les exemples de code suivants vont mixer à la
fois des ESM et des modules classiques.

Regardons le fichier `publication.js` :

```javascript
function printDetails(title, author, pubDate) {
    console.log(`
        Title: ${title}
        By: ${author}
        ${pubDate}
    `);
}

export function create(title, author, pubDate) {
    var publicAPI = {
        print() {
            printDetails(title, author, pubDate);
        }
    };

    return publicAPI;
}
```

Pour importer et utiliser ce module, à partir d'un autre ES module comme `blogpost.js` :

```javascript
import {create as createPub} from "publication.js";

function printDetails(pub, URL) {
    pub.print();
    console.log(URL);
}

export function create(title, author, pubDate, URL) {
    var pub = createPub(title, author, pubDate);

    var publicAPI = {
        print() {
            printDetails(pub, URL);
        }
    };

    return publicAPI;
}
```

Et enfin, pour utiliser ce module, on l'importe dans un autre ES module comme `main.js` :

```javascript
import {create as newBlogPost} from "blogpost.js";

var forAgainstLet = newBlogPost(
    "For and against let",
    "Kyle Simpson",
    "October 27, 2014",
    "https://davidwalsh.name/for-and-against-let"
);

forAgainstLet.print();
// Title: For and against let
// By: Kyle Simpson
// October 27, 2014
// https://davidwalsh.name/for-and-against-let
```

| NOTE :                                                                                                                                                                                                                                                                                                                                 |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| la clause `as newBlogPost` n'est pas obligatoire ; si elle est oubliée, une fonction du plus haut niveau nommée `created(..)` sera importée. Dans ce cas-là, je la renomme pour une meilleure lisibilité ; son nom générique `create(..)` devient plus descriptive et compréhensible dans son objectif en la renommant `newBlogPost()` |

Comme montré ici, les modules ES peuvent utiliser des modules classiques à l'intérieur s'ils ont besoin de plusieurs
instanciations. A fortiori, on aurait pu exposer une classe de notre module au lieu d'une fonction usine `create(..)`,
avec un résultat identique. Cependant, puisque vous utilisez déjà les ESM, je recommanderai de se tenir aux modules
classiques au lieu des classes.

Si votre module n'a besoin que d'une seule instance, vous pouvez zapper les couches de complexité : exportez ses
méthodes publiques directement.

### Le terrier du lapin est de plus en plus profond
--

Comme promis au début de ce chapitre, on a juste jeté un œil à la surface des nombreuses parties que comporte le langage
JS.
Votre tête doit encore être en train de tourner, mais c'est tout à fait normal après tant d'informations !

Même avec ce "bref" survol de JS, nous avons découvert des tonnes de détails sur lesquels vous devriez vous attarder
afin de vous assurer d'être confortable avec. Je suis sérieux quand je vous siggère de relire et de re-relire ce
chapitre.

Dans le prochain chapitre, on va aller plus loin dans certains des aspects les plus importants du fonctionnement de JS
dans son cœur. Mais avant de suivre le lapin dans son terrier, assurez-vous d'avoir bien le temps de digérer pleinement
ce qu'on vient de voir ici.

