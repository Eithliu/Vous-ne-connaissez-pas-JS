# Vous ne connaissez pas JS : Get Started - Traduction française de la 2e édition.
--

## Chapitre 1 : Qu'est-ce que JavaScript ?
--

Vous ne connaissez pas Javascript... encore. Moi non plus, pas complètement en tout cas. Aucun d'entre nous. Mais on peut tous et toutes commencer à mieux connaître JS.

Dans le premier chapitre du premier livre de cette série "Vous ne connaissez pas JS", on va prendre le temps de poser les fondations pour avancer correctement. On commencera par parcourir une variété de détails important des coulisses, dissiper certains mythes et idées fausses à propos de ce qu'est et ce que n'est pas ce langage.

C'est un aperçu précieux de l'identité et du processus autour de comment est organisé et maintenu JS; tous les développeurs et développeuses de JS devrait comprendre ça. Si vous voulez mieux connaître JS, voici comment commencer ce grand voyage.

## A propos de ce livre
--

Je mets l'accent sur le mot _voyage_ parce que connaître JS n'est pas une destination, mais une direction. Peu importe combien de temps vous passez avec le langage, vous trouverez toujours quelque d'autre à apprendre et comprendre un peu mieux. Ne voyez pas ce livre comme un truc à finir au plus vite pour réussir. Prenez plutôt le temps, et persistez, c'est le meilleur moyen, maintenant que vous entamez votre trajet.

A la suite de ce chapitre sur les coulisses, le reste du livre propose une carte de haut niveau de ce que vous allez trouver au cours de vos études autour de JS avec la série de livres "Vous ne connaissez pas JS".

En particulier, le chapitre 4 identifie les 3 principaux pilliers autour desquels le langage JS est organisé : le scope & les closures, les prototypes & objets et les types & coercitions. JS est un langage vaste et sophistiqué, avec beaucoup de fonctionnalités et de capacités. Mais tout JS est basé sur ces 3 piliers fondamentaux.

Gardez bien en tête que même si ce livre est titré "Get Started", **ce n'est pas un livre pour les débutants ni un livre d'introduction.** L'objectif premier de ce livre est de vous préparer à étudier JS plus en profondeur dans les livres suivants; il est écrit en présupposant que vous êtes déjà familiers avec JS, avec au moins quelques mois d'expériences derrière vous. Donc, pour tirer pleinement parti de Get Started, assurez-vous de pratiquer, d'écrire du code avec JS pour vous forger une expérience.

Même si vous avez déjà beaucoup codé en JS, ce livre ne devrait pas être lu en diagonale voire zappé; prenez le temps de digérer ce qui vous est proposé ici. **Un bon départ dépend toujours du premier pas**

## Qu'est-ce que c'est que ce nom ?
--
Le nom JavaScript est probablement le nom le plus confus et incompris des noms de langage de programmation.

Est-ce que ça a un rapport avec Java ? Est-ce seulement la forme scriptée de Java ? Est-ce seulement pour écrire des scripts et non des vrais programmes ?

La vérité, c'est que le nom JavaScript est né d'une forme de magouille en marketing. Quand Brendan Eich a conçu ce langage, son nom de code était Mocha. Chez Netscape, en interne, la marque LiveScript était utilisée. Mais quand il a fallu le nommer publiquement, "JavaScript" a remporté tous les votes.

Pourquoi ? Parce que ce langage a d'abord été conçu pour attirer un public constitué majoritairement de programmeurs Java, et parce que le mot "script" était populaire et impliquaient la notion de programmes plus légers. Ces "scripts" légers auraient été les premiers intégrés dans les pages de ce nouveau truc appelé le web !

En d'autres termes, JavaScript était un stratagème marketing pour positionner ce langage comme une alternative acceptable au plus connu et plus lourd langage Java. Ils auraient très bien pu l'appeler "WebJava" à ce niveau-là.

