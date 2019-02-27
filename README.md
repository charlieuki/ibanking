IBanking - Internet Banking
=====

Internet Banking client wrapper, useful to check internet banking statements (cek mutasi online) using PHP script.

## Documentation
The documentation is currently under construction.

You can read here:

## Installation

### Composer
Add _ibanking_ library in to your composer.json or create a new composer.json file:

```js
{
    "require": {
        "charlieuki/ibanking": "dev-master"
    }
}
```

Then, tell composer to download the library by running the command:

``` bash
$ php composer.phar install
```

Composer will generate the autoloader file automatically. So you only have to include this.
Typically its located in the _vendor_ directory and its called _autoload.php_

```php
<?php
include('vendor/autoload.php');
```

## Basic Usage
This library is using the PSR-4 standard: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4.md.
So you can use any autoloader which fits into this standard.
The tests directory contains an example bootstrap file.

```php
<?php
use IBanking\IBanking as IBanking;
use IBanking\IBParser\SampleBankParser as SBParser;

$credentials = [
	'corpid'	=> '',
	'username'	=> 'namauser',
	'password'	=> 'katasandi',
	'account'	=> 'nomor_rekening',
];

$ibanking = new IBanking(new SBParser, $credentials);

$loggedin = $ibanking->login();

var_dump($loggedin);
echo("\r\n");

$balance = $ibanking->getBalance();
var_dump($balance);
echo("\r\n");

$mutasi = $ibanking->getStatements('24/7/2017', '29/7/2017', 'credit');
var_dump($mutasi);
echo("\r\n");

var_dump($ibanking->isLoggedin($session=true));

$ibanking->logout();
```

For some very simple examples go to the _samples_ directory and have a look at the sample files.

## Contribution
Please send your PR on the Github repository to help improve this script.

(c) 2019
