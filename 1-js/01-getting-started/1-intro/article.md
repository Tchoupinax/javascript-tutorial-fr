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

Il existe des moyens d'interargir avec la caméra, le microphone ou d'autres appareils, mais ces utilisateurs demandent une permission explicite de l'utilisateur.


    There are ways to interact with camera/microphone and other devices, but they require a user's explicit permission. So a JavaScript-enabled page may not sneakily enable a web-camera, observe the surroundings and send the information to the [NSA](https://en.wikipedia.org/wiki/National_Security_Agency).
- Different tabs/windows generally do not know about each other. Sometimes they do, for example when one window uses JavaScript to open the other one. But even in this case, JavaScript from one page may not access the other if they come from different sites (from a different domain, protocol or port).

    This is called the "Same Origin Policy". To work around that, *both pages* must contain a special JavaScript code that handles data exchange.

    The limitation is again for user's safety. A page from `http://anysite.com` which a user has opened must not be able to access another browser tab with the URL `http://gmail.com` and steal information from there.
- JavaScript can easily communicate over the net to the server where the current page came from. But its ability to receive data from other sites/domains is crippled. Though possible, it requires explicit agreement (expressed in HTTP headers) from the remote side. Once again, that's safety limitations.

![](limitations.png)

Such limits do not exist if JavaScript is used outside of the browser, for example on a server. Modern browsers also allow installing plugin/extensions which may get extended permissions.

## What makes JavaScript unique?

There are at least *three* great things about JavaScript:

```compare
+ Full integration with HTML/CSS.
+ Simple things done simply.
+ Supported by all major browsers and enabled by default.
```

Combined, these three things exist only in JavaScript and no other browser technology.

That's what makes JavaScript unique. That's why it's the most widespread tool to create browser interfaces.

While planning to learn a new technology, it's beneficial to check its perspectives. So let's move on to the modern trends that include new languages and browser abilities.


## Languages "over" JavaScript

The syntax of JavaScript does not suit everyone's needs. Different people want different features.

That's to be expected, because projects and requirements are different for everyone.

So recently a plethora of new languages appeared, which are *transpiled* (converted) to JavaScript before they run in the browser.

Modern tools make the transpilation very fast and transparent, actually allowing developers to code in another language and autoconverting it "under the hood".

Examples of such languages:

- [CoffeeScript](http://coffeescript.org/) is a "syntactic sugar" for JavaScript, it introduces shorter syntax, allowing to write more precise and clear code. Usually Ruby devs like it.
- [TypeScript](http://www.typescriptlang.org/) is concentrated on adding "strict data typing", to simplify development and support of complex systems. It is developed by Microsoft.
- [Dart](https://www.dartlang.org/) is a standalone language that has its own engine that runs in non-browser environments (like mobile apps). It was initially offered by Google as a replacement for JavaScript, but as of now, browsers require it to be transpiled to JavaScript just like the ones above.

There are more. Of course even if we use one of those languages, we should also know JavaScript, to really understand what we're doing.

## Summary

- JavaScript was initially created as a browser-only language, but now it is used in many other environments as well.
- At this moment, JavaScript has a unique position as the most widely-adopted browser language with full integration with HTML/CSS.
- There are many languages that get "transpiled" to JavaScript and provide certain features. It is recommended to take a look at them, at least briefly, after mastering JavaScript.
