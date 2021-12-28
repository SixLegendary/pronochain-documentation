---
title: Husky
summary: Installation et configuration de husky
---

# Husky

**Husky** est un outil qui permet de créer facilement des hooks git. Un hook git est une **action réalisée avant ou après une commande git**.
Au lieu de créer manuellement des hooks git dans le répertoire .git, Husky permet d'ajouter simplement les hooks dans le package.json ou par commande.

**Pourquoi Husky ?**

- Plus de **25 000 étoiles** sur github
- Utilisé par plus de **700 000 repositories** (notamment webpack, babel, Next.js..)
- Plus de **4 millions de téléchargements par semaine**

### Avant toute chose

Vous n'avez pas besoin de suivre le tutoriel qui suit lorsque vous récupérez l'API. Tout sera déjà installé et configuré, il suffira simplement de lancer la commande :
    
    npm ci

Le tutoriel qui suit n'est écrit que dans un but informatif pour en apprendre plus.

### Installation et utilisation

Pour installer Husky, il suffit simplement de rentrer la commande npm :

    npm install husky -D

Ensuite, il faut ajouter un nouveau script npm nommé "prepare" et l'exécuter une première fois :

    npm set-script prepare "husky install"
    npm run prepare

Il ne reste plus qu'à ajouter des hooks selon les besoins avec la commande :

    npx husky add .husky/GIT_HOOK "COMMAND"

Par exemple, si je souhaite lancer la commande "npm test" avant chaque commit, j'utiliserai la commande suivante :

    npx husky add .husky/pre-commit "npm test"

Voici la liste des **hooks git disponibles** :
- pre-commit
- prepare-commit-msg
- commit-msg
- post-commit
- post-checkout
- pre-rebase

### Ressources :

- [Repository Husky](https://github.com/typicode/husky)
- [Package NPM](https://www.npmjs.com/package/husky)
- [Git hooks](https://www.atlassian.com/git/tutorials/git-hooks)
