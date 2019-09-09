nmap
====

**nmap** is a PHP wrapper for [Nmap](http://nmap.org/), a free security scanner for network exploration.

[![Build Status](https://travis-ci.org/willdurand/nmap.svg?branch=master)](https://travis-ci.org/willdurand/nmap)

> Updated version for symfony/process: ^4.0 and PHP 7.1+

Usage
-----

```php
$hosts = Nmap::create()->scan([ 'williamdurand.fr' ]);

$ports = $hosts->getOpenPorts();
```

You can specify the ports you want to scan:

``` php
$nmap = new Nmap();

$nmap->scan([ 'williamdurand.fr' ], [ 21, 22, 80 ]);
```

**OS detection** and **Service Info** are disabled by default, if you want to
enable them, use the `enableOsDetection()` and/or `enableServiceInfo()` methods:

``` php
$nmap
    ->enableOsDetection()
    ->scan([ 'williamdurand.fr' ]);

$nmap
    ->enableServiceInfo()
    ->scan([ 'williamdurand.fr' ]);

// Fluent interface!
$nmap
    ->enableOsDetection()
    ->enableServiceInfo()
    ->scan([ 'williamdurand.fr' ]);
```

Turn the **verbose mode** by using the `enableVerbose()` method:

``` php
$nmap
    ->enableVerbose()
    ->scan([ 'williamdurand.fr' ]);
```

For some reasons, you might want to disable port scan, that is why **nmap**
provides a `disablePortScan()` method:

``` php
$nmap
    ->disablePortScan()
    ->scan([ 'williamdurand.fr' ]);
```

You can also disable the reverse DNS resolution with `disableReverseDNS()`:

``` php
$nmap
    ->disableReverseDNS()
    ->scan([ 'williamdurand.fr' ]);
```

You can define the process timeout (default to 60 seconds) with `setTimeout()`:

``` php
$nmap
    ->setTimeout(120)
    ->scan([ 'williamdurand.fr' ]);
```

Version
------------
0.8.3

Installation
------------

The recommended way to install nmap is through
[Composer](http://getcomposer.org/):

``` json
{
    "require": {
        "repat/willdurand-nmap": "^0.8"
    }
}
```

Or:

`composer require repat/willdurand-nmap`

License
-------
nmap is released under the MIT License. See the bundled LICENSE file for details.
