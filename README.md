# Cloudder
[![Build Status](http://img.shields.io/travis/jrm2k6/cloudder/master.svg?style=flat-square)](https://travis-ci.org/jrm2k6/cloudder)
[![License](http://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square)](http://www.opensource.org/licenses/MIT)
[![Latest Version](http://img.shields.io/packagist/v/jrm2k6/cloudder.svg?style=flat-square)](https://packagist.org/packages/jrm2k6/cloudder)
[![Total Downloads](https://img.shields.io/packagist/dt/jrm2k6/cloudder.svg?style=flat-square)](https://packagist.org/packages/jrm2k6/cloudder)

Cloudinary wrapper for Laravel 4.2

__Initially forked from https://github.com/teepluss/laravel4-cloudinary.
As it doesn't seem to be maintained anymore, and facing the lack of response from the original maitainer (issue opened + pull request opened, last commit on August last year), I decided to create a new fork that I plan on maintaining. We will move to Laravel 5 really soon, so I will also have a laravel 5 branch in development.__


## Installation

```
composer require jrm2k6/cloudder
```
## Configuration
Modify ```config.php``` in jrm2k6/cloudder and all your information from your cloudinary dashboard.
Add the following in app.php:
```
'providers' => array(
  'JD\Cloudder\CloudderServiceProvider'
);
  
'aliases' => array(
  'Cloudder' => 'JD\Cloudder\Facades\Cloudder'
);
```
## Usage

``` 
Cloudder::upload($filename, $publicId, $options, $tags);
```
with:
- filename: path to the image you want to upload
- publicId: the id you want your picture to have on Cloudinary, leave it null to have Cloudinary generate a random id.
- options: options for your uploaded image, check the cloudinary documentation to know more
- tags: tags for your image

returns the CloudinaryWrapper.

```
Cloudder::getPublicId()
```
returns the public id of the last uploaded image.


```
Cloudder::getResult()
```
returns the result of the last uploaded image

```
Cloudder::show($publicId, $options)
```
with:
- publicId: public id of the resource to display
- options: options for your uploaded image, check the cloudinary documentation to know more

returns the url of the picture on cloudinary

```
Cloudder::showPrivateUrl($publicId, $format, $options)
```
with:
- publicId: public id of the resource to display
- format: format of the picture your want to display
- options: options for your uploaded image, check the cloudinary documentation to know more

returns the private url of the picture on cloudinary, expiring by default after an hour.


```
Cloudder::rename($publicId, $toPublicId, $options)
```

with: 
- publicId: publicId of the resource to rename
- toPublicId: new public id of the resource
- options: options for your uploaded image, check the cloudinary documentation to know more

renames the original picture with the toPublicId id.

```
Cloudder::destroyImage($publicId, $options)
Cloudder::delete($publicId, $options)
```
with:
- publicId: publicId of the resource to rename
- options: options for your uploaded image, check the cloudinary documentation to know more

removes image from Cloudinary

```
Cloudder::destroyImages($publicIds, $options)
```
with:
- publicIds: array of ids, identifying the pictures to remove
- options: options for the images to delete, check the cloudinary documentation to know more

removes images from Cloudinary


```
Cloudder::addTag($tag, $publicIds, $options)
```

with:
- tag: tag to apply
- publicIds: images to apply tag to
- options: options for your uploaded image, check the cloudinary documentation to know more

```
Cloudder::removeTag($tag, $publicIds, $options)
```

with:
- tag: tag to remove
- publicIds: images to remoe tag from
- options: options for your uploaded image, check the cloudinary documentation to know more

## Running tests
```
phpunit
```
