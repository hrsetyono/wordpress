# WordPress with Composer + WP CLI

Learn how to download and install WordPress with 1 simple command.

This repo contains 3 files:

- `composer.json` and `wp-cli.local.yml` are the local configs. Put this in the root folder of your project.

- `config.yml` is the global config. You will learn where to place it in the guide below.

## For Localhost

We assume you are on Windows 10 machine and already have PHP localhost like [WAMP 32-bit](https://github.com/hrsetyono/wordpress/wiki/Installing-WAMP-on-Windows-10).

If you're on Mac, the difference is only on One-time Setup. For the localhost, I heard [MAMP](https://www.mamp.info/en/) is good.

### One-time Setup

1. Install [Git](https://git-scm.com/downloads), [Composer 1.8](https://getcomposer.org/download/), and [WP-CLI 2.2](https://github.com/hrsetyono/wordpress/wiki/Installing-WP-CLI-on-Windows-10).
1. Set global config by putting `config.yml` inside `C:\Users\yourname\.wp-cli`.

     You also need to edit it to fit your localhost environment.

### Project Setup:

1. Create a new folder and a VirtualHost for your project.

   > [How to create VirtualHost with WAMP »](https://github.com/hrsetyono/wordpress/wiki/Installing-WAMP-on-Windows-10#4-creating-virtual-host)

1. Put `composer.json` and `wp-cli.local.yml` inside.

1. Open `composer.json` and modify it to fit your project. The important parts are:

    - `require` - The list of plugins and themes.
    - `scripts` - The shortcut to run series of command. You need to edit the parameter of `local-init`.

1. Run the command `composer local-init` to download and install WordPress.

1. Done!

## For Live Server

First thing first: your server needs to support **SSH Access**.

Good? Let's see how to set it up:

### One-time Setup:

1. Install Composer and WP-CLI on your server.

    > Ask your customer service on how to do it.

1. Upload `config.yml` to `.wp-cli/` folder of your server. Edit it to fit your environment.

### Project Setup:

1. Open `wp-cli.local.yml` and change the `@live` SSH address to yours.

    - This allows you to remotely run WP-CLI command by adding the alias like this: `wp @live --info`.

    - The `path` starts from where you land when connecting via SSH.

    - **NOTE**: In Windows, you need to use Git Bash for remote-command. Which should be installed together with Git.

1. Open `composer.json` and edit the `live-init` part. Then, upload it to your project directory.

1. Run the command `wp @live ${ composer live-init } -` to download and install WordPress in your server.

1. Done!