Il y a des ressemblances en surgace entre le code JavaScript et le Java. Ces similitudes ne viennent pas d'un développement partagé, mais parce que les 2 langages ciblaient des développeurs et développeuses avec des attentes de syntaxes venues du C (et par extension, du C++).

Par exemple, on utilise `{` pour commencer un bloc de code et `}` pour le fermer, comme en C/C++ et en Java. On utilise aussi le `;` pour ponctuer la fin d'une déclaration.

D'une certaine façon, les liens juridiques sont plus profonds que cette histoire de syntaxe. Oracle (par l'intermédiare de Sun), la compagnie qui possède Java possède également la marque officielle "JavaScript" (via Netscape). Cette marque n'est pratiquement jamais appliquée et ne le sera probablement jamais.

Pour ces différentes raisons, certains ont suggérés d'utiliser JS au lieu de JavaScript. C'est un sigle très commun, si ce n'est même un bon candidat pour un nom officiel. D'ailleurs, ces livres utiliseront la plupart du temps le terme JS pour se référer à ce langage.

Et pour s'éloigner encore plus de la marque appartenant à Oracle, le nom officiel du langage spécifié par TC39 et formalisé par les standards ECMA, c'est ECMAScript. Et d'ailleurs, depuis 2016, le nom officiel a aussi été suffixé avec l'année de révision; à l'heure où nous écrivons ces lignes, on en est à ECMAScript2019, ou son abbréviation "ES2019".

En d'autres termes, le JavaScript/JS qui tourne sur votre navigateur ou dans Node.js est une implémentation des standards ES2019.

|NOTES : |
|---|
|N'utilisez pas les termes "JS8" ou "ES8" pour parler de JS. Certains le font, mais cela entretient la confusion. "ES20xx" ou JS devrait suffire à vous faire comprendre. |

Que vous l'appeliez JavaScript, JS, ECMAScript, ou ES2019, ce n'est clairement pas une variante du langage Java !

> "Java is to JavaScript as ham is to hamster." --Jeremy Keith, 2009

## Spécifications du langage
--

J'ai mentionné plus haut TC39, le comité de pilotage technique qui gère JS. Leur tâche principale est de gérer les spécifications techniques du langage. Ils se réunissent régulièrement pour voter sur chaque modification validée, qu'ils soumettent ensuite à ECMA, l'organisation des standards.

La syntaxe et le comportement de JS sont définis dans les spécifications ES.

ES2019 est la 10e spécification/révision numérotée majeure depuis la création de JS en 1995, donc, dans l'url officielle de la spécification hebergée par ECMA, vous trouverez "10.0" :

https://www.ecma-international.org/ecma-262/10.0/

Le comité TC39 comprend entre 50 et environ 100 personnes provenant d'une large section d'entreprises ayant investis dans le web, telles que les créateurs de navigateurs (Mozilla, Google, Apple) et fabricants d'appareils (Samsung, etc.). Tous les membres de ce comité sont des volontaires, mais la plupart sont des employés desdites compagnies et recoivent donc une compensation pour leur devoir envers le comité.

Le comité TC39 se réunit environ tous les 2 mois, pendant à peu près 3 jours, pour examiner le travail effectué par ses membres depuis le meeting précédent, discuter de problèmes et voter des propositions. Le lieu des meetings change en fonction des entreprises membres qui souhaitent accueillir le comité.

Toutes les propositions du TC39 passent par un processus en 5 étapes, et puisqu'on est des développeurs, c'est à partir de 0 ! De l'étape 0 à l'étape 4. Pour en savoir plus sur le processus complet, vous pouvez cliquer ici : https://tc39.es/process-document/

L'étape 0 signifie en gros que quelqu'un du TC39 pense que c'est une bonne idée et prévoit de la défendre et de bosser dessus. Ce qui signifie que beaucoup d'idées que des non-membres du TC39 "proposent" via les réseaux sociaux ou des blogs sont en réalité la "pré-étape 0".  Il faut qu'un membre du TC39 choisisse votre idée et la défende pour être officiellement considérée à "l'étape 0".

