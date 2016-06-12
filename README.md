# OPENSHIFT Nginx PHP 7 Cartridge
<img src="https://raw.githubusercontent.com/budisteikul/openshift-cartridge-nginx-php7/master/usr/openshift-redhat.jpg"><br />Welcome to the world of [PHP-FPM](http://php.net/manual/en/book.fpm.php) within [OPENSHIFT](https://www.openshift.com/) by [REDHAT](https://www.redhat.com/en).

## What's inside

* Nginx: 1.11.1
* PHP: 7.1.0alpha1
* Latest Composer

## Installation
### Web Console
Click [here](https://openshift.redhat.com/app/console/application_type/custom?unlock=true&application_type%5Bcartridges%5D=http%3A%2F%2Fcartreflect-claytondev.rhcloud.com%2Fgithub%2Fbudisteikul%2Fopenshift-cartridge-nginx-php7) for installation via web console. <br />
Alternatively, you can use this [cartridge definition](http://cartreflect-claytondev.rhcloud.com/github/budisteikul/openshift-cartridge-nginx-php7) on application creation page.

### Command Line
```
rhc app create appname http://cartreflect-claytondev.rhcloud.com/github/budisteikul/openshift-cartridge-nginx-php7
```
## Updates
You can update the binaries from the cartridge without reinstalling. To check for updates, SSH to your app and run this command:

```
update
```
Make sure to have your backup just in case some things went wrong.

## Configuration

### Nginx
Nginx will automatically include `.openshift/nginx.conf.erb` file.

### PHP-FPM
PHP-FPM will automatically load `.openshift/php-fpm.ini.erb`, `.openshift/php-fpm.conf.erb`, and `.openshift/extension.ini.erb` files.

## Website
The web root directory is `public/`. Make changes to your website there, then commit and push.

## PECL
To install/uninstall pecl extension just run ssh to your application and run `php-pecl install <name> <ver>`
<br />
Example :
```
php-pecl install apcu 5.1.5
php-pecl install mongodb 1.1.7
php-pecl uninstall apcu
php-pecl uninstall mongodb
```

## Scripts
This cartridge comes with different scripts for easy management of your app inside SSH.

* `version` - Get the version of the cartridge binaries.
* `service` - A psuedo `/usr/bin/service` to start and stop services. Example:
    * `service php-fpm start`
	* `service php-fpm stop`
	* `service php-fpm restart`
	* `service nginx start`
    * `service nginx stop`
	* `service nginx restart`
* `update` - Allows automatic update of the cartridge binaries.
    * `update check` - Check for updates
    * `update install` - Install updates
* `php-pecl` - To install/uninstall pecl extension.
    * `php-pecl install <name> <ver>` - Install pecl extension
    * `php-pecl uninstall <name>` - Uninstall pecl extension
