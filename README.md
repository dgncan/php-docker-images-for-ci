# php-docker-images-for-ci

[![Contributor Covenant](https://img.shields.io/badge/Contributor%20Covenant-v1.4%20adopted-ff69b4.svg)](CONTRIBUTING.md) [![WOSPM Badge](https://app.wospm.info/badge/A42eGp0GOw)](https://app.wospm.info/project/A42eGp0GOw) [![CircleCI](https://circleci.com/gh/umutphp/php-docker-images-for-ci/tree/master.svg?style=svg)](https://circleci.com/gh/umutphp/php-docker-images-for-ci/tree/master)

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**

- [Introduction](#introduction)
- [List of PHP Images](#list-of-php-images)
- [List of CI Tools](#list-of-ci-tools)
    - [PHP Code Sniffer](#php-code-sniffer)
    - [PHP Copy/Paste Detector (PHPCPD)](#php-copypaste-detector-phpcpd)
    - [PHP Dead Code Detector](#php-dead-code-detector)
    - [SensioLabs Security Checker](#sensiolabs-security-checker)
    - [PhpMetrics](#phpmetrics)
    - [Psecio Parse](#psecio-parse)
    - [PHP VarDump Check](#php-vardump-check)
    - [PHP Parallel Lint](#php-parallel-lint)
    - [PHP Magic Number Detector (PHPMND)](#php-magic-number-detector-phpmnd)
    - [composer.json Fixer](#composerjson-fixer)
    - [PHP Assumptions](#php-assumptions)
    - [churn-php](#churn-php)
    - [Fink](#fink)
    - [PHPMD](#phpmd)
    - [PHP_Testability](#php_testability)
    - [composer-normalize](#composer-normalize)
    - [infection](#infection)
- [Custom Tools](#custom-tools)
- [How to use images locally](#how-to-use-images-locally)
- [How to Use in Gitlab CI](#how-to-use-in-gitlab-ci)
- [How to Use in CircleCI](#how-to-use-in-circleci)
- [How To Contribute](#how-to-contribute)
- [Code of Conduct](#code-of-conduct)
<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Introduction ##

A repository  of Docker files to create images from official PHP images (latest version per master branch) with some CI tools installed. 

The tools that are installed by Composer are isolated by using different folder per tool and linked to `/usr/local/bin` folder.

## List of PHP Images ##
- php:5.6
- php:7.0
- php:7.1
- php:7.2
- php:7.3

## List of CI Tools ##

#### PHP Code Sniffer ####
[PHP_CodeSniffer](https://github.com/squizlabs/PHP_CodeSniffer) tokenizes PHP, JavaScript and CSS files and detects violations of a defined set of coding standards. PHP_CodeSniffer comes with two PHP scripts; the main `phpcs` script that tokenizes PHP, JavaScript and CSS files to detect violations of a defined coding standard, and a second `phpcbf` script to automatically correct coding standard violations.

```
docker run -v /path/to/project:/app umutphp/php-docker-images-for-ci:7.1 phpcs /app
```

#### PHP Copy/Paste Detector (PHPCPD) ####
[PHP Copy/Paste Detector (PHPCPD)](https://github.com/sebastianbergmann/phpcpd) is a Copy/Paste Detector (CPD) for PHP code. It checks all the files under the folder given as a parameter and determines the code blocks which are copied and pasted.

```
docker run -v /path/to/project:/app umutphp/php-docker-images-for-ci:7.1 phpcpd /app
```

#### PHP Dead Code Detector ####
[PHP Dead Code Detector](https://github.com/sebastianbergmann/phpdcd) is a Dead Code Detector (DCD) for PHP code. It scans a PHP project for all declared functions and methods and reports those as being "dead code" that are not called at least once.

```
docker run -v /path/to/project:/app umutphp/php-docker-images-for-ci:7.1 phpdcd /app
```

#### SensioLabs Security Checker ####
The [SensioLabs Security Checker](https://github.com/sensiolabs/security-checker) is a command line tool that checks if your application uses dependencies with known security vulnerabilities. It uses the [Security Check Web service](https://security.symfony.com/) and the [Security Advisories Database](https://github.com/FriendsOfPHP/security-advisories).

```
docker run -v /path/to/project:/app umutphp/php-docker-images-for-ci:7.1 security-checker security:check /app
```

#### PhpMetrics ####
[PhpMetrics](https://www.phpmetrics.org/) provides software metrics about PHP project and classes. It generates readable and accessible reports about maintainability, quality and complexity of a source code.

```
docker run -v /path/to/project:/app umutphp/php-docker-images-for-ci:7.1 phpmetrics /app
```

#### Psecio Parse ####
[Psecio Parse](https://github.com/psecio/parse) scanner is a static scanning tool to review your PHP code for potential security-related issues. 

```
docker run -v /path/to/project:/app umutphp/php-docker-images-for-ci:7.1 psecio-parse scan /app
```
#### PHP VarDump Check ####
[PHP VarDump Check](https://github.com/JakubOnderka/PHP-Var-Dump-Check) is a PHP console application for finding forgotten variable dump lines. It supports PHP build in method print_r, var_dump and var_export methods and also methods from Tracy debugger, Ladybug, Symfony, Laravel, Doctrine and Zend Framework.

```
docker run -v /path/to/project:/app umutphp/php-docker-images-for-ci:7.1 var-dump-check /app
```

#### PHP Parallel Lint ####
[PHP Parallel Lint](https://github.com/JakubOnderka/PHP-Parallel-Lint) checks syntax of PHP files faster than serial check with a fancier output. Running parallel jobs in PHP is inspired by Nette framework tests.

```
docker run -v /path/to/project:/app umutphp/php-docker-images-for-ci:7.1 parallel-lint /app
```

#### PHP Magic Number Detector (PHPMND) ####
[PHP Magic Number Detector (PHPMND)](https://github.com/povils/phpmnd) is a tool that aims to help you to detect [magic numbers](https://github.com/povils/phpmnd#what-is-a-magic-number) in your PHP code. By default 0 and 1 are not considered to be magic numbers.

```
docker run -v /path/to/project:/app umutphp/php-docker-images-for-ci:7.1 phpmnd /app
```

#### composer.json Fixer ####
[composer.json fixer](https://github.com/kubawerlos/composer-json-fixer) is a tool for fixing and cleaning up `composer.json` file according to its [schema](https://getcomposer.org/doc/04-schema.md) and best practices.

```
docker run -v /path/to/project:/app umutphp/php-docker-images-for-ci:7.1 composer-json-fixer --dry-run /app
```

#### PHP Assumptions ####
[PHP Assumptions](https://github.com/rskuipers/php-assumptions) is the result of a proof of concept inspired by the "From assumptions to assertions" blog post. It's a static code analysis tool doing checks for weak assumptions.

```
docker run -v /path/to/project:/app umutphp/php-docker-images-for-ci:7.1 phpa /app
```

#### churn-php ####
[churn-php](https://github.com/bmitch/churn-php) is a package that helps you identify php files in your project that could be good candidates for refactoring. It requires atleast PHP 7.1.

```
docker run -v /path/to/project:/app umutphp/php-docker-images-for-ci:7.1 churn run src /app
```

#### Fink ####
[Fink](https://github.com/dantleech/fink) (pronounced "Phpink") is a command line tool for checking HTTP links written in PHP. It requires atleast PHP 7.1.

```
docker run -v /path/to/project:/app umutphp/php-docker-images-for-ci:7.1 fink http://yoursite.domain
```

#### PHPMD ####
[PHPMD](https://github.com/phpmd/phpmd) is a spin-off project of PHP Depend and aims to be a PHP equivalent of the well known Java tool PMD. [PHPMD](https://github.com/phpmd/phpmd) can be seen as an user friendly frontend application for the raw metrics stream measured by PHP Depend.

```
docker run -v /path/to/project:/app umutphp/php-docker-images-for-ci:7.1 phpmd /app text codesize,unusedcode,naming
```

#### PHP_Testability ####
[PHP_Testability](https://github.com/edsonmedina/php_testability) analyses and produces a report with testability issues of a php codebase. It requires atleast PHP 7.0.

```
docker run -v /path/to/project:/app umutphp/php-docker-images-for-ci:7.1 testability /app -o report
```

#### composer-normalize ####
[composer-normalize](https://github.com/localheinz/composer-normalize) Provides a composer plugin for normalizing `composer.json`. It requires atleast PHP 7.1.

```
docker run -v /path/to/project:/app umutphp/php-docker-images-for-ci:7.1 cd /app && composer normalize
```

#### infection ####
[Infection](https://infection.github.io/) is a PHP mutation testing framework based on AST (Abstract Syntax Tree) mutations. It works as a CLI tool and can be executed from your project’s root. It requires atleast PHP 7.1.

```
docker run -v /path/to/project:/app umutphp/php-docker-images-for-ci:7.1 infection
```

## Custom Tools ##
- **Gitignore Checker:** `gitignore_checker` checks the .gitignore file under the directory that the command executed and finds if there are file or files both in the git ignore file and the repository.
- **Git Merge Conflict Marker Checker:** `merge_conflict_checker` checks all the files in the given folder (current folder is checked if not given) to find the forgotten merge conflict markers like "<<<<<<< HEAD". 

## How to use images locally ##
* A sample execution for [PHP Code Sniffer](https://github.com/squizlabs/PHP_CodeSniffer);

```
docker run -v /path/to/project:/app umutphp/php-docker-images-for-ci:7.1 phpcs /app
```

* A sample execution for [SensioLabs Security Checker](https://github.com/sensiolabs/security-checker);

```
docker run -v /path/to/project:/app umutphp/php-docker-images-for-ci:7.1 security-checker security:check /app/composer.lock
```

* A sample execution for [Psecio Parse](https://github.com/psecio/parse);

```
docker run -v /path/to/project:/app umutphp/php-docker-images-for-ci:7.1 /root/.composer/vendor/bin/psecio-parse scan /app
```

## How to Use in Gitlab CI ##
You need to enable Docker executors on Gitlab CI. You can find sample job definitions for executing the tools on Gitlab CI pipeline for your repo. 

A sample job definition for [PHP Code Sniffer](https://github.com/squizlabs/PHP_CodeSniffer);

```
code_sniffer:
    stage: stage_name
    image: umutphp/php-docker-images-for-ci:7.1
    script:
        - cd /path/to/code/base
        - phpcs 
```

A sample job definition for [SensioLabs Security Checker](https://github.com/sensiolabs/security-checker);

```
security_composer_checker:
    stage: stage_name
    image: umutphp/php-docker-images-for-ci:7.1
    script:
        - security-checker security:check /path/to/composer.lock
```

A sample job definition for [Psecio Parse](https://github.com/psecio/parse);

```
security_psecio_parse:
    stage: stage_name
    image: umutphp/php-docker-images-for-ci:7.1
    script:
        - psecio-parse scan /path/to/your/codebase/
```

## How to Use in CircleCI ##
You can make some static code checks before bulding and testing your application on CircleCI.

```
# PHP CircleCI 2.0 configuration file
#
version: 2
jobs:
  checks:
    docker:
      - image: umutphp/php-docker-images-for-ci:7.2
    steps:
      - checkout
      - run: 
          name: Composer-normalize
          no_output_timeout: 20m
          command: composer normalize --dry-run
      - run: 
          name: PHP-Lint
          no_output_timeout: 20m
          command: parallel-lint --exclude vendor .
      - run: 
          name: Var-Dump-Check
          no_output_timeout: 20m
          command: var-dump-check .
      - run: 
          name: Merge-Conflict-Checker
          no_output_timeout: 20m
          command: merge_conflict_checker .
workflows:
  version: 2
  build:
    jobs:
      - checks
```


## How To Contribute ##
Please read the instructions in [CONTRIBUTING.md](CONTRIBUTING.md) file.

## Code of Conduct ##
See [CODE_OF_CONDUCT](CODE_OF_CONDUCT) for information.