Une fois qu'une proposition a atteint l'étape 4, elle est élligible pour être incluse dans la prochaine révision annuelle du langage. Il peut se passer de quelques mois à quelques années pour qu'une proposition passent toutes les étapes.

Toutes les propositions sont gérées dans le repository public sur le GitHub du TC39 : https://github.com/tc39/proposals

Tout le monde, du TC39 ou non, peut participer aux discussions publiques et au processus de travail sur les propositions.
Mais seuls les membres du TC39 peuvent assister aux réunions et voter les propositions et changements. Donc, dans les faits, les membres du TC39 portent sur leurs épaules le poids de la direction que va prendre JS.

Contrairement à un mythe bien établi, il n'y a pas plusieurs versions de JS dans la nature. Il n'y a qu'un seul JS, le standard officiel maintenu par TC39 et ECMA.

Dans les années 2000, quand Microsoft maintenait un fork d'une version rétro-ingéniérée (et pas complètement compatible) de JS appelée "JScript", on pouvait effectivement parler de "plusieurs versions" de JS. Mais cela fait très longtemps que ce n'est plus le cas. C'est daté, et faux de dire ça de JS de nos jours.

Tous les navigateurs principaux et fabricants d'appareils se sont engagé à ce que leurs implémentations JS soient conforme à la spécification. Bien sûr, les moteurs implémentents des fonctionnalités à des instans différents. Mais le cas où le moteur V8 (le moteur JS de Chrome) implémente une fonctionnalité qui serait incompatible avec le moteur SpiderMonkey (le moteur JS de Mozilla) ne devrait jamais arriver.

Cela signifie que vous pouvez apprendre un JS et vous fier à ce seul JS partout et tout le temps.

### Le web gouverne tout (JS)
--

Tandis que le tableau des environnement qui font tourner JS s'étend régulièrement (des navigateurs aux serveurs (Node.js), aux robots, ampoules, aux...), l'environnement que contrôle JS, c'est le web. En d'autres termes, comment l'implémentation de JS dans les navigateurs web est, en toute logique, la seule réalité qui compte.

Pour la plus grosse part, le JS qui est défini dans les spécifications et le JS qui tourne dans les moteurs JS des navigateurs est le même. Mais il y a tout de même certaines différences à connaître.

Parfois, les spécifications JS vont inventer ou redéfinir des comporter, et pourtant, ça ne va pas exactement correspondre au fonctionnement des moteurs JS des navigateurs. Ce genre d'incompatibilités est historique : les moteurs JS ont plus de 20 ans de comportements observables autour de cas particuliers de fonctionnalités sur lesques repose le contenu web. En tant que tels, les moteurs JS vont parfois refuser de se conformer aux spécifications dictées parce que ça casserait le contenu web.

Dans ces cas-là, souvent, le TC39, va revenir en arrière et simplement se conformer aux réalités du web. Par exemple, le TC39 prévoyait d'ajouter une méthode `contains(..)` aux tableaux, mais on a découvert que ce nom entrait en conflit avec de vieux frameworks JS toujours usités sur certains sites, donc, ils ont changé le nom pour `includes(..)`. La même chose s'est produite avec une crise tragi-comique de la communité JS connue comme le "smooshgate", où la méthode `flatten(..)` a finalement été renommée `flat(..)`.

Mais de temps en temps, le TC39 décide que la spécification doit rester ferme sur certains points, même s'il y a peu de chances que les moteurs JS des navigateurs s'y conforment.

La solution ? L'annexe B, "Fonctionnalités additionnelles d'ECMAScript pour les Navigateurs Web". La spécification JS inclut cette annexe pour détailler les écarts connus entre la spécification JS officielle et la réalité de JS sur le web. En d'autres termes, il y a des exceptions qui sont autorisées uniquement pour le web; d'autres environnements JS doivent se tenir à la spécification à la lettre.

