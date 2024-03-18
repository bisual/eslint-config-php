# Bisual eslint PHP

## Installation

1.Install dependency

Run the following command in the terminal to install the necessary dependencies:

```bash
  composer require bisual/eslint-config-php --dev
```

2.Linter Configuration

Create a file named `.php-cs-fixer.php` in the root of the project and add the following content:

```php
<?php

namespace Bisual\LintConfigPhp;

use Bisual\LintConfigPhp\CodingStyle;

return CodingStyle::getConfig();
```

In the `CodingStyle::getConfig()` function, you can provide parameters to configure the formatter. It is passed as a parameter an array with the following options:

- $disabled_rules (array): Rules to be disabled.
- $routes (array): Routes of the files to be formatted.
- $exclude_files (array): Files to be excluded from formatting.

3.Install a Formatter Extension

Install the [junstyle.php-cs-fixer]('https://marketplace.visualstudio.com/items?itemName=junstyle.php-cs-fixer') extension in Visual Studio Code.

> [!TIP]
> To facilitate the installation of the formatter extension in Visual Studio Code for new contributors, you can create an `extensions.json` file in the `.vscode` folder with the following content:
```json
{
  "recommendations": ["junstyle.php-cs-fixer"]
}
```

4.Automatic Formatting Configuration

To enable automatic code formatting on save, follow these steps:

- Create a folder named .vscode in the root of the project.
- Inside the .vscode folder, create a file named settings.json.
- Add the following content to the settings.json file:

```json
{
  "[php]": {
    "editor.formatOnSave": true,
    "editor.defaultFormatter": "junstyle.php-cs-fixer"
  },
  "php-cs-fixer.onsave": true,
  "php-cs-fixer.formatHtml": true,
  "php-cs-fixer.executablePath": "${workspaceFolder}/vendor/bin/php-cs-fixer",
  "php-cs-fixer.config": ".php-cs-fixer.php"
}

```

After making these changes, you may need to restart Visual Studio Code for them to take effect.
