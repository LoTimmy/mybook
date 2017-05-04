
```console
shell> apt-get install php5-common libapache2-mod-php5 php5-cli
shell> apt-get install php7.0-common libapache2-mod-php7.0 php7.0-cli
shell> apt-get install php-common libapache2-mod-php php-cli

shell> apt-get install php5-mysql php5-curl
shell> apt-get install php7.0-mysql php7.0-curl
shell> apt-get install php-mysql php-curl

shell> /etc/init.d/apache2 stop
shell> /etc/init.d/apache2 start
```

#### :books: 參考網站：
- http://php.net/manual/en/install.unix.debian.php

---

```php
<?php
  $ip = file_get_contents('https://api.ipify.org');
  echo "My public IP address is: " . $ip;
?>
```

#### :books: 參考網站：
- [ipify](https://www.ipify.org/)

---

<img src="http://i.imgur.com/4JzyLLO.jpg" width="100">

- `CodeIgniter`是由`PHP`寫出的`Framework`

![](http://www.codeigniter.com/user_guide/_images/appflowchart.gif)

---

`application/controllers/Pages.php`

```php
<?php
class Pages extends CI_Controller {

  public function view($page = 'home')
  {
    if ( ! file_exists(APPPATH.'/views/pages/'.$page.'.php'))
    {
      // Whoops, we don't have a page for that!
      show_404();
    }

    $data['title'] = ucfirst($page); // Capitalize the first letter

    $this->load->view('templates/header', $data);
    $this->load->view('pages/'.$page, $data);
    $this->load->view('templates/footer', $data);
  }

}
```

`application/views/templates/header.php`

```php
<html>
  <head>
    <title>CodeIgniter Tutorial</title>
  </head>
  <body>

    <h1><?php echo $title; ?></h1>
```

`application/views/templates/footer.php`

```php
    <em>&copy; 2015</em>
  </body>
</html>
```

`application/views/pages/home.php`
`application/views/pages/about.php`

`application/config/routes.php`
```php
$route['default_controller'] = 'pages/view';
$route['(:any)'] = 'pages/view/$1';
```

`.htaccess`
```
RewriteEngine On
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^(.*)$ index.php/$1 [L]
```

---

```console
shell> apt-get install php-cli git zip
shell> curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin && \
       mv /usr/local/bin/composer.phar /usr/local/bin/composer

shell> composer update
```

```console
shell> composer require codeigniter/framework
shell> composer create-project codeigniter/framework your-project-name

shell> composer create-project laravel/laravel your-project-name 4.2.*

shell> composer remove codeigniter/framework 
```

```console
shell> composer require monolog/monolog
shell> composer require phpmailer/phpmailer
```

`composer.json`
```json
{
  "require": {
    "monolog/monolog": "^1.18"
  }
}
```

```php
<?php

require __DIR__ . '/vendor/autoload.php';

use Monolog\Logger;
use Monolog\Handler\StreamHandler;
use Monolog\Formatter\JsonFormatter;

$stream = new StreamHandler(__DIR__.'/my_app.log', Logger::DEBUG);

$stream->setFormatter($formatter);

// Create the logger
$logger = new Logger('my_logger');
$logger->pushHandler($stream);

// You can now use your logger
$logger->addInfo('My logger is now ready');

$logger->addInfo('Adding a new user', array('username' => 'Seldaek'));

```

```php
<?php

require __DIR__ . '/vendor/autoload.php';

use Monolog\Logger;
use Monolog\Handler\StreamHandler;
use Monolog\Formatter\JsonFormatter;

$stream = new StreamHandler(__DIR__.'/my_app.log', Logger::DEBUG);

$stream->setFormatter(new JsonFormatter());

// Create the logger
$logger = new Logger('my_logger');
$logger->pushHandler($stream);

// You can now use your logger
$logger->addDebug('My logger is now ready');
$logger->addInfo('My logger is now ready');


$logger->addNotice('My logger is now ready');
$logger->addWarning('My logger is now ready');
$logger->addError('My logger is now ready');
$logger->addCritical('My logger is now ready');
$logger->addAlert('My logger is now ready');
$logger->addEmergency('My logger is now ready');

$logger->addInfo('Adding a new user', array('username' => 'Seldaek'));
```

```console
shell> composer require geoip/geoip
shell> wget -N http://geolite.maxmind.com/download/geoip/database/GeoLiteCountry/GeoIP.dat.gz
shell> gunzip GeoIP.dat.gz
```

```php
<?php
require __DIR__ . '/vendor/autoload.php';

$gi = geoip_open("GeoIP.dat",GEOIP_STANDARD);

echo geoip_country_code_by_addr($gi, "24.24.24.24") . "\t" .
     geoip_country_name_by_addr($gi, "24.24.24.24") . "\n";
echo geoip_country_code_by_addr($gi, "61.231.58.233") . "\t" .
     geoip_country_name_by_addr($gi, "61.231.58.233") . "\n";

geoip_close($gi);
```

#### :books: 參考網站：
- [composer](https://getcomposer.org/doc/03-cli.md)
- [download](https://getcomposer.org/download/)
- [packagist](https://packagist.org/)
- [phpmailer](https://packagist.org/packages/phpmailer/phpmailer)
- [laravel](https://laravel.com/docs/4.2/quick)    
    
---

#### :books: 參考網站：
- [codeigniter](https://ellislab.com/codeigniter)
- [docs](http://www.codeigniter.com/docs)
- [user_guide](http://www.codeigniter.com/user_guide/)
- [urls](https://www.codeigniter.com/userguide3/general/urls.html)



---

```php
<?php

$array = array(
  "catalog" => "bar",
  "book" => array(
    array(
      'title' => 'Corets, Eva',
      'author' => 'Maeve Ascendant'
    ),
    array(
      'title' => 'Midnight Rain',
      'author' => 'Ralls, Kim'
    )
  )
);


$array = array(
    "foo" => "bar",
    42    => 24,
    "multi" => array(
         "dimensional" => array(
             "array" => "foo"
         )
    )
);

echo json_encode($array);
```

```
{
  "42": 24,
  "foo": "bar",
  "multi": {
    "dimensional": {
      "array": "foo"
    }
  }
}
```