Les sections B.1 et B.2 couvrent les ajouts à JS (côté syntaxe et API) que le JS du web inclus, toujours pour des raisons historiques, mais que le TC39 ne prévoit pas de spécifier formellement dans le cœur de JS. Des exemples comme les littéraux octaux préfixés à 0, les utilitaires globalisés `escape(..)/unescape(..)`, les "helpers" de String comme `anchor(..)` et `blink()` et la méthode RegExp `compile(..)`.

La section B.3 évoque certains conflits qui font que le code peut tourner à la fois dans des moteurs JS web et non-web, mais où le comportement peut être visiblement différent, et montrant des résultats différents. La plupart des changements listés impliquent des situations qui sont considérées comme des erreurs précoces quand le code est exécuté en mode strict.

Les pièges à éviter de l'annexe B ne sont pas rencontrées souvent, mais c'est toujours bon de savoir comment les éviter pour plus de sûreté. Autant que possible, collez vous à la spécification JS et ne vous fiez pas sur le comportement qui ne s'applique que dans certains environnements JS.

### Pas tous les (web) JS
--

Est-ce que ce bout de code est du JS ?

```Javascript
alert("Hello, JS!");
```

Ca dépend de comment vous voyez les choses. la fonction `alert(..)` montrée ici n'est pas incluse dans la spécification JS, mais est bien dans tous les environnements web JS. Pourtant, vous ne la trouverez pas dans l'annexe B, alors qu'est-ce qu'il se passe ?

Différents environnements JS (comme les moteurs JS de navigateurs, Node.js, etc.) ajoutent des API au scope globale de vos programmes JS, ce qui vous ajoute des compétences spécifiques à cet environnement, comme par exemple, la possibilité de faire apparaître une pop-up de style "alerte" dans le navigateur de l'utilisateur.

En fait, un large pan d'API qui ressemble à du JS, comme `fetch(..)`, `getCurrentLocation(..)`, et `getUserMedia(..)` sont tours des API web qui ressemblent à du JS. En Node.js, on peut accéder à des centaines de méthodes d'API venant de divers modules inclus, comme `fs.write(..)`.

Un autre exemple classique, c'est le `console.log(..)`
 (et toutes les autres méthodes console.* !). Elles ne sont pas spécifiées en JS, mais en raison de leur utilité universelle, elles sont définies par quasiment tous les environnements JS, grâce à un certain consensus.

Donc `alert(..)` et `console.log(..)` ne sont pas définis par JS. Mais ils ressemblent à du JS. Elles sont des fonctions et des méthodes d'objets qui obeissent aux règles de syntaxe de JS. Le comportement derrière elles est contrôlé par l'environnement qui éxécute le moteur JS, mais en surface, elles doivent absolument se conformer à JS pour pouvoir jouer sur le terrain de jeu de JS.

La plupart des différences entre navigateurs donc les gens se plaignent avec des "JS est tellement incohérent !" sont en réalité lié aux différences dans la façon dont les environnements fonctionnents, pas dont le langage JS fonctionne.

Donc un appel à `alert(..)`, c'est du JS, mais l'alerte elle-même est en vérité juste un invité, qui ne fait pas partie de la spécification JS officielle.

### C'est pas toujours JS

Utiliser la console/REPL (Read-Evaluate-Print_Loop, Lire-Evaluer-Imrpimer-Boucler) via le _developer tool_ (ou Node) de votre navigateur ressemble à un environnement JS de prime abord. Mais ce n'est pas le cas.

Le _developer tools_ est ... un outil pour les développeurs et développeurs. Ils mettent l'accent sur l'experience des dev' (DX). Ce n'est pas l'objectif de cet outil d'être le reflet parfaitement exact d'un environnement respectant strictement la moindre nuance de la spécification JS. Ainsi, il existe beaucoup de trucs bizarres qui peuvent se compter comme un "piège à éviter" si vous considérez la console comme un pur environnement JS.

