**Monorepo:**

Utilise un référentiel unique pour héberger tout le code des multiples bibliothèques ou services qui composent les projets d'une entreprise. 
À l'extrême, l'intégralité de la base de code d'une entreprise – couvrant divers projets et codage dans plusieurs language – est hébergée dans un référentiel unique.

Les boucles automatisées vous permettent de créer, tester et déployer du code sans erreurs (en particulier le spectre des erreurs humaines). Ces avancées contribuent à rationaliser toutes les phases de livraison des applications.

L’élément principal du monorepo est l’espace de travail. Chaque application et package que vous créez se trouvera dans son propre espace de travail, avec son propre package.json. Les espaces de travail peuvent dépendre les uns des autres, ce qui signifie que votre espace de travail de documentation peut dépendre d'shared-utils.

Les espaces de travail sont gérés par la même CLI (interface de ligne de commande) qui installe vos dépendances.

Vous disposerez également d'un espace de travail racine, package.json dans le dossier racine de votre base de code. C'est un endroit utile pour :

- Préciser les dépendances présentes dans l'ensemble du monorepo
- Ajout d'activités qui opèrent sur l'ensemble du monorepo, pas seulement sur des zones de travail individuelles
- Ajout de la documentation sur l'utilisation de monorepo

<br>

- Gestion simplifiée des processus DevOps (centralitation):

La centralisation du code permet de créer des pipelines pour l'ensemble du projet avec un énorme gain de temps. En conséquence, ils deviennent plus rigoureux avec des processus éprouvés, prédictifs et reproductibles. Tout cela facilite l’ajout de nouvelles portions de code.

Nous pouvons désormais coupler des pipelines en fonction de l'étape (construire, tester, déployer). Les processus sont lancés en parallèle, ce qui était impossible ou fortement contraint en multirepo. Chaque ensemble de tests étant commun, le développement de fonctionnalités affectant plusieurs applications est beaucoup plus rapide.

Ces fonctionnalités sont par exemple utiles lorsqu'un problème s'étend sur deux (ou plus) bibliothèques child avec un bug existant sur la bibliothèque dépendante. Avec plusieurs repository, il peut être difficile de trouver le morceau de code où le problème se produit.

En plus de cela, nous devrons déterminer quel repository utiliser pour créer le problème, puis croiser les membres d'autres équipes pour aider à résoudre le problème.
Cependant, avec un monorepo, la localisation des problèmes de code et la collaboration pour la résolution de problèmes deviennent plus faciles à réaliser.

- Nouveaux développeurs:

Lorsque de nouvelles personnes commencent à travailler, elles doivent télécharger le code et installer les outils nécessaires pour commencer à accomplir leurs tâches. Supposons que le projet soit réparti sur plusieurs repository, chacun possédant ses propres instructions d'installation et les outils requis. Dans ce cas, la configuration initiale sera complexe et, le plus souvent, la documentation ne sera pas complète, ce qui obligera les nouveaux membres de l'équipe à se tourner vers des collègues pour obtenir de l'aide.

Un monorepo simplifie les choses. Puisqu’il existe un seul emplacement contenant tout le code et la documentation, cela peut simplifier la configuration initiale.

- Refactoring:

Lorsque vous refactorisez du code dans une application en direct, plusieurs bibliothèques seront concernées. Si l'état est pris en charge par le multi-repository, vous devrez gérer tous les différents contenus du pull pour le maintenir synchronisé avec ceux qui peuvent être rivetés dans un endroit sûr.

Un monorepo facilite l'exécution de toutes les modifications et codes pour tous les bibliothèques à soumettre sous une seule pull request.

- Autres fonctionnalités:

Avec le monorepo, nous pouvons configurer tous les tests pour toutes les bibliothèques à exécuter à chaque fois qu'une seule bibliothèque est modifiée. En conséquence, la probabilité que les modifications apportées à certaines bibliothèques aient un effet négatif sur d'autres est réduite.

- Team:

Bien que cela ne soit pas impossible, avec une approche monorepo, il devient difficile d'inspirer des sous-cultures uniques au sein de différentes équipes. Puisqu’ils partageront le même repository, ils partageront très probablement les mêmes méthodologies de programmation et de gestion et utiliseront les mêmes outils de développement.

Les développeurs peuvent récupérer et intégrer toutes les modifications en cours, renforçant ainsi la compréhension globale. Vous n'avez plus besoin d'examiner plusieurs projets pour trouver des problèmes cachés, tout est à portée de main. Nous modifions et testons rapidement, raccourcissant ainsi le cycle de validation. Changer de contexte est également plus facile : un développeur travaillant sur plusieurs projets ou intégrant le travail d'un collègue peut comparer les différences beaucoup plus rapidement.

- Qualité du code:

