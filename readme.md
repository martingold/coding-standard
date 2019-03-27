# Coding style

## Installation
```
composer require \
    martingold/coding-standard \
    slevomat/coding-standard \
    consistence/coding-standard --dev
```
then run coding standard like:
```
php vendor/bin/phpcs --standard=vendor/martingold/coding-standard/src/coding-standard.xml --extensions=php --tab-width=4 -sp app
```
## Too long to remember?
This command seems to be too much hassle to type it every time. We can instead
leverage composer scripts to speed up the workflow. Add this piece of configuration
to your composer.json.
```json
"scripts": {
    "phpcs": "php vendor/bin/phpcs --standard=vendor/martingold/coding-standard/src/coding-standard.xml --extensions=php --tab-width=4 -sp src",
    "phpcbf": "php vendor/bin/phpcbf --standard=vendor/martingold/coding-standard/src/coding-standard.xml --extensions=php --tab-width=4 -sp src",
    "lint": "php vendor/bin/parallel-lint src",
    "phpstan": "php vendor/phpstan/phpstan/bin/phpstan analyse src -l 7 -c phpstan.neon",
    "style": [
      "@lint",
      "@phpcs",
      "@phpstan"
    ]
}
```
We can then type just `composer style` to check for PHP syntax errors and check if
code meets coding standard requirements. The syntax error checking is done with
[JakubOnderka/PHP-Parallel-Lint](https://github.com/JakubOnderka/PHP-Parallel-Lint)
which you must install when you want to use this exact example. It is highly advised
to run [PHPStan](https://github.com/phpstan/phpstan) analysis to check for unexpected
behaviour. It is very handy tool to catch low-hanging-fruit bugs in your code.

## Example of code using this coding-standard
Example of code can be found in `src/Person.php`.