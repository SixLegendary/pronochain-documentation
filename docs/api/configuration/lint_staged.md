---
title: Lint Staged
summary: Installation et configuration de lint staged
---

# Lint staged

**Lint staged** est un outil conçu pour n’examiner que le travail stagé (git). En revanche, il nous incombe de lui dire quels fichiers traiter et avec quels outils.

### Installation et configuration

Pour installer Lint staged, il suffit simplement de rentrer la commande npm :

    npm install lint-staged -D

Il faut ensuite créé à la racine du projet un fichier `lint-staged.config.js` pour le configurer.

    module.exports = {
        '**/*.php': [
            'php ./vendor/bin/php-cs-fixer fix --config .php-cs-fixer.php --allow-risky=yes'
        ],
    };

Dans notre exemple, nous configurons que lint-staged doit seulement examiner les fichiers php avec la commande [php-cs-fixer](https://sixlegendary.github.io/pronochain-documentation/api/configuration/php_cs_fixer/).

Lint-staged est appelé lors du hook pre-commit à l'aide de [Husky](https://sixlegendary.github.io/pronochain-documentation/api/configuration/husky/).

- [Repository Lint-Staged](https://github.com/okonet/lint-staged)
- [Package NPM](https://www.npmjs.com/package/lint-staged)
