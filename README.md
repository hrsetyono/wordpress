# WordPress with Composer + WP CLI

We will explain how to download and install WordPress with 1 simple command.

```
composer init-wp
```

## One-time Setup

We assume you are on Windows 10 machine and already running any PHP localhost like [WAMP 32-bit](http://www.wampserver.com/en/) or XAMPP.

1. Install [Git](https://git-scm.com/downloads).
1. Install [Composer 1.8](https://getcomposer.org/download/).
1. Install [WP-CLI 2.2](https://github.com/hrsetyono/wordpress/wiki/Installing-WP-CLI-on-Windows-10).
1. Go to `C:\Users\yourname\.wp-cli` and put `config.yml` there.
1. Edit the value in `config.yml` to fit your environment.

## Project Setup

1. Create a new directory for your project and put `composer.json` and `wp-cli.yml` inside.

1. Edit the value in `wp-cli.yml` to fit your project.

1. Run the command `composer init-wp`.

## Live Server Setup (Optional)

This allows you to install and migrate WordPress to your live server.

**Coming Soon**