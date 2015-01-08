# CakePHP Oracle Datasource

Connect to an Oracle database using the OCI* PHP extension.

## Requirements

The master branch has the following requirements:

* CakePHP 2.2.0 or greater.
* PHP 5.4.0 or greater.

## Installation

_[Using [Composer](http://getcomposer.org/)]_

Add the plugin to your project's `composer.json`:

```javascript
{
  "require": {
    "asaladino/oracle_datasource": "0.8.*"
  }
}
```

Because this plugin has the type `cakephp-plugin` set in it's own `composer.json`, composer knows to install it inside your `/Plugin` directory, rather than in the usual vendors file.
It is recommended that you add `/Plugin/OracleDatasource` to your .gitignore file. (Why? [read this](http://getcomposer.org/doc/faqs/should-i-commit-the-dependencies-in-my-vendor-directory.md).)

_[Manual]_

* Download the [OracleDatasource archive](https://github.com/asaladino/cakephp_oracle_datasource/zipball/master).
* Unzip that download.
* Rename the resulting folder to `OracleDatasource`
* Then copy this folder into `app/Plugin/`

_[Enable]_

Add `CakePlugin::loadAll();` to `bootstrap.php` then implement in database.php and a model.

```php
class DATABASE_CONFIG {
    public $oracle = array(
        'datasource' => 'OracleDatasource.Oci',
        'persistent' => false,
        'host' => '127.0.0.1',
        'port' => '1521',
        'login' => 'user',
        'password' => 'oracle',
        'schema' => 'USER_SCHEMA',
        'sid' => 'orcl', // or service name
        'prefix' => ''
    );
}
```

```php
App::uses('AppModel', 'Model');

class DemoState extends AppModel {
    public $primaryKey = 'st';
    public $displayField = 'state_name';
    public $useDbConfig = 'oracle';
}
```