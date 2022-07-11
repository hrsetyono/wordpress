# WordPress Boilerplate

This is the starter kit used by [PixelStudio.id](https://pixelstudio.id) to create WordPress project. It contains **Edje**, a developer-friendly theme.

## Localhost Workflow

1. Create a WP localhost site using [LOCAL](https://localwp.com/).
1. Create a new Github repo and set `/app/public` as that Git directory.
1. Copy **composer.json** and **.gitignore** to the `/app/public` directory.
1. Open site shell in LOCAL and run:  

    `composer update`

1. Rename `/wp-content/themes/edje-wp-theme` so your changes won't get overriden. After that, remove `edje-wp-theme` from **package.json**.
1. Go to WP Admin then activate "Edje WP Library" and "Advanced Custom Fields" plugin. Those two are a must use.
1. Done! Start developing your project.

## Publishing Workflow

1. Create an empty WordPress site in your live server.
1. Put all the plugins.  

    - If your server supports SSH, put **composer.json** into the WP directory (where wp-config.php lies) and run `composer update`. Install Composer if you haven't yet.
    - If doesn't support SSH, simply use FTP to upload all the plugins.

1. Setup Github Action to automatically deploy the theme whenever you pushed a commit. [Read more »](https://wptips.dev/wordpress-workflow/).
1. Activate "WP Sync DB" plugin in both localhost and live server to sync database between them. [Read more »](https://wptips.dev/wp-sync-db/).  

    - **Note**: The "sync media" feature often fails if internet connection is bad. In that case, simply use FTP to upload the media.

1. Setup automatic backup with "Updraft Plus" plugin to Google Drive. A weekly schedule should suffice.

## LOCAL Config

LOCAL uses WP-CLI to generate WordPress files. That means we can create a global config to define constants. Here's how:

1. Go to `C:/Users/yourname` (windows) or `/usr` (MAC).
1. Create a new folder named `/.wp-cli`.
1. Create a new file inside that folder named `config.yml`
1. Open that file with any text editor and put this code:

```yml
config create:
  extra-php: |
    define('WP_DEBUG', true);
    define('JETPACK_DEV_DEBUG', true);
    define('WP_POST_REVISIONS', 10);
    define('DISALLOW_FILE_EDIT', true);

core download:
  skip-content: 1
```