Cette praticité est une bonne chose d'ailleurs ! Je suis ravi que le _developer tools_ me facilite la vie en tant que développeur ! Je suis ravi d'avoir une expérience utilisateur sympa grâce à l'autocomplétion des variables et propriétés, etc. Je souligne juste le fait qu'on ne devrait pas s'attendre à ce que cet outil soit rigoureusement soumis aux règles de JS, parce que ce n'est tout simplement pas le but de cet outil.

Puisque ces outils varient d'un navigateur à l'autre, et puisque ces derniers changent (parfois très souvent), je ne vais pas donner d'exemples de code spécifique dans ce texte, sinon, le livre risque d'être dépassé très rapidement.

Mais je vais juste donner quelques exemples de bizarreries qui ont été vraies plusieurs fois dans plusieurs environnements de console JS, pour renforcer l'idée que ça n'assume pas le comportement JS natif tout en les utilisant :

* Comment une déclaration `var` ou de fonction dans le scope global, au plus haut niveau de la console créé réellement une variable globale (et reflète les propriétés de window, et vice-versa !).

* Que se passe-t-il lors de la déclaration de plusieurs `let` et `const` dans le scope global.

* Comment en écrivant `"use strict";` dans la console et que l'appui sur la touche _entrée_ active le mode strict le temps de la session de cette console, de la même façon que cette même ligne dans un fichier .js , et que ça marche aussi bien que si on écrit `"use strict";` et qu'on continue d'écrire au-delà de cette ligne et que le strict mode soit tout de même activé pour cette session.

* Comment dans le mode non-strict, la liaison par défaut de `this` marche à l'appel d'une fonction et comment "l'objet global" va contenir des variables globales attendues.

* Comment la "remontée" (_hoiting_) (Voir le livre 2, Scope & Closures) fonctionne mau travers de plusieurs lignes déclarées.

Et plusieurs autres...

La console ne prétend pas être un compilateur JS qui gère votre code exactement de la même manière que le moteur JS gèe un fichier .js. Elle essaie juste de te faciliter la vie avec quelques lignes de code dont tu peux voir le résultat immédiatement. Ce sont des cas d'usages très différents, et donc, ce ne serait pas pertinent de s'imaginer que cet outil soit capable de gérer les deux de la même manière.

Ne faites pas confiance au comportement que vous voyez dans la console comme une représentation exacte de la sémantique JS; pour ça, lisez les spécifications. Pensez plutôt la console comme un environnement "JS-friendly". C'est utile dans bien des cas.

### Plusieurs visages
--

Le terme "paradigme" dans le contexte d'un langage informatique se réfère à une vaste (et presque universel) approche pour un code structuré. Dans un paradigme, il y a une myriade de variations de style et de form qui distingue les programmes, incluant un nombre infini de bibliothèques différentes et de frameworks qui laissent une signature unique dans chaque code.

Mais peu importe le style d'un programme, on voit quasiment toujours de façon évidente le paradigme au premier coup d'œil de n'importe quel programme.

Quelques catégories de paradigmes de code dont le procédural, l'orienté objet (OO / classes) et le fonctionnel (FP) :

* Le style procédural consiste à organiser le code dans une progression du haut vers le bas, au travers d'une série d'opérations prédéfinies, habituellement collectées ensemble dans des unités reliées appelées procédures.
* Le style Orienté Objet organise le code en collectant la logique et les données ensemble dans des unités appelées des classes.
* le style fonctionnel organise le code en fonction (pures, au contraire des procédures), et l'adpatation de ces fonctions en des valeurs.

Les paradigmes ne sont ni bonnes ni mauvaises. Ils sont une direction qui guide les programmeurs dans leur approche des problèmes et des solutions, la façon de structurer et de maintenir leur code.

