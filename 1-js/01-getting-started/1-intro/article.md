# Introduction à JavaScript

Découvrons ensemble ce qu'il y a de si spécial avec JavaScript, ce que nous pouvons faire avec ce langage et quelles autres technologies informatiques se marient bien avec lui.

**Notes du traducteur :** Certains termes sont difficilement traductibles car dans le développement informatiques les mots sont souvent les mêmes qu'en anglais et leurs traductions ne leur donnent pas totalement leurs sens. De ce fait, des traductions seront apportées le plus fidèlement possible mais les termes anglais seront gardés là où c'est nécessaire. Je ne serais trop vous conseiller de vous renseigner sur leurs sens et de les apprendre rapidement. ;)

## Qu'est-ce que JavaScript ?

A la base, *JavaScript* a été créé pour *"rendre les pages vivantes"*.

Les programmes écrits dans ce langage sont appelés *scripts*. Ils peuvent être écrits directement dans la page HTML et sont exécutés automatiquement au fur et à mesure du chargement de la page.

Les scripts sont fournis et exécutés en tant que simple text brut. Ils n'ont pas besoin d'être compilés ou préparés pour être lancés.

Sur ce point, JavaScript est très différent d'un autre langage de programmation appelé [Java](https://fr.wikipedia.org/wiki/Java_(langage)).

```smart header="Pourquoi <u>Java</u>Script ?"
Quand JavaScript a été créé, il portait un nom différent : "LiveScript". Seulement, Java était un langage très populaire à cette époque et il a été pensé que positionner ce nouveau langage en tant que "petit frère" de Java pourrait l'aider à devenir populaire.

Mais au fil de son évolution, JavaScript est devenu un langage informatique totalement indépendant avec ses propres spécifications techniques, appelées [ECMAScript](https://fr.wikipedia.org/wiki/ECMAScript). A présent, le JavaScript n'a *absolument* rien à voir avec le Java. Souvenez-vous en !
```

Aujourd'hui, Javascript peut non seulement être exécuté par un navigateur, côté client, mais aussi par un server. Globalement, n'importe quel appareil informatique disposant d'un programme spécial appelé [moteur JavaScript](https://fr.wikipedia.org/wiki/Moteur_JavaScript) peut exécuter du JavaScript.

Les navigateurs ont un moteur JavaScript intégré aussi appelé "machine virtuelle JavaScript".

Il existe différents moteurs JavaScript : 

