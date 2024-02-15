Introduction:

Mon projet chef d'ouvre est basé sur une application qui génère des histoires interactives grâce à l'intelligence artificielle, conçue pour aider les enfants ayant des difficultés de concentration grâce également à la gamification de l'application, qui permet d'obtenir des points d'expérience en fin de lecture utilisables pour débloquer de nouvelles histoires ou pour personnaliser l'avatar.

Après avoir analysé le projet et compris ce qui était nécessaire au bon développement de l'application, j'ai fait le choix technologique général suivant:

Choix des technologies
Design
Figma
Font-End
Projet qui se focalise sur une utilisation mobile et tablette : React Native (technologie soutenue par Meta).

Intérêt :
cross-plateform. Cette technologie permet de concevoir des applications mobiles pour les deux systèmes d'exploitations principaux sur ces appareils : IOs et Android.
Technologie similaire à React reposant donc sur du javascript. Langage de programmation (JS/TS) et Framework Front-end qu'on maîtrise, pas de nécessité d'apprendre un autre langage de programmation et proximité avec le framework ce qui n'est pas forcément le cas pour les autres solutions.
Comparaisons:
Autres technologies cross-plateform :
Flutter, technologie soutenue par Google. Permet également le développement d'applications sur IOs et Android. Nécessite cependant l'apprentissage du langage Dart.
Technologies natives :
Swift, langage supporté par Apple pour les applications natives sur IOs. Descendant de l'Objective-C.
Kotlin, langage suporté par Google pour les applications natives sur Android. Deuxième langage natif pour Android après Java.
Nous n'avons pas opté pour des solutions natives car elles imposaient trop de contraintes. Soit il fallait abandonner l'idée de développer une application qui fonctionnerait sur les deux systèmes d'exploitation soit doubler, à minima, le temps de développement pour utiliser chacune des technologies natives.

Back-End
Utilisation de NodeJS avec le framework Express.
ORM (Object-Relational Mapping) : Sequelize
Base de données
Base de données en Postgres. Utilisation de PostgreSQL15.
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

# DEVOPS : Optimisation du Cycle de Vie des Applications

## Conteneurisation : Docker

Le choix de Docker pour la conteneurisation s'explique par la révolution qu'il a instaurée dans notre approche du cycle de vie des applications. Docker offre une approche agile, transcendant les limitations classiques du développement, du test et du déploiement. Grâce à la création de conteneurs, Docker encapsule tous les éléments nécessaires à l'exécution d'une application, formant des unités autonomes. Cette approche présente une pléthore d'avantages, tels que la facilité de reproduction des environnements de développement, un déploiement ultrarapide, une efficacité opérationnelle accrue, des performances optimales, des fonctionnalités avancées répondant à divers besoins, et une intégration fluide dans nos pipelines CI/CD. La modularité des conteneurs et leur capacité à réutiliser des parties communes à travers des images intermédiaires facilitent la gestion et la mise à l'échelle de nos applications.

## Tests

### Unitaire : Vitest

Vitest a été choisi pour les tests unitaires JavaScript en raison de sa rapidité exceptionnelle et de son intégration transparente avec Vite. La configuration aisée des tests grâce à cette combinaison permet une couverture exhaustive pendant la phase de développement. La rapidité d'exécution des tests unitaires assure une validation rapide des fonctionnalités, facilitant ainsi la détection précoce des erreurs et garantissant la robustesse de nos applications.

### End-to-End : Playwright

L'adoption de Playwright pour les tests End-to-End est justifiée par sa polyvalence, offrant une prise en charge complète de divers navigateurs tels que Chrome, Firefox, Safari et Edge. La capacité de Playwright à effectuer des tests en parallèle représente un gain significatif en termes de performances. Son outil de "codegen" simplifie la création de scénarios en reproduisant les actions de l'utilisateur de manière automatisée. Les fonctionnalités avancées, telles que le retour dans le temps et la génération de vidéos, font de Playwright un choix incontournable pour le débogage approfondi et la garantie de performances optimales dans des scénarios réels.

## Qualité logicielle

### Logger : Winston

Winston s'est imposé comme le choix principal pour la journalisation dans les serveurs Node.js. Sa flexibilité et son extensibilité offrent une solution complète pour répondre aux besoins de surveillance, de dépannage et d'optimisation des performances. En offrant une gestion avancée des journaux, Winston contribue de manière significative à la fiabilité de nos applications, permettant une analyse approfondie des événements système et une réaction rapide aux incidents.

### Linter : Eslint

L'intégration d'ESLint dans le processus de développement vise à automatiser la détection des erreurs de programmation et de style. Au-delà de la correction syntaxique, ESLint favorise la cohérence du code entre les membres de l'équipe, créant ainsi une base solide pour la qualité globale du code source. Son rôle va au-delà de la simple détection d'erreurs, contribuant à l'adoption de bonnes pratiques de codage et à la création d'un code plus lisible et maintenable.

### Prettier

Prettier, en complément d'ESLint, apporte une dimension supplémentaire à la qualité logicielle en automatisant la correction des erreurs de style. Son rôle est essentiel pour garantir la cohérence visuelle du code, en imposant un formatage uniforme conforme aux meilleures pratiques. L'utilisation conjointe de Prettier et ESLint assure une cohérence maximale dans le formatage du code, renforçant ainsi la qualité et la lisibilité du code source.

## StoryBook

Le choix de Storybook pour le développement de composants en isolation repose sur sa capacité à créer un environnement de développement organisé et structuré. Storybook permet de constituer un catalogue organisé de composants, facilitant la visualisation des différents états par use-case. Cette approche simplifie considérablement le processus de développement en permettant aux équipes de se concentrer sur des composants spécifiques, favorisant ainsi une approche modulaire et une documentation intégrée. L'utilisation de Storybook contribue également à la création d'une bibliothèque de composants réutilisables, accélérant ainsi le développement global et assurant une cohérence visuelle et fonctionnelle dans l'ensemble de l'application.