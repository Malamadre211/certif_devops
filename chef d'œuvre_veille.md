Devops
Conteneurisation : Docker
Tests :
Unitaire : Vitest
End-to-End : Playwright
Qualité logiciel
Logger : Winston
Linter : eslint
Prettier
StoryBook

**DEVOPS**

- Conteneurisation : Docker

Docker est un outil open source qui permet de créer, tester et déployer des applications très rapidement, grâce à la création de conteneurs, c'est-à-dire des progiciels légers, autonomes et exécutables qui incluent tout le nécessaire pour exécuter une application : code, runtime, outils système, système. bibliothèques et paramètres.

Les conteneurs proviennent d'images, une image n'est rien de plus qu'un fichier où sont spécifiées toutes les étapes nécessaires à la création d'un conteneur. Les images sont déclarées à l'aide d'une série de balises pouvant accepter un ou plusieurs paramètres.

En fait, Docker est capable de recycler toutes les parties communes que les images ont entre elles grâce au fait que les images sont en réalité constituées de plusieurs couches superposées également appelées images intermédiaires, cela rend les images modulaires et donc faciles à réutilisation à d’autres fins.

**Pourquoi utiliser Docker**

Docker est devenu le standard de facto pour le déploiement d'applications en production. Les avantages découlant de l’utilisation de conteneurs sont nombreux :

- Facilité de reproduction des environnements : Comme nous l'avons dit, les conteneurs sont des progiciels qui incluent tout ce dont vous avez besoin. De plus, le fait qu'ils soient apatrides, donc non modifiables, garantit que lorsque le logiciel arrive en production, il n'y a pas de surprises.
- Évolutivité : Les conteneurs sont rapides à lancer, il devient donc également rapide de les faire évoluer.
- Efficacité : Les conteneurs sont beaucoup plus légers que les VM, et beaucoup plus d'applications peuvent être exécutées sur le même serveur.
- Performance : Docker n'a besoin que des ressources qu'il demande, tandis que les VM ont souvent besoin de ressources qui leur sont exclusivement allouées.
- Fonctionnalités : les conteneurs peuvent accéder aux fonctionnalités du système d'exploitation auxquelles la VM ne peut pas accéder, par exemple les cartes graphiques.
- Intégrabilité : Il s'intègre très bien dans les pipelines CI/CD, chaque fois que le code est modifié, le pipeline peut créer une nouvelle image qui est déployée dans un conteneur de votre infrastructure, le tout en quelques minutes.

**Tests**

**Les critères d'un bon test unitaire**

- Unité  

Un test unitaire se concentre sur une seule unité, qui est le plus petit
élément identifiable de notre application. Selon les contextes et les
langages de programmation, plusieurs éléments du code peuvent
constituer une unité. Il peut s’agir d’une fonction, d’une méthode de
classe, d’un module, d’un objet…

- Isolation :
Les tests unitaires visant à tester chaque unité en isolation totale par
rapport aux autres, ils doivent pouvoir être indépendants des tests lui
précédents. Votre suite de tests unitaires doit pouvoir être lancé
dans n'importe quel ordre sans affecter le résultat des tests suivants.
C'est pourquoi l'utilisation de Mocks et Stubs est indispensable aux
tests unitaires.

- Rapidité
La petite échelle des tests unitaires et le fait qu’ils soient écrits par
les développeurs pendant le développement font que les tests
unitaires sont souvent très rapides. Ils peuvent ainsi être lancés très
fréquemment, idéalement à chaque modification dans le code ou à
chaque compilation. Cette façon de procéder permet de repérer les
bugs bien plus rapidement : si vous avez accidentellement cassé une
fonctionnalité pendant votre dernier changement, vous le saurez
immédiatement et n’aurez pas à chercher bien loin pour le réparer.

- L ’indépendance
Veillez à isoler vos tests unitaires au maximum et à les rendre totalement
indépendants les uns des autres. Ne faites jamais appel à une base de
données ou à une API externe même si votre classe en dépend :
utilisez toujours des données de test les plus proches possibles des
données réelles. On peut utiliser des mocks et des stubs pour simuler
le fonctionnement des autres modules qui ne sont pas dans le scope
de notre unité, ceux-ci seront testés unitairement de leurs côtés.

- Automatisés
Les tests unitaires doivent produire un résultat Pass ou Fail
automatiquement. Ils doivent pouvoir être interprétés par un test
runner et ne pas demander au développeur de lire ou d'observer
manuellement que le test a réussi ou échoué. C'est pourquoi les tests
automatisés, qu'ils soient unitaires ou non, sont exécutés par un test
runner et évalués par une librairie d'assertion.

- Rejouabilité
L'intérêt de bons tests unitaires réside dans le fait qu'ils soient
idempotents, c’est-à-dire que pour un test donné, quel que soit
l'environnement ou le nombre de fois qu'il soit joué, il produise
toujours le même résultat. C'est pourquoi il est indispensable de faire
abstraction des appels en base de données ou des requêtes HTTP
pour avoir un test unitaire robuste.

**Vitest**

Vitest est un framework de tests unitaires JavaScript. Il a été créé pour compléter Vite, un outil qui permet de gérer et de créer des applications Web basées sur JavaScript.

