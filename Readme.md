# laravel code formator

## Format PHP Files.
1. Install PHP-CS-Fixer: PHP-CS-Fixer is a tool that automatically fixes PHP code to follow the PSR-12 standard. You can install it using Composer:

```
composer require --dev friendsofphp/php-cs-fixer
```

2. Create a configuration file: Create a .php-cs-fixer.dist.php file in the root directory of your Laravel project. This file will contain the configuration for PHP-CS-Fixer. Here's an example configuration:

```
<?php

$finder = PhpCsFixer\Finder::create()
    ->in([
        __DIR__ . '/app',
        __DIR__ . '/config',
        __DIR__ . '/database',
        __DIR__ . '/resources',
        __DIR__ . '/routes',
        __DIR__ . '/tests',
    ])
    ->name('*.php')
    ->notName('*.blade.php')
    ->ignoreDotFiles(true)
    ->ignoreVCS(true);

$config = new PhpCsFixer\Config();
return $config->setRules([
        '@PSR12' => true,
        'array_syntax' => ['syntax' => 'short'],
        'ordered_imports' => ['sort_algorithm' => 'alpha'],
        'no_unused_imports' => true,
        'not_operator_with_successor_space' => true,
        'trailing_comma_in_multiline' => true,
        'phpdoc_scalar' => true,
        'unary_operator_spaces' => true,
        'binary_operator_spaces' => true,
        'blank_line_before_statement' => [
            'statements' => ['break', 'continue', 'declare', 'return', 'throw', 'try'],
        ],
    ])
    ->setFinder($finder);
```

3. Add a script to your package.json: In your project's package.json file, add a script to run the PHP-CS-Fixer:
```
{
  "scripts": {
    "format": "php vendor/bin/php-cs-fixer fix"
  }
}
```

4. Run the formatting command: Now, you can run the formatting command using the following command:
```
npm run format
```
This will automatically format your PHP code to follow the PSR-12 standard.


## Format Blade Files.

1. Install the package: In your Laravel project's root directory, run the following command to install the shufo/blade-formatter package using npm:
```
npm install @shufo/blade-formatter --save-dev
```

2. Create a configuration file: Create a .blade-formatter.yml file in the root directory of your Laravel project. This file will contain the configuration for the Blade formatter. Here's an example configuration:

```
# .blade-formatter.yml
indent_size: 4
indent_style: space
max_line_length: 120
```

3. Add a script to your package.json: In your project's package.json file, add a script to run the Blade formatter:

```
{
  "scripts": {
    "format:blade": "blade-formatter \"resources/views/**/*.blade.php\" --write"
  }
}
```
You can also add multiple arguments to the script, like this:
```
{
  "scripts": {
    "format:blade": "blade-formatter \"resources/views/**/*.blade.php\" --write --sort-tailwindcss-classes"
  }
}
```
This will format the Blade files, write the changes back to the files, and sort the Tailwind CSS classes.

4. Run the formatting command: Now, you can run the formatting command for Blade files using the following command:
```
npm run format:blade
```
This will automatically format your Blade files according to the configuration in the .blade-formatter.yml file.
