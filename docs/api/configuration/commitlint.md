---
title: Commitlint
summary: Installation et configuration de commitlint
---

# Commitlint

**Commitlint** vérifie si les messages de commit respectent le format de [commit conventionnel](https://www.conventionalcommits.org/).

### Prérequis

- [Husky](https://sixlegendary.github.io/pronochain-documentation/api/configuration/husky/)

### Installation et utilisation

Pour installer Commitlint, il suffit simplement de rentrer la commande npm :

    npm install --save-dev @commitlint/config-conventional @commitlint/cli

Et configurer commitlint pour utiliser la config-conventional

    module.exports = {extends: ['@commitlint/config-conventional']}

Enfin, ajouter la commande Husky :

    npx husky add .husky/commit-msg 'npx --no-install commitlint --edit'