Nous n'avons plus besoin de dupliquer, d'insérer une bibliothèque dans un projet principal et d'aller et venir continuellement. Avoir tout le code à portée de main vous aide à identifier les problèmes plus rapidement. Nous pouvons également alléger le fardeau des applications en éliminant le code mort sans craindre qu’il soit utilisé ailleurs. Partager le même environnement réduit les désaccords entre les équipes.

Lorsque l'on modifie une bibliothèque, ces vérifications sont effectuées en premier : le code est-il conforme à la réglementation en vigueur ? Est-ce que ça fonctionne comme prévu ? Nous testons ensuite les applications qui l'utilisent pour valider sa bonne intégration. Il s'agit d'une approche en couches, passant des tests (unitaires) les plus simples aux plus complexes (end-to-end).

- Accélération du développement: 

Le monorepo facilite la sortie régulière de nouvelles fonctionnalités. Nous rattrapons les modifications des autres développeurs beaucoup plus rapidement. Avec l’automatisation des processus, la production devient plus fluide. En accélérant la boucle de rétroaction, nous pouvons itérer plus rapidement.

**Multi-Repo:**

Du coup, L’utilisation de plusieurs repository peut donner lieu à divers problèmes: 

- Les bibliothèques doivent être constamment resynchronisées
- Peut fragmenter les équipes

Entrerprise qui utilisent le Monorepo: 

Google, Facebook, Twitter et Uber se sont tous publiquement engagés à adopter l'approche monorepo. 
Microsoft gère le plus grand monorepo Git de la planète pour héberger le code source du système d'exploitation Windows.

En bref, pour faciliter le développement entre les projets, l'équipe doit regrouper le code de l'application dans un référentiel unique (monorepo). L’objectif est d’améliorer les processus de mise à jour, de faciliter la collaboration et d’accélérer le développement de l’écosystème.

Comment faire la transition progressivement:

- Diviser la migration en plusieurs phases intégrant l'impact potentiel pour les collègues.
- Testez chaque étape en amont, lorsque cela est possible.
- Détaillez chaque étape avec une liste de tâches « prête à l'emploi » pour le grand jour.
- Planification des étapes de migration en période de faible fréquentation.
- Simulation de scénarios de crise pour anticiper les problèmes et prédire les actions à mettre en œuvre.

Si je devais résumer brièvement :

- Récupération simplifiée des modifications.
- Partage de la configuration de certains outils.
- Gestion réduite des modifications sur plusieurs applications.
- Simplification du développement : tout est disponible au même endroit et il est beaucoup plus facile de naviguer entre les zones.

Turborepo:

Turborepo est un système de construction intelligent optimisé pour les bases de code JavaScript et TypeScript.

Vos tâches de base de code, comme le lint, la construction et les tests, ne s'exécutent pas aussi vite qu'elles le pourraient. Turborepo utilise la mise en cache pour alimenter la configuration locale et accélérer le CI (Continuous Integration).

Turborepo exploite des techniques avancées de système de build pour accélérer le développement, à la fois sur votre machine locale et sur CI/CD.

Il fournit des fonctionnalités puissantes telles que :

- Création incrémentielle rapide
- Mise en cache informatique locale
- Mise en cache informatique distribuée
- Orchestration des activités locales
- Visualisation du graphique de dépendance
- Partage de code source

L’idée principale du monorepo est de ne jamais recalculer le travail déjà effectué précédemment. Il conserve un cache des versions précédentes pour chaque projet, puis l'utilise pour les versions suivantes. Il suit le résultat de toute tâche effectuée, puis ignore le travail déjà effectué. 
Turborepo est conçu pour être adopté progressivement, vous pouvez donc l'ajouter à notre base de code en quelques minutes. Accélérez vos tâches grâce à une planification intelligente, minimisant le processeur inactif.

Les caches de build sont généralement générés et contrôlés sur votre ordinateur local. Par conséquent, si vous examinez le code d'un membre de votre équipe, vous devrez également le créer localement. La mise en cache à distance partage le cache à l'échelle mondiale, le transformant en une « boîte de dépôt de votre dossier de distribution ». Vercel propose une mise en cache à distance gratuite sur les versions Turborepo même si vous n'hébergez pas votre application sur les serveurs Vercel.

Avec la mise en cache à distance, les builds peuvent atteindre des temps de build étonnamment rapides en fournissant un moyen de partager les calculs compilés et les artefacts de code dans Vercel. Ces artefacts peuvent être une sortie de journal, une sortie de build, des blobs de données, etc. La mise en cache à distance identifie tous les artefacts nécessaires déjà générés dans le même code PR et les recycle sur différentes machines. Ce recyclage ou réutilisation peut se faire lors du processus de création Vercel ou via un CI/CD externe.

Turborepo peut rendre votre pipeline 10 fois plus rapide. Il offre une immense valeur prête à l'emploi avec un pipeline de compilation déclarative, d'excellentes options de débogage/profilage et une excellente documentation.