Il est possible d'utiliser Vitest sans Vite, mais cela nécessitera généralement plus d'efforts de la part des développeurs pour configurer les tests. Si vous utilisez Vitest pour tester le code que vous gérez via Vite, la plupart de la configuration des tests se fera automatiquement, grâce à l'intégration étroite entre Vitest et Vite.

Vitest est compatible avec la plupart des API Jest. Cela signifie que la plupart des tests développés pour Jest peuvent également être exécutés à l'aide de Vitest, avec peu ou pas de modifications nécessaires.

En tant que framework de test, la caractéristique la plus importante de Vitest est l'accent mis sur la vitesse.

Un autre avantage de Vitest est son intégration étroite avec Vite, qui permet une configuration et une gestion de test simples. Si vous gérez le code de votre application via Vite, vous pouvez réutiliser la plupart des configurations, plugins et autres éléments que vous avez déjà développés lors de la création de vos tests.

**Playwright**

Playwright permet des tests E2E sur la plupart des navigateurs (Chrome, Firefox, Safari et Edge).

En plus, Playwright donne la possibilité de faire des tests en "multi thread" et donc en parallèle les uns des autres. Un vrai gain de temps en performance !

Playwright gère très bien les attentes d'action pour interagir sur les éléments d'interactions, comme le ferait un utilisateur humain de façon intuitive.

De plus, il vient avec un outil de "codegen". Son but est d'ouvrir un navigateur sur une url précise, de faire son scenario en tant qu'humain et il génère tout le code pour reproduire le scénario à l'identique. Il ne manque plus que quelques assertions et le test est terminé.

Enfin, avec Playwright le debugging est facilité puisqu'il est capable de remonter dans le temps, de connaître l'état du DOM à une étape clé et même générer des vidéos du parcours testé. 

Playwright est Open Source ce qui lui permet aussi une intégration native dans la Github CI (détenue aussi par Microsoft).

**Logger : Winston**

De bonnes pratiques de logging sont cruciales pour surveiller et dépanner vos serveurs Node.js. Ils vous aident à suivre les erreurs dans l'application, à découvrir des opportunités d'optimisation des performances et à effectuer différents types d'analyses sur le système (par exemple en cas de pannes ou de problèmes de sécurité) pour prendre des décisions critiques concernant les produits.

Node.js est livré avec l'API de console, qui contient des méthodes pouvant être utilisées pour la journalisation. Mais les journaux ont tendance à être difficiles à lire ou à filtrer car ils sont au format texte.

La plupart des outils de journalisation fournissent une prise en charge JSON prête à l'emploi et vous pouvez facilement ajouter des dates, trier ou envoyer des journaux vers les destinations souhaitées.

Winston est la bibliothèque de logging la plus populaire pour Node.js. Il vise à rendre le logging plus flexible et extensible en dissociant différents aspects tels que les niveaux de log, le formatage et le stockage afin que chaque API soit indépendante et que de nombreuses combinaisons soient prises en charge. Il utilise également les flux Node.js pour minimiser l'impact sur les performances de la mise en œuvre de la log dans votre application.

**Linter : Eslint**

Le linting est la vérification automatisée de votre code source pour détecter les erreurs de programmation et de style. Cela se fait à l'aide d'un outil anti-peluches (également connu sous le nom de linter). Un outil lint est un analyseur de code statique de base.

Par exemple, le linteur détectera :

- les variables qui n'existent pas
- les variables inutilisées
- les doubles déclarations de variables, de fonctions, etc...
- la mauvaise organisation du code
- le non respect des bonnes pratiques d'écriture de code
- les erreurs de syntaxe

Un linteur se présente sous la forme d'un petit programme indépendant auquel on peut demander de lire et de vérifier les sources de notre projet.

L’intérêt d’ESLint va bien au-delà d’une simple correction syntaxique pour rendre votre code plus uniforme. C’est une véritable béquille intellectuelle pour développeurs de façon à passer plus de temps à livrer un programme fonctionnel plutôt que faire de la chasse au bug.

ESLint est un plugin permettant d’uniformiser la mise en forme du code entre les différents développeurs contribuant au projet.

Prettier vient en complément de ESLint et vient forcer la correction de vos erreurs suivant un set de règles. Là où ESLint de base ne fait que lister les erreurs, Prettier vient scanner votre fichier à la recherche d’erreurs de style et vient automatiquement les corriger.

Il est possible d’utiliser Prettier en complément d’ESLint à condition d’avoir configuré le même set de règles.

Prettier est un formateur de code avisé. Il applique un style cohérent en analysant votre code et en le réimprimant avec ses propres règles qui prennent en compte la longueur maximale de la ligne, en encapsulant le code si nécessaire.

**Storybook**

Storybook est un outil open source qui permet de développer des composants en complète isolation, ce qui donne lieu à une création plus organisée et donc plus efficace. 

C’est un environnement de développement permettant de naviguer dans un catalogue de composant (book) et de voir les différents états d’un composant par use-case (story).

Il est compatible avec la plupart des frameworks front-end (Vue, React, Angular...). 
Il s'exécute dans son propre environnement.

Storybook est un outil formidable qui permet à la fois de documenter les projets, construire une bibliothèque de composants réutilisables et développer des composants en isolation.