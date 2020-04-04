# WordPress with Composer + WP CLI

Learn how to download and install WordPress with 1 command.

How to:

1. [Install These Softwares](#1-install-these-softwares) (First time only)
1. [Create Global Config](#2-create-global-config) (First time only)
1. [Initiate Your Project](#3-initiate-your-project)


## 1. Install These Softwares

1. PHP Server like [WAMP 32-bit](https://github.com/hrsetyono/wordpress/wiki/Installing-WAMP-on-Windows-10) (Windows) or [MAMP](https://www.mamp.info/en/) (MAC).

1. [Git](https://git-scm.com/downloads).

1. [Composer 1.8](https://getcomposer.org/download/)

1. [WP-CLI 2.2](https://github.com/hrsetyono/wordpress/wiki/Installing-WP-CLI-on-Windows-10)


## 2. Create Global Config

(For Windows) Run these commands:

```sh
cd %HOMEPATH%

# Create a folder and enter it
mkdir .wp-cli
cd .wp-cli

# Create and open the file
copy NUL config.yml
config.yml
```

(For MAC) I don't know the commands, but simply create `/.wp-cli/config.yml` in `/usr` folder.

```
```

It will open **config.yml** in your text editor.

Put in these codes and edit the value to fit your environment:

```yml
# Database and wp-config.php settings
config create:
  dbuser: root
  dbpass: my-db-password
  extra-php: |
    define( 'WP_DEBUG', true );
    define( 'WP_POST_REVISIONS', 10 );
    define( 'EDJE', true );
    define( 'DISALLOW_FILE_EDIT', true );
    define( 'JETPACK_DEV_DEBUG', true );

# WP-Admin credentials
core install:
  admin_user: my-wp-username
  admin_password: my-wp-password
  admin_email: my-wp-email@gmail.com

core multisite-install:
  admin_user: my-wp-username
  admin_password: my-wp-password
  admin_email: my-wp-email@gmail.com


# Skip the default theme and plugins when downloading wordpress
core download:
  skip-content: 1

# Ignore this
disabled_commands:
  - db drop
  - db reset
```

## 3. Initiate Your Project

1. Create a new folder and a VirtualHost for your project.

   > [How to create VirtualHost with WAMP »](https://github.com/hrsetyono/wordpress/wiki/Installing-WAMP-on-Windows-10#4-creating-virtual-host)

1. Download this repo and put it in the new folder.

1. Open `composer.json` and modify it to fit your project. The important parts are:

    - `require` - The list of plugins and themes.
    - `scripts` - The shortcut to run series of command. You need to edit the parameter of `local-init`.

1. Run the command `composer local-init` to download and install WordPress.

1. Done!

-----

# Live Server Installation

First thing first: your server needs to support **SSH Access**.

Good? Let's see how to set it up:

1. Install Composer and WP-CLI on your server.

    > Ask your customer service on how to do it.

1. Create global config `.wp-cli/config.yml`. Location vary between hosting.

## Project Setup:

1. Open `wp-cli.local.yml` and change the `@live` SSH address to yours.

    - This allows you to remotely run WP-CLI command by adding the alias like this: `wp @live --info`.

    - The `path` starts from where you land when connecting via SSH.

    - **NOTE**: In Windows, you need to use Git Bash for remote-command. Which should be installed together with Git.

1. Open `composer.json` and edit the `live-init` part. Then, upload it via FTP to your project folder.

1. Run the command `wp @live ${ composer live-init } -` to download and install WordPress in your server.

1. Done!