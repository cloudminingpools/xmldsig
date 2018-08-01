# XMLDSIG for PHP

* Sign XML Documents with Digital Signatures ([XMLDSIG](https://www.w3.org/TR/xmldsig-core/))
* Verify the Digital Signatures of XML Documents

[![Latest Version on Packagist](https://img.shields.io/github/release/odan/xmldsig.svg)](https://github.com/odan/xmldsig/releases)
[![Software License](https://img.shields.io/badge/license-MIT-brightgreen.svg)](LICENSE)
[![Build Status](https://travis-ci.org/odan/xmldsig.svg?branch=master)](https://travis-ci.org/odan/xmldsig)
[![Code Coverage](https://scrutinizer-ci.com/g/odan/xmldsig/badges/coverage.png?b=master)](https://scrutinizer-ci.com/g/odan/xmldsig/?branch=master)
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/odan/xmldsig/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/odan/xmldsig/?branch=master)
[![Total Downloads](https://img.shields.io/packagist/dt/odan/xmldsig.svg)](https://packagist.org/packages/odan/xmldsig)

## Requirements

* PHP 7.1.3+
* openssl extension

## Installation

```
composer require odan/xmldsig
```

## Usage

### Sign XML Documents with Digital Signatures

```php

```

### Verify the Digital Signatures of XML Documents

#### Using a .pfx file

Input file: example.xml

```xml
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2025</expiry>  
    </creditcard>  
</root>
```

```php
use Odan\XmlDSig\SignedXml;

$signedXml = new SignedXml('sha512');
$signedXml->loadPfx('filename.pfx', 'password');
$signedXml->signXmlFile('example.xml', 'signed-example.xml');
```

Output file: signed-example.xml

```xml
<?xml version="1.0"?>
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2025</expiry>  
    </creditcard>  
	<Signature xmlns="http://www.w3.org/2000/09/xmldsig#">
	<SignedInfo>
		<CanonicalizationMethod Algorithm="http://www.w3.org/TR/2001/REC-xml-c14n-20010315"/>
		<SignatureMethod Algorithm="http://www.w3.org/2000/09/xmldsig#rsa-sha512"/>
		<Reference URI="">
			<Transforms>
				<Transform Algorithm="http://www.w3.org/2000/09/xmldsig#enveloped-signature"/>
			</Transforms>
			<DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha512"/>
			<DigestValue>e4fItlvaCb8Vm2MYTnnmGZ3aujRb/J+79Fc/nCkE8WYn5lPuztUl1GxoODZYFMA1jzP4FSTaEuMgsCmmmXU0xw==</DigestValue>
		</Reference>
	</SignedInfo>
	<SignatureValue>rzflsb768ViuC+yrrZfr7H+iren/cvIIpXETqGNwHU5u9TixY13vI4xgmriGDErKCKe5...</SignatureValue>
	</Signature>
</root>
```

## Documentation

This package is documented [here](https://odan.github.io/xmldsig/).

## License

The MIT License (MIT). Please see [License File](LICENSE) for more information.


[PSR-1]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md
[PSR-2]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md
[PSR-4]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md
[Composer]: http://getcomposer.org/
[PHPUnit]: http://phpunit.de/
