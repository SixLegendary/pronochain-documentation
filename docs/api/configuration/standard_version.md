---
title: Standard Version
summary: Installation et configuration de standard version
---

# Standard Version

**Standard version** est un outil pour le versioning utilisant [semver](https://semver.org) et la génération de CHANGELOG alimenté par [Conventional Commits](https://www.conventionalcommits.org/).

### Installation et utilisation

Pour installer Standard Version, il suffit simplement de rentrer la commande npm :

    npm install standard-version -D

Il faut ensuite ajouter un script npm dans le `package.json` :

    {
        "scripts": {
            "release": "standard-version"
        }
    }

Vous pouvez désormais utiliser la commande npm release.

### Configuration

Un fichier `.versionrc.json` peut être créé à la racine du projet pour définir sa propre configuration.

Ceci a été fait pour le projet Pronochain avec la configuration suivante :

    {
        "types": [
            {"type": "feat", "section": "Fonctionnalités"},
            {"type": "fix", "section": "Correctifs"},
            {"type": "chore", "hidden": true},
            {"type": "docs", "hidden": true},
            {"type": "style", "hidden": true},
            {"type": "refactor", "hidden": true},
            {"type": "perf", "hidden": true},
            {"type": "test", "hidden": true}
        ],
        "commitUrlFormat": "https://dev.azure.com/SixLegendary/Pronochain/_git/pronochain-back/commit/{{hash}}",
        "compareUrlFormat": "https://dev.azure.com/SixLegendary/Pronochain/_git/pronochain-back/branchCompare?baseVersion=GT{{previousTag}}&targetVersion=GT{{currentTag}}"
    }

Nous avons redéfini les **noms des sections** pour que le CHANGELOG généré soit en français, puis nous avons défini les **URL de commit et de comparatif** pour avoir des **versions cliquables** dans le CHANGELOG.

- [Repository Standard Version](https://github.com/conventional-changelog/standard-version)
- [Package NPM](https://www.npmjs.com/package/standard-version)
