# League\Flysystem\AwsS3v3

[![Author](http://img.shields.io/badge/author-@frankdejonge-blue.svg?style=flat-square)](https://twitter.com/frankdejonge)
[![Build Status](https://img.shields.io/travis/thephpleague/flysystem-aws-s3-v3/master.svg?style=flat-square)](https://travis-ci.org/thephpleague/flysystem-aws-s3-v3)
[![Coverage Status](https://img.shields.io/scrutinizer/coverage/g/thephpleague/flysystem-aws-s3-v3.svg?style=flat-square)](https://scrutinizer-ci.com/g/thephpleague/flysystem-aws-s3-v3)
[![Quality Score](https://img.shields.io/scrutinizer/g/thephpleague/flysystem-aws-s3-v3.svg?style=flat-square)](https://scrutinizer-ci.com/g/thephpleague/flysystem-aws-s3-v3)
[![Software License](https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square)](LICENSE)
[![Packagist Version](https://img.shields.io/packagist/v/league/flysystem-aws-s3-v3.svg?style=flat-square)](https://packagist.org/packages/league/flysystem-aws-s3-v3)
[![Total Downloads](https://img.shields.io/packagist/dt/league/flysystem-aws-s3-v3.svg?style=flat-square)](https://packagist.org/packages/league/flysystem-aws-s3-v3)

This is a Flysystem adapter for the aws-sdk-php v3. Forked to support minio. (https://minio.io)

# Installation

```bash
composer require digiservnet/flysystem-aws-s3-v3-minio
```

# Bootstrap

``` php
<?php
use Aws\S3\S3Client;
use League\Flysystem\AwsS3v3\AwsS3Adapter;
use League\Flysystem\Filesystem;

include __DIR__ . '/vendor/autoload.php';

$client = new S3Client([
    'credentials' => [
        'key'    => 'your-key',
        'secret' => 'your-secret'
    ],
    'region' => 'your-region',
    'version' => 'latest|version',
]);

$options = [
        'override_visibility_on_copy' => true
    ];
$adapter = new AwsS3Adapter($client, 'your-bucket-name', '', $options);
$filesystem = new Filesystem($adapter);
```

# Laravel 
config/filesystems.php
```
'site' => [
    'driver' => 's3',
    'key' => env('AWS_KEY'),
    'secret' => env('AWS_SECRET'),
    'endpoint' => env('AWS_ENDPOINT'),
    'region' => env('AWS_REGION'),
    'bucket' => env('AWS_BUCKET'),
    'use_path_style_endpoint' => true,
    'options' => [
        'override_visibility_on_copy' => 'private',
    ]
]
```
