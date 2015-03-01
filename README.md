# CakePHP 3 Facebook Plugin

A CakePHP 3.x Plugin to allow Facebook Login into an application.

THIS DOCUMENT IS IN DEVELOPMENT

## Requirements
- CakePHP 3.x with Auth component enabled
- PHP 5.4.6
- Facebook PHP SDK 4.0
- User Table with at least the following columns
    * `facebook_id varchar(20)`
    * `first_name`
    * `last_name`
    * `username`
    * `password`

Except `facebook_id` and `password`, work is underway to make the other fields not required and dynamic

NOTE: Facebook PHP SDK is a requirement. Composer will automatically install Facebook for you if not already installed. If manual download is chosen, you must download the Facebook Source into `vendor/facebook/php-sdk-v4`

## Included
- Facebook Graph Component
- Facebook Graph Helper

## Installation

#### Git Clone (plugins/AkkaFacebook)
`git clone git@github.com:akkaweb/AKKA-CakePHP-Facebook-Plugin.git`

#### Download
`https://github.com/akkaweb/AKKA-CakePHP-Facebook-Plugin/archive/master.zip`

#### Composer (Composer should be the preferred choice as it can automatically update this plugin)

1. Add the following to your `composer.json` in the `require` section

```php
"require": {
	"akkaweb/cakephp-facebook": "dev-master"
}
```

2. Run the following at the root of your application

```
sudo php composer.phar update
```



## Configuration

1. Load the plugin in your application's `bootstrap.php` file:

```php
Plugin::load('AkkaFacebook', ['bootstrap' => false, 'routes' => true]);
```

2. Load the plugin's component in `AppController.php` 
```php
public function initialize(){
    parent::initialize();
    
    $this->loadComponent('AkkaFacebook.Graph', [
	'app_id' => 'your-fb-app-id',
	'app_secret' => 'your-fb-app-secret',
	'app_scope' => '', //ie. email
	'redirect_url' => '', //ie. Router::url(['controller' => 'Users', 'action' => 'login'], TRUE),
	'post_login_redirect' => '' //ie. Router::url(['controller' => 'Users', 'action' => 'account'], TRUE)
    ]);
}
```

## Usage

Note: GraphHelper is automatically loaded by the composer. If that is not desired, add `'enable_graph_helper' => false,` to `$this->loadComponent()` above.

#### Helper Template File Setup

- Add `<?php echo $this->Facebook->initJsSDK(); ?>` immediately after the opening `<body>` tag

#### Login Button

`<?php echo $this->Facebook->loginLink(); ?>`



DOCUMENTANTION IN DEVELOPMENT. MORE COMING SOON...


## Disclaimer
Use at your own risk. Please provide any fixes or enhancements via issue or pull request.
