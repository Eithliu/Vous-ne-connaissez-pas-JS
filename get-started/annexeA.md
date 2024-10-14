# Vous ne connaissez pas JS : Get Started - Traduction française de la 2e édition.
--
## Annexe A : Aller plus loin dans l'exploration
--
Dans cette annexe, on va rentrer plus en détails de certains sujets du chapitre principal. Considérez ce contenu comme une prévisualisation optionnelle de certains détails nuancés traités dans la série de livres.

### Valeurs vs Références
--

Dans le chapitre 2, on évoque les 2 types de valeurs les plus courantes : les primitives et les objets. Mais on n'a pas parlé des différences entre les deux : comment ces valeurs sont assignées et transmises.

Dans beaucoup de langages, le ou la développeuse peut choisir entre assigner une valeur en tant que valeur elle-même, ou comme une référence à la valeur. Mais en JS, cette décision est totalement déterminée par le type de valeur. Cela surprend bon nombres de développeurs d'autres langages quand ils commencent le JS.

Si vous assignez une valeur en tant que valeur propre, elle est copiée. Par exemple :
```Javascript
var myName = "Kyle";

var yourName = myName;
```
Ici, la variable `yourName` a une copie distincte de `"Kyle"`, la chaîne de caractères qui est la valeur stockée dans `myName`. C'est parce que la valeur est une primitive, et les primitives, sont toujours assignées comme des **copies**.

Voici un exemple de comment prouver qu'il y a 2 valeurs bien distinctes :
```Javascript
var myName = "Kyle";

var yourName = myName;

myName = "Frank";

console.log(myName);
// Frank

console.log(yourName);
// Kyle
```

Vous voyez comment `yourName` n'a pas été affecté par la ré-assignation de `myName` en `"Frank"` ? C'est parce que chaque variable détient sa propre copie de la valeur.

Au contraire, les références sont un concept dans lequel 2 ou plusieurs variables pointent vers la même valeur, impliquant que modifier cette valeur partagée sera propagé en accédant à n'importe laquelle de ces références. En JS, seules les valeurs objet (tableaux, objets, fonctions, etc.) sont traitées comme des références.

Imaginez :
```JavaScript
var myAddress = {
    street: "123 JS Blvd",
    city: "Austin",
    state: "TX"
};

var yourAddress = myAddress;

// Je dois déménager !
myAddress.street = "456 TS Ave";

console.log(yourAddress.street);
// 456 TS Ave
```

Parce que la valeur assignée à `myAdress` est un objet, c'est une référence, ainsi, l'assignation à la variable `yourAdress` est une copie de la référence, pas la valeur de l'objet elle-même.
C'est pourquoi la valeur modifiée assignée à `myAdress.street` est réfléchie du côté de `yourAdress.street`. `myAdress` et `yourAdress` ont chacune une copie de la référence du seul objet partagé, donc une mise à jour de l'une des variable implique une mise à jour de l'autre également.

Encore une fois, JS choisit l'un des deux comportements suivants : la copie de valeur vs la copie de référence en fonction du type de valeur. Les primitives, c'est de la copie de valeur, les objets, c'est de la copie de référence. Il n'y a aucun moyen de passer outre ce comportement en JS.

### Tant de types de fonctions
Souvenez-vous de ce bout de code de la section "Fonctions" dans le chapitre 2 :
```JavaScript
var awesomeFunction = function(coolThings) {
    // ..
    return amazingStuff;
};
```
Cette fonction est appelée __fonction anonyme__ parce qu'elle n'est pas identifiée par un nom entre le mot clé `function` et la liste de paramètres `(...)`. Ce point précis est confus pour pas mal de développeurs et développeuses JS parce que depuis ES6, JS est capable de faire de "l'inférence de nom" sur une fonction anonyme :
```JavaScript
awesomeFunction.name;
// "awesomeFunction"
```

La propriété `name` d'une fonction va réveler soit directement son nom donné lors de sa déclaration, soit son nom inféré dans le cas d'une expression anonyme. Cette valeur est généralement utilisée pour dans les __developer tools__ quand on veut inspecter la valeur d'une fonction ou l'établissement d'une __error stack trace__

Donc, même une fonction anonyme _peut_ avoir un nom. Cependant, l'inférence d'un nom se produit dans des cas spécifiques limités, comme quand l'opération d'une fonction est assignée (avec `=`) Si vous passez une expression en argument d'un appel de fonction, par exemple, il n'y a pas d'inférence de nom. La propriété `name` sera une chaîne de caractères vide, et la console de votre inspecteur va la nommer "(anonymous function)".

