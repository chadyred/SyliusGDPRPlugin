[![License](https://badgen.net/github/license/synolia/SyliusGDPRPlugin)](https://github.com/synolia/SyliusGDPRPlugin/blob/master/LICENSE)
[![CI](https://github.com/synolia/SyliusGDPRPlugin/actions/workflows/ci.yaml/badge.svg?branch=master)](https://github.com/synolia/SyliusGDPRPlugin/actions/workflows/ci.yaml)
[![Version](https://badgen.net/github/tag/synolia/SyliusGDPRPlugin?label=Version)](https://packagist.org/packages/synolia/sylius-gdpr-plugin)
[![Total Downloads](https://poser.pugx.org/synolia/sylius-gdpr-plugin/downloads)](https://packagist.org/packages/synolia/sylius-gdpr-plugin)

<p align="center">
    <a href="https://sylius.com" target="_blank">
        <img src="https://demo.sylius.com/assets/shop/img/logo.png" />
    </a>
</p>
<h1 align="center">Sylius GDPR Plugin</h1>

![Capture](/etc/capture.png "Capture")

## Features

   - Anonymize customer with the GDPR section in the admin customer show.
   - Export customer data with the GDPR section in the admin customer show.

   [Click to see the anonymization configuration](ANONYMIZE_CONFIGURATION.md).
   
   [Click to see the export data configuration](EXPORT_CONFIGURATION.md).

   - Anonymize any entity with command for example :

   ```shell
   php bin/console synolia:gdpr:anonymize --entity='Sylius\Component\Core\Model\Customer' --id=1 
   ```
   Use --help to get more informations

### Events

   - Synolia\SyliusGDPRPlugin\Event\BeforeAnonymize
   - Synolia\SyliusGDPRPlugin\Event\AfterAnonymize
   - Synolia\SyliusGDPRPlugin\Event\AfterCustomerAnonymize
   - Synolia\SyliusGDPRPlugin\Event\BeforeExportCustomerData

## Requirements

| | Version |
| :--- | :--- |
| PHP  | 7.3, 7.4, 8.0 |
| Sylius | 1.9, 1.10 |

## Installation

1. Add the bundle and dependencies in your composer.json :

    ```shell
    composer require synolia/sylius-gdpr-plugin --no-scripts
    ```

2. Enable the plugin in your `config/bundles.php` file by add

    ```php
    Synolia\SyliusGDPRPlugin\SynoliaSyliusGDPRPlugin::class => ['all' => true],
    ```

3. Import required config in your `config/packages/_sylius.yaml` file:

    ```yaml
    imports:
        - { resource: "@SynoliaSyliusGDPRPlugin/Resources/config/app/config.yaml" }
    ```

4. Import routing in your `config/routes.yaml` file:

    ```yaml
    synolia_gdpr:
        resource: "@SynoliaSyliusGDPRPlugin/Resources/config/routes/admin/customer.yaml"
        prefix: '/%sylius_admin.path_name%'
    ```

5. Clear cache

    ```shell
    php bin/console cache:clear
    ```

## Development

See [How to contribute](CONTRIBUTING.md).

## License

This library is under the [EUPL-1.2 license](LICENSE).

## Credits

Developed by [Synolia](https://synolia.com/).
