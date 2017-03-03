# PHP Barcode Generator
This is, first of all, a fork of [this repo](https://github.com/violuke/php-barcodes)
The goal of this fork is to make this project easier to use.
This is an easy to use, non-bloated, framework independent, barcode generator in PHP.

It creates SVG, PNG, JPG and HTML images, from the most used 1D barcode standards.

*The codebase is largely from the [TCPDF barcode generator](https://github.com/tecnickcom/TCPDF) by Nicola Asuni. This code is therefor licensed under LGPLv3. It is still a bit of a mess, bit I will clean it in the future. I do not expect the interface of this class will change during the clean ups.*

## Installation
Just clone the repo and `include` required modules.
## Usage
Initiate the barcode generator for the output you want, then call the ->getBarcode() routine as many times as you want.

```php
$generator = new Picqer\Barcode\BarcodeGeneratorHTML();
echo $generator->getBarcode('081231723897', $generator::TYPE_CODE_128);
```

The ->getBarcode() routine accepts the following:
- $code Data for the barcode
- $type Type of barcode, use the constants defined in the class
- $widthFactor Width is based on the length of the data, with this factor you can make the barcode bars wider then default
- $totalHeight The total height of the barcode
- $color Hex code of the foreground color

## Image types
```php
$generatorSVG = new Picqer\Barcode\BarcodeGeneratorSVG();
$generatorPNG = new Picqer\Barcode\BarcodeGeneratorPNG();
$generatorJPG = new Picqer\Barcode\BarcodeGeneratorJPG();
$generatorHTML = new Picqer\Barcode\BarcodeGeneratorHTML();
```

## Accepted types
- TYPE_CODE_39
- TYPE_CODE_39_CHECKSUM
- TYPE_CODE_39E
- TYPE_CODE_39E_CHECKSUM
- TYPE_CODE_93
- TYPE_STANDARD_2_5
- TYPE_STANDARD_2_5_CHECKSUM
- TYPE_INTERLEAVED_2_5
- TYPE_INTERLEAVED_2_5_CHECKSUM
- TYPE_CODE_128
- TYPE_CODE_128_A
- TYPE_CODE_128_B
- TYPE_CODE_128_C
- TYPE_EAN_2
- TYPE_EAN_5
- TYPE_EAN_8
- TYPE_EAN_13
- TYPE_UPC_A
- TYPE_UPC_E
- TYPE_MSI
- TYPE_MSI_CHECKSUM
- TYPE_POSTNET
- TYPE_PLANET
- TYPE_RMS4CC
- TYPE_KIX
- TYPE_IMB
- TYPE_CODABAR
- TYPE_CODE_11
- TYPE_PHARMA_CODE
- TYPE_PHARMA_CODE_TWO_TRACKS

## Examples
Embedded PNG image in HTML:

```php
$generator = new \Picqer\Barcode\BarcodeGeneratorPNG();
echo '<img src="data:image/png;base64,' . base64_encode($generator->getBarcode('081231723897', $generator::TYPE_CODE_128)) . '">';
```