Mais même si un nom est inféré, ça reste une fonction anonyme. Pourquoi ? Parce que le nom inféré est une métadonnée, pas un identifiant disponible pour se référer à ladite fonction. Une fonction anonyme n'a pas besoin d'identifiant pour se référer à elle-même de l'intérieur pour de la récursivité, de l'unbinding d'événement, etc.

Comparons la forme de l'expression anonyme à :

```Javascript
// let awesomeFunction = ..
// const awesomeFunction = ..
var awesomeFunction = function someName(coolThings) {
    // ..
    return amazingStuff;
};

awesomeFunction.name;
// "someName"
```

Ce type de fonction est une fonction nommée, puisque son identifiant `someName` est directement associée à la fonction au moment de la compilation; l'association avec l'identifiant `awesomeFunction` n'a lieu qu'au moment de l'exécution de cette déclaration. Ces 2 identifiants n'ont pas besoin de correspondre l'un avec l'autre; parfois, il y a besoin qu'ils soient différents, d'autres fois, c'est plus utile que les deux soit les mêmes.

Notez aussi que le nom d'une fonction explicite, l'identifiant `someName` est prioritaire lors de l'assignation d'un __nom__ pour la propriété `name`.

Les fonctions doivent-elles être nommées ou anonymes ? Les avis varient largement sur la question. La plupart des developpeurs et développeuses ne se posent pas vraiment la question en utilisant des fonctions anonymes. C'est surtout plus court, et clairement plus commun dans le monde du code en JS.

A mon avis, si une fonction existe dans votre programme, elle a un but; sinon, supprimez-la. Et si elle a un but, un nom évident peut décrire ce but.

Si une fonction a un nom, vous, l'auteur ou autrice du code devriez inclure un nom dans le code, pour que la personne qui lit votre code n'ai pas à inférer ce nom en lisant et mentalement exécuter le code source de cette fonction. Même une fonction basique dont le contenu ressemble à `x * 2` devrait être lu avec un nom du type "double" ou "multBy2"; ce travail mental supplémentaire n'est pas nécessaire alors qu'il suffit de nomme une fois votre fonction "double" ou "multBy2", évitant une gymnastique mentale pénible à la personne qui relira votre code.

Il y a, malheureusement, beaucoup d'autres formes de fonction en JS depuis début 2020 (et sûrement encore plus à l'avenir !)

En voici quelques-unes :

```Javascript
// Une fonction génératrice
function *two() { .. }

// Une fonction asynchrone
async function three() { .. }

// Une fonction génératrice asynchrone
async function *four() { .. }

// Une fonction nommée exportée (ES6 modules)
export function five() { .. }
```

Et en voici quelques autres des (nombreuses) formes de fonction possibles :

```javascript
// IIFE : une fonction auto-appelante
(function(){ .. })();
(function namedIIFE(){ .. })();

// une fonction auto-appelante asynchrone
(async function(){ .. })();
(async function namedAIIFE(){ .. })();

// des fonctions fléchées
var f;
f = () => 42;
f = x => x * 2;
f = (x) => x * 2;
f = (x,y) => x * y;
f = x => ({ x: x * 2 });
f = x => { return x * 2; };
f = async x => {
    var y = await doSomethingAsync(x);
    return y * 2;
};
someOperation( x => x * 2 );
// ..
```

Gardez en tête que les fonctions fléchées (__arrow functions__) sont techniquement anonymes, la syntaxe même empêche de nommer directement la fonction. Elle peut avoir un `name` inféré, mais seulement en cas d'assignation (création de la fonction), pas dans le cas où elle est passée comme argument d'une autre fonction (comme dans la dernière ligne de notre exemple de code ci-dessus)

Je ne suis pas très fan de la surutilisation des fonctions anonymes, c'est également le cas de la version fléchée. Ce type de fonction a un objectif bien spécifique (c'est-à-dire la gestion du mot clé `this`), mais ça ne veut pas dire qu'il faut l'utiliser à chaque fois qu'on veut écrire une fonction. Il faut utiliser l'outil le plus approprié pour chaque chose.

Les fonctions peuvent aussi être spécifiées lors de la définition d'une classe et de la définition littérale d'un objet. On les appelle, dans ces cas-là, des "méthodes", même si en JS cette terminologie n'implique pas de différences majeures avec une "fonction" :

```javascript
class SomethingKindaGreat {
    // méthodes de classes
    coolMethod() { .. }   // pas de virgules !
    boringMethod() { .. }
}

var EntirelyDifferent = {
    // méthodes d'objet
    coolMethod() { .. },   // des virgules !
    boringMethod() { .. },

    // propriété d'une opération de fonction (anonyme)
    oldSchool: function() { .. }
};
```
> NDLT : La coercition en langage informatique

Pfiou ! Ca fait beaucoup de façons de définir une fonction.

