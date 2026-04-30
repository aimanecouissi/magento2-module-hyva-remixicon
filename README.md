# AimaneCouissi_HyvaRemixicon

[![Latest Stable Version](http://poser.pugx.org/aimanecouissi/module-hyva-remixicon/v)](https://packagist.org/packages/aimanecouissi/module-hyva-remixicon) [![Total Downloads](http://poser.pugx.org/aimanecouissi/module-hyva-remixicon/downloads)](https://packagist.org/packages/aimanecouissi/module-hyva-remixicon) [![Magento Version](https://img.shields.io/badge/magento-2.4.x-E68718)](https://packagist.org/packages/aimanecouissi/module-hyva-remixicon) [![License](http://poser.pugx.org/aimanecouissi/module-hyva-remixicon/license)](https://packagist.org/packages/aimanecouissi/module-hyva-remixicon) [![PHP Version Require](http://poser.pugx.org/aimanecouissi/module-hyva-remixicon/require/php)](https://packagist.org/packages/aimanecouissi/module-hyva-remixicon) [![Hyvä Compatible](https://img.shields.io/badge/hyv%C3%A4-compatible-99004D)](https://packagist.org/packages/aimanecouissi/module-hyva-remixicon)

Integrates the **[Remixicon](https://remixicon.com/)** SVG icon set into **Hyvä Themes**, exposing `line` and `fill`
styles as dedicated `SvgIcons` view models. Browse the included icons
in [the SVG directory](https://github.com/aimanecouissi/magento2-module-hyva-remixicon/tree/main/view/frontend/web/svg)
or preview them at [remixicon.com](https://remixicon.com/).

## Installation

```bash
composer require aimanecouissi/module-hyva-remixicon
bin/magento module:enable AimaneCouissi_HyvaSvgIcons AimaneCouissi_HyvaRemixicon
bin/magento setup:upgrade
bin/magento cache:flush
```

## Usage

### In Hyvä PHTML templates

Require the view models for the styles you need and call their helper methods to render icons:

```php
<?php

use AimaneCouissi\HyvaRemixicon\ViewModel\RemixiconFill;
use AimaneCouissi\HyvaRemixicon\ViewModel\RemixiconLine;
use Hyva\Theme\Model\ViewModelRegistry;

/** @var ViewModelRegistry $viewModels */

$remixiconLine = $viewModels->require(RemixiconLine::class);
$remixiconFill = $viewModels->require(RemixiconFill::class);
?>
```

```php
<?= $remixiconLine->shoppingCartHtml('w-6 h-6', 24, 24, ['aria-label' => 'Cart']) ?>
<?= $remixiconFill->starHtml('w-5 h-5 text-yellow-400', 20, 20, ['aria-hidden' => 'true']) ?>
```

Methods are generated from SVG filenames and fully documented via PHPDoc on each view model, so your IDE can
autocomplete them. Icons whose names start with a digit are prefixed with an underscore (e.g. `_24HoursHtml`,
`_4kHtml`).

### In CMS content

The module registers two icon prefixes for Hyvä `SvgIcons`: `remixicon-line` and `remixicon-fill`. Icons can be used
directly in CMS pages, blocks, and widgets:

```txt
{{icon "remixicon-line/shopping-cart" classes="inline-block w-6 h-6" width=24 height=24}}
{{icon "remixicon-fill/star" classes="inline-block w-5 h-5 text-yellow-400" width=20 height=20}}
```

## Uninstall

```bash
bin/magento module:disable AimaneCouissi_HyvaRemixicon
composer remove aimanecouissi/module-hyva-remixicon
bin/magento setup:upgrade
bin/magento cache:flush
```

## Changelog

See [CHANGELOG](CHANGELOG.md) for all recent changes, including icon set version updates.

## License

The Remixicon SVG icons are created by [Remix Design](https://github.com/Remix-Design/RemixIcon) and licensed
under [Remix Icon License v1.0](https://github.com/Remix-Design/RemixIcon/blob/master/License).

> [!WARNING]
> Individual brand icons may be subject to their own trademark and usage guidelines. Trademark usage is the
> responsibility of the end user. Please consult individual brand guidelines before displaying logos in commercial
> contexts.

This module's source code is separately licensed under [MIT](LICENSE).
