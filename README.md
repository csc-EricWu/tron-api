# TRON API

A PHP API for interacting with the Tron Protocol

[![Latest Stable Version](https://poser.pugx.org/iexbase/tron-api/version)](https://packagist.org/packages/iexbase/tron-api)
[![Software License](https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square)](LICENSE)
[![Build Status](https://api.travis-ci.com/iexbase/tron-api.svg?branch=master)](https://travis-ci.com/iexbase/tron-api)
[![Contributors](https://img.shields.io/github/contributors/iexbase/tron-api.svg)](https://github.com/iexbase/tron-api/graphs/contributors)
[![Total Downloads](https://img.shields.io/packagist/dt/iexbase/tron-api.svg?style=flat-square)](https://packagist.org/packages/iexbase/tron-api)

## Install

```bash
composer require iexbase/tron-api
```

### Install from a Git repository (fork)

If Packagist is outdated or the original repository is unmaintained, you can install from a Git repository (for example a fork) via Composer VCS.

Example using `csc-EricWu/tron-api`:

1. Add a VCS repository to your project's `composer.json`:

```json
{
  "repositories": [
    {
      "type": "vcs",
      "url": "https://github.com/csc-EricWu/tron-api"
    }
  ],
  "require": {
    "iexbase/tron-api": "master"
  }
}
```

2. Update/install:

```bash
composer update iexbase/tron-api
```

Tip: For production, prefer pinning to a tag or a specific commit hash instead of tracking a moving branch.

## Requirements

The following versions of PHP are supported by this version.

- PHP >= 8.0

Extensions required:

- ext-bcmath
- ext-gmp

## Example Usage

```php
use IEXBase\TronAPI\Tron;

$fullNode = new \IEXBase\TronAPI\Provider\HttpProvider('https://api.trongrid.io');
$solidityNode = new \IEXBase\TronAPI\Provider\HttpProvider('https://api.trongrid.io');
$eventServer = new \IEXBase\TronAPI\Provider\HttpProvider('https://api.trongrid.io');

try {
    $tron = new \IEXBase\TronAPI\Tron($fullNode, $solidityNode, $eventServer);
} catch (\IEXBase\TronAPI\Exception\TronException $e) {
    exit($e->getMessage());
}


$this->setAddress('..');
//Balance
$tron->getBalance(null, true);

// Transfer Trx
var_dump($tron->send('to', 1.5));

//Generate Address
var_dump($tron->createAccount());

//Get Last Blocks
var_dump($tron->getLatestBlocks(2));

//Change account name (only once)
var_dump($tron->changeAccountName('address', 'NewName'));


// Contract
$tron->contract('Contract Address');



```

## Testing

```bash
$ vendor/bin/phpunit
```

## Donations

**Tron(TRX)**: TRWBqiqoFZysoAeyR1J35ibuyc8EvhUAoY
