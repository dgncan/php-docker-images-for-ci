# php-docker-images-for-ci
A repository with a set of Docker files created from official PHP images with some CI tools

## List of CI Tools ##
- [PHP Code Sniffer](https://github.com/squizlabs/PHP_CodeSniffer)
- [PHP Copy/Paste Detector (PHPCPD)](https://github.com/sebastianbergmann/phpcpd)
- [PHP Dead Code Detector](https://github.com/sebastianbergmann/phpdcd)
- [SensioLabs Security Checker](https://github.com/sensiolabs/security-checker)
- [PhpMetrics](https://www.phpmetrics.org/)
- [Psecio Parse](https://github.com/psecio/parse)
- [PHP VarDump Check](https://github.com/JakubOnderka/PHP-Var-Dump-Check)
- [PHP Parallel Lint](https://github.com/JakubOnderka/PHP-Parallel-Lint)
- [PHP Magic Number Detector (PHPMND)](https://github.com/povils/phpmnd)

## How to use ##
1. **Directly From Docker Hub:** You use the images already built from [umutphp/php-docker-images-for-ci](https://cloud.docker.com/repository/registry-1.docker.io/umutphp/php-docker-images-for-ci).
2. **Build Your Own:** Copy the Dockerfile and build your own image.

## Howto Use in Gitlab CI ##
You need to enable Docker executors on Gitlab CI. You can find sample job definitions for executing the tools on Gitlab CI pipeline for your repo. 

* A sample job definition for [PHP Code Sniffer](https://github.com/squizlabs/PHP_CodeSniffer);

```
code_sniffer:
    stage: stage_name
    image: umutphp/php-docker-images-for-ci:7.1
    script:
        - cd /path/to/code/base
        - phpcs 
```

* A sample job definition for [SensioLabs Security Checker](https://github.com/sensiolabs/security-checker);

```
security_composer_checker:
    stage: stage_name
    image: umutphp/php-docker-images-for-ci:7.1
    script:
        - security-checker security:check /path/to/composer.lock
```

* A sample job definition for [Psecio Parse](https://github.com/psecio/parse);

```
security_psecio_parse:
    stage: stage_name
    image: umutphp/php-docker-images-for-ci:7.1
    script:
        - /root/.composer/vendor/bin/psecio-parse scan /psth/to/your/codebase/
```