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

