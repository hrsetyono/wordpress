# WordPress w/ Composer

Do you know you can install WordPress and its plugins using command-line?

This fork of WordPress is slightly customized so it works with Composer and our own library: **Edje**.

**REQUIREMENTS**

- PHP ~7.0
- Composer ~1.8

## Composer.json

Below is the Composer setup we typically use for our projects:

It includes our [Starter theme](https://github.com/hrsetyono/edje-wp-theme) and [Custom-made Library](https://github.com/hrsetyono/edje-wp-library) that is made to work with [Timber](https://timber.github.io/docs/).

```json
{
  "name": "your-name/new-site",
  "description": "Run the command `composer update` to download WordPress and specified plugins",
  "repositories":[
    { "type":"composer", "url":"https://wpackagist.org" }
  ],
  "authors": [
    { "name": "Your Name", "email": "your-email@example.com", "homepage": "https://your-site.com" }
  ],
  "require": {
    "pixelstudio/wordpress": "~5.1",
    "pixelstudio/edje-wp-library": "~2.0.0",
    "pixelstudio/wp-sync-db": "~1.6",
    "pixelstudio/wp-sync-media": "~1.1",
    "wpackagist-plugin/jetpack": "*",
    "wpackagist-plugin/timber-library": "~1.9.0",
    "wpackagist-plugin/autodescription": "*",
    "wpackagist-plugin/contact-form-7": "*",
    
    "pixelstudio/edje-wp-theme": "~1.0",
    "wpackagist-theme/twentynineteen": "*"
  },
  "require-dev": {},
  "autoload": { "psr-0": { "Acme": "src/" } }
}
```

## Installation

1. Create a new empty directory and put the **composer.json** file in it.
1. Run the command `composer update` inside the directory - It will take few minutes to finish downloading.

**Project Setup**

1. Enter `/wp-core ...` and move all the files to root except the JSON file.
1. Enter `/wp-content/themes` and rename `edje-wp-theme` to your project name.
1. Remove
1. Done!

Our recommended `composer.json`:



If you want a WooCommerce site, add these packages:

```json
"wpackagist-plugin/woocommerce": "~3.5",
"pixelstudio/edje-wc-library": "~2.0",
"wpackagist-theme/storefront": "*"
```

## Changes to Core

- Removed `/wp-content` directory so it won't override existing one.
- Changed some constants in `wp-config-sample.php`. DISALLOW_FILE_EDIT to true and WP_POST_REVISIONS to 5.
- Added `wp-config-sample-dev.php` for use in localhost environment. You need to rename it to `wp-config-sample.php`, removing the existing one first.
- Removed `readme.html`.
- Removed `license.txt`.