Ici, il n'y a pas 36 moyens; Il faut peu à peu se familiariser avec tous les types de fonction, savoir les reconnaître dans du code existant et savoir les utiliser correctement dans le code que vous écrivez. Etudiez-les attentivement et pratiquez !

### Comparaison conditionnelle coercitive

Oui, le nom de cette section est assez tordu. Mais de quoi parle-t-on ici ? On parle des opérations de conditions qui nécessitent de faire des comparaisons de type coercitives pour prendre leur décision.

Les déclarations `if` et la comparaison ternaire `? :`, ainsi que les tests effectués dans les boucles `while` et `for` réalisent une comparaison de valeurs implicite. Mais de quelle sorte ? Est-ce "strict" ou "coercitif" ? Et bien, les deux.

Par exemple :
```javascript
var x = 1;

if (x) {
    // will run!
}

while (x) {
    // will run, once!
    x = false;
}
```
Vous imaginez le fonctionnement de ces expressions de conditions `(x)` comme ceci :

```javascript
var x = 1;

if (x == true) {
    // will run!
}

while (x == true) {
    // will run, once!
    x = false;
}
```
Dans ce cas précis -- la valeur de x étant 1 --, ce modèle mental fonctionne, mais de façon général, ce n'est pas toujours vrai. Par exemple :

```javascript
var x = "hello";

if (x) {
    // will run!
}

if (x == true) {
    // won't run :(
}
```

Oups. Mais alors que fait ce `if` réellement ? Voici le modèle mental exact :

```javascript
var x = "hello";

if (Boolean(x) == true) {
    // will run
}

// which is the same as:

if (Boolean(x) === true) {
    // will run
}
```

Puisque la fonction `Boolean(..)` retourne toujours une valeur de type booléen, le `==` vs `===` dans ce bout de code n'est pas pertinent; Ils feront tous les deux la même chose. Mais le plus important ici, c'est de constater qu'avant la comparaison, une coercition a lieu, de peu-importe-le-type-de `x` à booléen.

Vous ne pouvez pas échapper à la coercition dans les comparaisons en JS. Accrochez-vous et apprenez les.

### Classes prototypiques.

Dans le chapitre 3, on a parlé des prototypes et on a montré comment on peut lier des objet via une chaine de prototypes.

Une autre façon de relier de tels prototypes a servi de prédécesseur (honnêtement, pas très élégant) à l'élégance du système de classes ES6 (voir le chapitre 2, « Classes »), et est appelée classes prototypiques.


| ASTUCE |
|---     |
| Même si ce type de code est devenu rare en JS, maintenant, c'est toujours étonnament commun d'être interrogé dessus lors d'entretiens d'emploi.  |


Souvenons-nous de la façon de coder avec un `Object.create(..)`
```javascript
var Classroom = {
    welcome() {
        console.log("Welcome, students!");
    }
};

var mathClass = Object.create(Classroom);

mathClass.welcome();
// Welcome, students!
```

Ici, un objet `mathClass` est lié via son prototype à un objet `Classroom`. A travers cette liaison, l'appel de la fonction `mathClass.welcome()` est déléguée à la méthode définie dans `Classroom`.

Le __pattern__ de la classe prototypique aurait étiqueté ce comportement de délégation "héritage", et l'aurait également défini (avec le même comportement) comme suit :

```javascript
function Classroom() {
    // ..
}

Classroom.prototype.welcome = function hello() {
    console.log("Welcome, students!");
};

var mathClass = new Classroom();

mathClass.welcome();
// Welcome, students!
```

Toutes les fonctions, par défaut, font référence à un objet vide comme propriété nommée `prototype`. En dépit de la confusion que le nom peut engendrer, il ne s'agit **pas** du prototype de la fonction (quand la fonction est liée au prototype), mais plutôt de l'objet prototype _ à lier_ quand d'autres objets sont créés en appelant la fonction avec `new`.

On a ajouté une propriété `welcome` sur cet objet vide (appelé `Classroom.prototype`), qui pointe sur la fonction `hello()`.

Ensuite, `new Classroom()` isntancie un nouvel objet (assigné à `mathClass`), et lie le prototype à l'objet existant `Classroom.prototype`.

Même si `mathClass` n'a pas de fonction/propriété `welcome()`, elle délègue sans problème à la fonction `Classroom.prototype.welcome()`.

Ce pattern de  "classe prototypique" est vivement déconseillé, en faveur du mécanisme proposé par ES6 :
```javascript
class Classroom {
    constructor() {
        // ..
    }

    welcome() {
        console.log("Welcome, students!");
    }
}

var mathClass = new Classroom();

mathClass.welcome();
// Welcome, students!
```

Sous le capot, c'est la même façon de faire qu'avec la liaison des prototypes, mais cette syntaxe de classe correspond au design pattern orienté class, bien plus propre que les "classes prototypiques".
