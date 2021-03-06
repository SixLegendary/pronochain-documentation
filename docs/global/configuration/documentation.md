---
title: Documentation
summary: Information sur la documentation
---

# Documentation

Il a été décidé de centraliser toutes nos documentations des différentes solutions afin d'éviter de se rendre dans les quatre solutions pour trouver une information. Nous avons choisi **squidfunk/mkdocs** pour plusieurs raisons :

- **Initialisation et installation très simple** : fonctionne sur une **image docker** sans dépendances.
- **Ergonomie et fonctionnalités** : de base, le design de la documentation est **plutôt beau** et la multitude des fonctionnalités implémentées de base nous permet de structurer notre documentation de la meilleure des manières.
- **Hébergement en ligne gratuit** sur GitHub.

## Consultation

Si ce que vous souhaitez correspond uniquement à de la **consultation** rendez vous sur la documentation en ligne : [Documentation Pronochain](https://sixlegendary.github.io/pronochain-documentation/) . Sinon, si vous souhaitez **ajouter ou modifier une page**, suivez les étapes dans **Installation**

## Installation

Pour installer la documentation, il vous suffit de **cloner le répertoire GIT**. Dans ce répertoire, le fichier ***docker-compose.yml*** va vous permettre de récupérer l'image et de la build sur votre docker. Une fois démarré, il suffira de se rendre sur **localhost:9090**.

Rendez-vous à la **racine de la solution** de la documentation et tapez la commande dans une **console** (**powershell** de préférence si vous êtes sous Windows) :

    docker-compose up --build -d

Cette commande va **build l'image** et **démarrer la documentation**. Si vous souhaitez seulement la démarrer, car vous l'avez déjà build :

    docker-compose up -d

???+ warning not-expand "Installer la police "Poppins-Regular.ttf""

## Ajouter une page

Créer votre branche depuis **master**.
Tout ce qui concerne la navigation se trouve dans le fichier ***mkdocs.yml***. Ce fichier comporte plusieurs informations, dont l'**ajout d'extentions**. La seule partie dans ce fichier qui doit être **modifiée** est le code à la **fin du fichier**.
La **structure et l'indentation** de la navigation doivent être respectées, comme pour les dossiers et les fichiers dans le dossier **docs**.

```yaml
nav:
  - Accueil: index.md
  - Global:
    - Configuration:
      - Documentation: global/configuration/documentation.md
  - Génération NFT:
    - Initialisation: generation_nft/index.md
    - Configuration:
      - Variables d'environnements: generation_nft/configuration/variables_environnements.md
      - Pre-commit: generation_nft/configuration/pre_commit.md
      - Visual Studio Code: generation_nft/configuration/vs_code.md
    - Python:
      - Architecture: generation_nft/python/architecture.md
      - Packages: generation_nft/python/packages.md
      - Tests: generation_nft/python/tests.md
      - Règles et nomenclatures: generation_nft/python/regles.md
      - Logging: generation_nft/python/logging.md
```

Pour ce qui est du contenu des pages et des différentes syntaxes, il faut connaître le **markdown**. De plus, vous pouvez vous rendre sur [cette page](https://squidfunk.github.io/mkdocs-material/reference/) pour voir la liste des extensions que vous pouvez utiliser.

## Déployer en ligne

???+ danger not-expand "ATTENTION, NE JAMAIS PULL REQUEST, REBASE OU MERGE LA BRANCHE origin/gh-pages OU gh-pages SUR master OU UNE AUTRE BRANCHE !"

Lorsque vous avez **modifié** la documentation, il est impératif de **redéployer** les nouveautées.

Faites une **pull request** que vous allez **directement accepter** dans le répertoire GitHub. [LIEN RAPIDE](https://github.com/Pronochain/pronochain-documentation/pulls).

Une fois que la pull request de **votre branche à master** a été **validée et mergée**, faites les étapes qui suivent.

Installer sur votre **ordinateur** le package **mkdocs-material** (voir documentation de la solution **Génération NFT -> Initialisation** pour installer correctement Python sur votre ordinateur).

    pip install mkdocs-material


Une fois que votre **documentation est écrite**, **commité vos changements** et **pushé votre branche**.

    git push nom-de-ta-branche

La section qui va suivre nécessite de se rendre sur le **Google DRIVE -> Pronochain -> Informations -> Identifiants -> Identifiants compte**.
Il se peut qu'une **popup GitHub** s'ouvre pour vous demander les informations de connexion pour la **première action** sur le répertoire. Pour la première popup avec le logo de GitHub visible, remplissez avec **l'email et le mot de passe**. La seconde popup : **l'email**, et la dernière : le **PAT** (**personal access token**).
Une fois votre branch push en distant, faites en sorte de mettre votre **branche sur master** grâce à la **pull request** du github (vous pouvez directement sans reviewers).
Une fois **master à jour en distant et en local**, faites:

    mkdocs gh-deploy --force

Et voilà !