Certains langages sont très fortement orientés vers un paradigme : C est procédural, Java/C++ sont quasi totalement orientés objet, et Haskell est du pur fonctionnel.

Mais beaucoup de langages supportent aussi des patterns qui peuvent provenir de différents paradigmes. Les langages dits "multi-paradigmes" offrent une grande flexibilité. Dans certains cas, un seul programme peut même avoir du code qui reflète l'expression de ces paradigmes côté à côte.

Javascript est très clairement un langage multi-paradigmes. Vous pouvez écrire du code procédural, orienté objet ou de type fonctionnel et vous pouvez changer d'avis une ligne après l'autre au lieu d'être forcé dans un choix unique.

### En arrière et en avant
--

Un des principes les plus fondamentaux qui guident JavaScript est la rétrocompatibilité. Beaucoup ne comprennent pas les implications de ce terme, et la confonde souvent avec une autre forme de compatibilité : la compatibilité en amont.

Voyons cela.

La compatibilité en amont, cela signifie qu'une fois que quelque chose est considéré comme du JS valide, il n'y aura pas de chagement dans le futur qui causeront l'invalidité du code JS. Du code écrit en 1995, bien que primitif ou même limité, devrait a priori toujours fonctionner aujourd'hui. Comme les membres du TC39 le répètent souvent : "on ne casse pas le web !".

L'idée, c'est que les développeurs et développeuses JS peuvent écrire du code avec la certitude que leur code ne cassera pas de façon imprévisible à cause d'une mise à jour d'un navigateur. Ce qui rend la décision de choisir JS pour écrire un programme sage et plus sûre pour le futur.

Cette "garantie" n'est pas une petite affaire. Maintenir des années de compatibilité en arrière, qui s'étendent sur 25 ans d'histoire du langage, c'est un poids à porter et toute une série de défis à relever. Il est difficile de trouver un autre example d'un tel engagement de compatibilité en amont.

S'en tenir à ses principes a un coût qu'on ne peut pas ignorer. La bar est très haute pour include des changements ou étendre le langage; chaque décision devient permanente, erreurs comprises. Une fois que c'est dans le JS, on ne peut pas l'enlever, parce que ça pourrait casser du code, même si on aimerait vraiment vraiment la supprimer !

