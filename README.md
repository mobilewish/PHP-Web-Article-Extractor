# PHP Web Article Extractor

Web Article Extractor is a PHP library that detects and extracts the primary 'article' content from a web page, detecting and removing the 'clutter' to give you the clean article. Additionally, it will also filter information from the article that can be used for indexing, such as *language* and *keywords*. 

## Features

* Extracts a clean article and headline from a web page quickly.
* Identifies the language of the extracted article.
* Identifies keywords for the extracted article.
* Designed to easily integrate into pipeline or microservice project architectures.

## Usage
There are two ways to use Web Article Extractor, the first way is to use the provided Docker file (See 'Installation'), this will create an instance that you can start using straight away and is ideal for pipeline architectures, the second way is to add the PHP library into your project through Composer.

## Installation
#### Docker
To build with Docker execute the build command inside this project's root directory
```bash
$ docker build -t zackslash/web-article-extractor .
```
You should now be able to run the article extractor script with the following command
```bash
$ docker run zackslash/web-article-extractor <URL>
```

Example:
```bash
$ docker run zackslash/web-article-extractor http://uk.ign.com/articles/2015/03/19/gabe-newell-discusses-possibility-of-half-life-3
```

#### Composer
The first step to using Web Article Extractor in PHP is to download Composer:

```bash
$ curl -s http://getcomposer.org/installer | php
```

Now add PHP Web Article Extractor to your project with Composer:

```bash
$ php composer.phar require zackslash/php-web-article-extractor
```

And that's it! Composer will automatically handle the rest.

Alternatively, you can manually add the dependency to `composer.json` file...

```json
{
    "require": {
        "zackslash/php-web-article-extractor": "*"
    }
}
```

... and then install our dependencies using:
```bash
$ php composer.phar install
```

PHP simple example:

```php
<?php

// This file is generated by Composer
require_once 'vendor/autoload.php';

// Extract article directly from a URL
$extractionResult = WebArticleExtractor\Extract::extractFromURL('http://uk.ign.com/articles/2015/03/19/gabe-newell-discusses-possibility-of-half-life-3');

// Display the extracted article in JSON form
echo json_encode($extractionResult);

?>
```
## Requirements

* PHP >= 5.5.0

## Running the Tests (Optional)

To run the unit tests, you'll need to install [PHPUnit](https://phpunit.de/), once installed, just launch the following command inside this libraries' 'build' directory:

```
$ phpunit
```

## Acknowledgements

Parts of PHP Web Article Extractor are based on algorithms from the whitepaper ['Boilerplate detection using Shallow Text Features'](http://www.l3s.de/~kohlschuetter/publications/wsdm187-kohlschuetter.pdf) 
and 'Boilerpipe' by Christian Kohlschuetter, Peter Fankhauser, Wolfgang Nejdl

PHP Web Article Extractor implements the Rapid Automatic Keyword Extraction (RAKE) algorithm as described in the book ['Text Mining: Theory and Applications'](http://www.amazon.com/Text-Mining-Applications-Michael-Berry/dp/0470749822) and the implementation was based on [aneesha's open source Python version](https://github.com/aneesha/RAKE)

The Stop Word dictionary used in this project was pulled from [Peter Graham's 'stopwords' repository](https://github.com/6/stopwords)


## License

PHP Web Article Extractor is released under the MIT License.
See the bundled [LICENSE](https://github.com/zackslash/PHP-Web-Article-Extractor/blob/master/LICENCE) file for details.