- [V8](https://es.wikipedia.org/wiki/Chrome_V8) -- dans Chrome et Opera.
- [SpiderMonkey](https://fr.wikipedia.org/wiki/SpiderMonkey) -- dans Firefox.
- ... il y a aussi d'autres noms comme "Trident", "Chakra" pour les différentes versions de IE, "ChakraCore" pour Microsoft Edge, "Nitro" et "SquirrelFish" pour Safari, etc.

Les termes énumérés ci-dessus sont utiles à retenir parce qu'ils sont utilisés dans de nombreux articles Internet sur le développement et nous les utiliserons aussi. Par exemple, si "une fonctionnalité X est supportée par V8", cela veut probablement dire qu'elle fonctionne sur Chrome et Opéra.

```smart header="Comment les moteurs fonctionnent-t-ils ?"

Les moteurs JavaScript sont compliqués mais les bases élémentaires sont faciles à comprendre.

1. Le moteur JavaScript (embarqué s'il s'agit d'un navigateur) lit ("parse" en anglais) le script.
2. Ensuite, il le convertit (Sorte de compilation) en langage machine.
3. Enfin, le code machine est exécuté par la machine.

Le moteur optimise le script à chaque étape du processus. Il surveille même le script compilé lors de son exécution, analyse les données qui le traversent et applique des optimisations au code machine d'après ces analyses. Au final, les scripts sont assez rapides.
```

## Que peut faire JavaScript dans un navigateur ?

Le JavaScript moderne est un langage de programmation "sécurisé". Il ne fournit pas d'accès *bas niveau* au processeur ou à la mémoire vive, parce qu'il a été initialement créé pour les navigateurs et ceux-ci n'en ont pas besoin.

Les capacités de JavaScript dépend de l'environnement qui l'exécute. Par exemple, [Node.JS](https://wikipedia.org/wiki/Node.js) supporte des fonctions qui permettent à JavaScript de de lire et d'écrire des fichiers, d'exécuter des requêtes sur le réseau, etc...

Le JavaScript inclus dans les navigateurs peut faire à peu près tout ce qui touche à la manipulation des pages internet (aussi nommé comme la manopulation du *DOM*), ainsi qu'interargir avec l'utilisateur et le serveur web.

Quelques points clés des capacités de JavaScript dans un navigateur :

-  Ajouter du nouveau code HTML à une page, changer le contenu existant de la page, modifier des styles.
- Réagir aux actions de l'utilisateur, déclencher des actions selon ses clics, ses mouvements de souris ou ses appuis sur les touches du clavier.
- Envoyer des requêtes à travers le réseau à des serveurs distants, télécharger des données en aynchrone (technologies connues : [AJAX](https://en.wikipedia.org/wiki/Ajax_(programming)) et [COMET](https://en.wikipedia.org/wiki/Comet_(programming))
- Lire et écrire des cookies, poser des questions à l'utilisateur, afficher des messages.
- Sauvegarder des données coté client (*"Local Storage"*)

## Que ne peut pas faire JavaScript dans un navigateur ?

Les capacités du JavaScript dans un navigateur sont limitées pour assurer la sécurité de l'utilisateur. Le but est d'empêcher une page malveillante d'accéder à des données privées de l'utilisateur et de lui nuire.

Ci-dessous des exemples de ces restrictions :

- JavaScript n'a pas accès au disque dur quand il est exécuté dans le navigateur. Ainsi, il ne peut lire ni écrire des fichiers sur le disque dur de l'ordinateur. Il ne peut pas non plus exécuter des programmes. Globalement, il n'a aucun accès aux fonctions système du système d'exploitation.

    Les navigateurs modernes permettent de travailler avec des fichiers, mais l'accès est très limité et donné seulement dans le cas où l'utilisateur fait certaines actions comme de "lâcher" un fichier dans la fenêtre d'un navigateur ou en le sélectionnant par un tag `<input>`.

    Il existe des moyens d'interargir avec la caméra, le microphone ou d'autres appareils, mais ces utilisateurs demandent une permission explicite de l'utilisateur. De cette façon, une page web autorisant JavaScript ne pourra discrètement activer votre webcam, observer les environnements et envoyer les informaions à la [NSA](https://en.wikipedia.org/wiki/National_Security_Agency).

- Les différents onglets et fenêtres du navigateur ne savent rien à propos des autres onglets et fenêtres et ne peuvent pas interargir avec. Quelques fois, un fenêtre pourra utiliser JavaScript pour ouvrir un seconde fenêtre, mais même dans ce cas, un fenêtre ne peut pas accèder à une page qui vient d'un site différent (domaine, protocole ou port différent).

    Cette règle est appelée the "Same Origin Policy" (Traduire "la politique de l'origine identique"). Pour travailler avec ce système, *les deux pages* doivent contenir un bout de code JavaScript spécial qui gère l'échange de données entre les pages.

    Cette limite est mise en place à nouveau pour la sécurité de l'utilisateur. Une page provenant de `http://nimportequelsite.com` qu'un utilisateur a ouvert ne doit pas être capable d'accèder à un autre onglet du navigateur avec l'adresse `http//gmail.com` pour y dérober des informations.

- JavaScript peut facilement communiquer à travers Internet vers le serveur d'où vient la page actuelle. Mais ses capacités à recevoir des données depuis d'autres sites internets ou d'autres domaines est limitée. Bien que possible, cette fonctionnalité requiert un accord explicite (précisé dans les entêtes HTTP) fournit par la ressource distante. Encore une fois, ces restrictions sont mises en place pour la sécurité.

![](limitations.png)

<br>
Ces restrictions n'existent pas si JavaScript est utilisé à l'extérieur d'un navigateur, par exemple sur un serveur. Les navigateurs modernes permettent aussi d'installer des plug-ins/extensions qui peuvent étendre ces permissions.

## Qu'est ce qui donne à JavaScript son unicité ?

Il y a au minimum *trois* choses géniales à propos de JavaScript : 

```compare
+ Intégration complète avec HTML/CSS.
+ Les choses simples sont faites simplement.
+ Supporté par tous les navigateurs principaux et activé par défaut.
```

Combinés, ces trois points n'existent dans aucune technologie des navigateurs autre que JavaScript.

C'est ce qui fait que JavaScript est unique et c'est pourquoi c'est l'outil le plus répandu pour créer des interfaces de navigateurs.

Quand on planifie d'apprendre une nouvelle technologie, il est bénéfique de regarder ses perspectives. Donc, allons regarder du côté des tendances qui incluent des nouveaux langages et des capacités de navigateur.

## Les langages "à travers" JavaScript

La syntaxe de JavaScript ne convient pas aux besoins de tout le monde. Des personnes différentes veulent des fonctionnalités différentes.

C'est ce qui est attendu, parce que les projets et les exigences sont différents pour chacun.

Récemment, une pléthore de nouveaux langages sont apparus. Ces langages sont *transpilés* (convertis) en JavaScript avant d'être lancés dans le navigateur.

Les outils modernes offrent une tranpilation très rapide et transparente, autorisant les développeurs à coder dans un autre langage et à le transformer automatiquement.

Exemples de ces langages :

- [CoffeeScript](http://coffeescript.org/) a une syntaxe en "sucre". Il apporte une syntaxe plus courte, permet d'écrire du code plus précis et plus clair. Les dévelopeurs Ruby l'aiment généralement.

- [TypeScript](http://www.typescriptlang.org/) est tourné vers l'ajout d'un typage fort, pour simplifié les développements de systèmes complexes. Il est développé par Microsoft.

- [Dart](https://www.dartlang.org/) est un langage indépendant qui a son propre moteur d'exécution qui tourne dans un environnment autre qu'un navigateur (comme les applications mobiles). Initialement offert par Google en tant que replacement de JavaScript, dorénavant les navigateurs ont besoin de ce moteur pour transpiler le code en JavaScript comme pour les langages précédents.

Il en existe bien plus. Evidemment, utiliser un de ces langages requiert de déjà connaître JavaScript afin de bien comprendre ce que nous sommes en train de faire.

## Sommaire

- JavaScript a été initialement spécifiquement pour être utilisé par les navigateurs uniquement mais il est maintenant utilisé par bien d'autres environnements.
- Aujourd'hui, JavaScript a une position unique en tant que langage navigateur le plus répandu avec une intégration complète avec HTML/CSS.
- Il y a beaucoup de langages qui sont "transpilés" en JavaScript and fournissent ainsi certaines fonctionnalités. Il est recommandé de jeter un coup d'oeil à ces langages, même brièvement, une fois que vous maîtriserez JavaScript.