Il y a quelques rares exceptions à cette règle. JS a eu quelques changements rétro-incompatibles, mais le TC39 fait très attention dans ces cas-là. Ils étudient le code existant sur le web (via des données de navigateurs compilées) pour estimer l'impact d'une telle action, et les navigateurs décident et votent pour déterminer s'ils sont prêts à subir les foudres des utilisateurs à cause de ce changement à impact faible par rapport aux avantages de la correction ou de l'amélioration du langage pour bien plus de sites (et d'utilisateurs).

Ce type de changements est rare, et sont quasiment toujours à faible impact sur la plupart des sites.

Comparons la rétrocompatibilité à son pendant, la compatibilité en amont. Etre compatible en amont signifie qu'en ajoutant des choses à un langage, ça ne devrait pas casser le programme s'il tourne sur un vieux moteur JS. JS n'est pas compatible en amont en dépit du souhait de beaucoup de monde, et c'est même un mythe que certains croient.

HTML et CSS, au contraire, sont compatibles en amont mais pas rétrocompatibles. Si vous déterrez un vieux code HTML/CSS écrit en 1995, c'est tout à fait possible que ça ne fonctionne pas (ou pas de la même façon) aujourd'hui. Mais, si vous utilisez une nouvelle fonctionnalité de 2019 dans un navigateur de 2010, la page n'est pas "cassée" -- Le HTML/CSS qui n'est pas reconnu est zappé, tandis que ce qui est connu sera traité normalement.

Cela semble une bonne idée d'inclure la compatibilité en amont dans un design de langage de programmation, mais c'est globalement peu pratique à faire. Le balisage (HTML) ou le style (CSS) sont déclaratifs par nature, donc c'est bien plus simple de "zapper" des déclarations inconnues avec un impact minimal envers les autres déclarations reconnues.

Mais le chaos et le non-déterminisme s'ensuivrait si un moteur de langage de programmation zappait certaines déclarations (ou même des expressions !) qu'ils ne comprendrait pas, parce que c'est impossible de s'assurer que les parties suivantes du programme ne s'attendent pas à ce que la partie zappée ait été traitée.

Bien que JS n'est pas, et ne peux pas être, compatible en amont, c'est essentiel de reconnaître la rétrocompatibilité de JS, y compris les avantages durables pour le web et les contraintes et difficultés qui en découlent pour JS.

### Combler les lacunes

Puisque JS n'est pas compatible en amont, cela signifie qu'il y a toujours un risque potentiel de lacune entre un code que vous pouvez écrire qui serait du JS valide, et le plus vieux moteur que votre site ou application doit supporter. Si vous exécutez un programme qui utilise une fonctionnalité ES2019 dans un moteur de 2016, il y a de fortes chances que le programme s'arrête et crash.

Si la fonctionnalité est une nouvelle syntaxe, le programme va  être incapable de compiler et de s'exécuter, en renvoyant une erreur de syntaxe (syntax error). Si la fonctionnalité est une API (comme le `Object.is(..) de ES6`), le programme peut s'exécuter jusqu'à un certain point, mais renverra une exception d'exécution (runtime exception) et s'arrêter une fois qu'il rencontre la référence à cette API inconnue.

Est-ce que cela signifie que les développeurs et développeuses JS devraient toujours rester à la traîne du progrès et utiliser du code qui fonctionnerait sur les plus vieux environnements qu'ils doivent supporter ? Non !

Mais cela veut tout de même dire que les développeurs et développeuses JS doivent prendre des précautions particulières pour combler cette lacune.

Pour les syntaxes nouvelles et incompatibles, la solution, c'est la transpilation. Transpiler, c'est un terme inventé par la communauté pour décrire l'utilisation d'un outil pour convertir le code source d'un programme d'une forme à une autre (mais toujours comme du code source textuel). Typiquement, les problèmes de compatibilité en amont liés à la syntaxe sont résolus en utilisant un transpileur (le plus connu étant Babel (https://babeljs.io)) afin de convertir de cette version récente de syntaxe de JS vers une syntaxe équivalente plus vieille.

Par exemple, un ou une développeuse pourrait écrire ce type de code :
```javascript
if (something) {
    let x = 3;
    console.log(x);
}
else {
    let x = 4;
    console.log(x);
}
```

Voici à quoi ce code ressemblerait dans la branche du code source pour cette application. Mais pour créer le ou les fichiers à déployer sur un site web public, le transpiler Babel pourrait convertir le code pour qu'il ressemble à ça :
```javascript
var x$0, x$1;
if (something) {
    x$0 = 3;
    console.log(x$0);
}
else {
    x$1 = 4;
    console.log(x$1);
}
```

Le code original s'appuie sur le `let` pour créer des variables `x` scopées par bloc à la fois dans le `if` et dans le `else`, ce qui fait que les deux n'interfèrent pas l'un avec l'autre.
Un programme équivalent (avec une ré-écriture minimale) que Babel peut produire, c'est de choisir deux noms différents de variables, chacune avec un nom unique, produisant ainsi le même résultat de non-interférence entre les deux.

|Notes :|
|--|
|Le mot clé `let` a été ajouté dans ES6 (en 2015). L'exemple de transpilation ci-dessus serait utile uniquement dans le cas où l'application doit tourner dans un environnement JS antérieur à ES6. L'exemple ici est juste pour illustrer simplement. Quand ES6 était tout récent, le besoin d'une telle transpilation était assez courant, mais en 2020, c'est de moins en moins commun de supporter des environnements antérieurs à ES6. La "cible" utilisée pour la transpilation est donc une fenêtre coulissante qui se déplace vers le haut uniquement lorsque des décisions sont prises pour qu'un site/une application cesse de prendre en charge un ancien navigateur/moteur. |

Vous vous demandez peut-être : pourquoi s'embêter avec un outil pour convertir d'une syntaxe nouvelle à une vieille syntaxe ? Pourquoi ne pas simplement écrire ces deux variables et zapper l'utilisation du mot clé `let` ? La raison est que c'est fortement recommandé que les développeurs et développeuses utilisent la dernière version de JS afin que leur code soit propre et communique ses idées de la façon la plus efficace.

Les développeuses et développeurs devraient se concentrer sur l'écriture d'un code propre, avec les nouvelles syntaxes, et laisser les outils s'occuper de rendre compatible et déployer ce code aux environnements JS plus vieux.

### Combler les lacunes

Si le problème de compatibilité n'est pas dû à une nouvelle syntaxe, mais à une méthode API manquante qui a été ajoutée récemment, la solution la plus courante est de fournir une définition pour cette méthode d'API manquante qui se comporte comme si le vieil environnement la connaissait déjà nativement. Ca s'appelle un polyfill.

Par exemple :
```javascript
// getSomeRecords() nous retourne une promesse
// Pour les données qu'il va fetcher.
var pr = getSomeRecords();

// Montre le cercle de chargement le temps de
// récupérer les données
startSpinner();

pr
.then(renderRecords)   // C'est rendu si tout s'est bien passé
.catch(showError)      // affiche une erreur si c'est pas le cas
.finally(hideSpinner)  // cache toujours le cercle de chargement.
```
Ce code utilise une fonctionnalité d'ES2019, la méthode `finally(..)` sur une promesse de prototype. Si ce code est utilisé dans un environnement antérieur à ES2019, la méthode `finally(..)` n'existant pas, une erreur sera affichée.

Un polyfill pour remplacer `finally(..)` dans un environnement pré-ES2019 ressemblerait à ça :

```javascript
if (!Promise.prototype.finally) {
    Promise.prototype.finally = function f(fn){
        return this.then(
            function t(v){
                return Promise.resolve( fn() )
                    .then(function t(){
                        return v;
                    });
            },
            function c(e){
                return Promise.resolve( fn() )
                    .then(function t(){
                        throw e;
                    });
            }
        );
    };
}
```

|ATTENTION :|
|--- |
|Il s'agit ici d'un exemple simplifié pour illustrer notre propos. N'utilisez pas ce polyfill pour remplacer `finally(..)`; utilisez toujours un polyfill robuste, officiel si possible, comme par exemple la collection de polyfills de ES-Shim.|

La déclaration d'un `if` protège la définition du polyfill en s'assurant de ne pas l'exécuter si l'environnement dans lequel tourne le moteur JS a déjà défini cette méthode. Dans des environnements plus vieux, le polyfill est ainsi défini, mais dans des environnements plus récents, le `if` est simplement ignoré.

Les transpileurs comme Babel détectent de quel polyfill votre code a besoin et les fournit automatiquement pour vous. Mais parfois, il sera peut-être nécessaire de les inclure ou définir explicitement, ce qui sera similaire au bout de code qu'on vient de voir.

Ecrivez toujours un code avec les fonctionnalités les plus appropriées pour communiquer clairement et efficacement vos idées. En général, cela signifie utiliser la version stable la plus récente de JS. Essayez d'éviter d'impacter négativement votre code en essayant de coder vous même les lacunes de syntaxe ou d'API. C'est à cela que servent les outils !

La transpilation et les polyfills sont deux techniques très efficaces pour combler les lacunes entre le code qui utiliser les dernières fonctionnalités stables du langage, et les vieux environnements que le site ou l'application doit supporter. Puisque JS ne va pas arrêter de s'améliorer, les lacunes ne s'en iront jamais. Ces deux techniques devraient faire partie intégrante de la chaîne de production de chaque projet JS à l'avenir.

