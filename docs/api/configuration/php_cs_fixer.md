---
title: PHP CS FIXER
summary: Installation et configuration de php cs fixer
---

# Php cs fixer

**Php cs fixer** est un outil qui permet de corriger le code pour qu'il respecte des **normes de codage PHP** telles que définies dans les **PSRs**, etc. ou d'autres **normes communautaires** comme celles de Symfony. Il est également possible de définir son propre style par le biais de la configuration.

### Installation et utilisation

Pour installer Php cs fixer, il suffit simplement de rentrer la commande composer :

    composer require friendsofphp/php-cs-fixer --dev

Il est désormais possible de l'utiliser avec la commande :

    ./vendor/bin/php-cs-fixer fix /path/to/fix

Cependant, pour des raisons de praticité, il est recommandé de créer deux nouveaux scripts dans `composer.json` :

    "scripts": {
        "sniff": [
            "./vendor/bin/php-cs-fixer fix -vvv --dry-run --show-progress=dots"
        ],
        "lint": [
            "./vendor/bin/php-cs-fixer fix -vvv --show-progress=dots --allow-risky=yes"
        ]
    }

La première, `composer sniff` permet d'avoir un **aperçu des bouts de codes qui ne respectent pas les normes** sans pour autant le corriger.
<br />
La seconde, `composer lint`, permet de **corriger** les manquements aux normes.

Il est possible de n'utiliser que la seconde commande, cependant il peut être utile d'avoir un aperçu avant correctif.

### Configuration

Un fichier `.php-cs-fixer.php` peut être créé à la racine du projet pour définir sa propre configuration.

Ceci a été fait pour le projet Pronochain avec la configuration suivante :

    <?php

    use PhpCsFixer\Config;
    use PhpCsFixer\Finder;
    
    $rules = [
        '@PhpCsFixer' => true,
    ];
    
    $finder = Finder::create()
        ->in(__DIR__)
        ->exclude(['bootstrap', 'storage', 'vendor'])
        ->name('*.php')
        ->notName('*.blade.php')
        ->ignoreDotFiles(true)
        ->ignoreVCS(true)
    ;
    
    return (new Config())
        ->setFinder($finder)
        ->setRules($rules)
        ->setRiskyAllowed(true)
        ->setUsingCache(true)
    ;

Dans un premier temps, on définit les [ensembles de règles](https://github.com/FriendsOfPHP/PHP-CS-Fixer/blob/master/doc/ruleSets/index.rst) qui vont être utilisés.
L'ensemble **@PhpCsFixer** est utilisé car celui-ci implémente l'ensemble @Symfony (qui respecte tous les PSRs) ainsi que d'autres [règles](https://github.com/FriendsOfPHP/PHP-CS-Fixer/blob/master/doc/rules/index.rst).

Il est possible de ne pas utiliser d'ensemble de règles et de définir une à une le comportement de chaque règle.

Ensuite, on configure le fixer en indiquant le **répertoire** dans lequel il va agir (répertoire courant), les **dossiers** que l'on ne prend pas en compte, les **fichiers** pris ou non en compte et on ignore les fichiers dot (.env par exemple).

Enfin, on applique notre configuration.

### Ressources :

- [Repository PhpCsFixer](https://github.com/FriendsOfPHP/PHP-CS-Fixer)
