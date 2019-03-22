# WordPress with Composer

This is a fork of Wordpress for use with Edje framework.

**REQUIREMENTS**

- PHP ~7.0
- Composer ~1.8

## Installation

1. Create a new empty directory.
1. Inside, create a new file `composer.json` - It contains the list of plugins you want to use in your Wordpress site. You can find the recommended setup below.
1. Run the command `composer update` inside the directory - It will take few minutes to finish downloading.
1. Cut all the files inside the newly generated `/wp-core` directory to root - Except the JSON file.
1. Done!

Recommended setting in `composer.json`:

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