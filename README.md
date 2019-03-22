# WordPress with Composer

This is a fork of Wordpress for use with Edje framework.

## Installation

1. Create a new empty directory.
1. Inside, create a new file named `composer.json`. It contains the list of plugins you want to use in your Wordpress site. You can find the recommended setup below.
1. Open cmd / terminal in that directory and run the command `composer update`. It will take few minutes to finish downloading.
1. 

Recommended setting:

```json
{
  "name": "your-name/new-site",
  "description": "Run the command `composer update` to download WordPress and specified plugins",
  "repositories":[
    { "type":"composer", "url":"https://wpackagist.org" }
  ],
  "authors": [
    {
      "name": "Your Name",
      "email": "your-email@example.com",
      "homepage": "https://your-site.com"
    }
  ],
  "require": {
    "pixelstudio/wordpress": "~5.1",
    "pixelstudio/edje-wp-library": "~2.0",
    "pixelstudio/edje-wp-theme": "~1.0",
    "pixelstudio/wp-sync-db": "~1.6",
    "pixelstudio/wp-sync-media": "~1.1",
    "wpackagist-plugin/jetpack": "~7.1",
    "wpackagist-plugin/timber-library": "~1.8",
    "wpackagist-plugin/autodescription": "~3.2",
    "wpackagist-plugin/contact-form-7": "~5.1.",
    "wpackagist-theme/twentynineteen": "~1.3",
    
    "wpackagist-plugin/woocommerce": "~3.5",
    "pixelstudio/edje-wc-library": "~2.0",
    "wpackagist-theme/storefront": "~2.4"
  },
  "require-dev": {},
  "extra": {
	  "wordpress-install-dir": "cut-all-inside-to-root"
  },
  "autoload": { "psr-0": { "Acme": "src/" } }
}
```

If you want a WooCommerce site, add this in `require`:

```json
"wpackagist-plugin/woocommerce": "~3.5",
"pixelstudio/edje-wc-library": "~2.0",
"wpackagist-theme/storefront": "~2.4"
```

## Changes to Core

- Removed `/wp-content` directory so it won't override existing one.
- Changed some constants in `wp-config-sample.php`. DISALLOW_FILE_EDIT to true and WP_POST_REVISIONS to 5.
- Added `wp-config-sample-dev.php` for use in localhost environment. You need to rename it to `wp-config-sample.php`, removing the existing one first.
- Removed `readme.html`.
- Removed `license.txt`.