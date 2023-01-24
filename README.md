# OpenAPIClient-php

Due to regulatory requirements applicable to our EU/UK sellers, for certain APIs, developers need to add digital signatures to the respective HTTP call. The Key Management API creates keypairs that are required when creating digital signatures for the following APIs:<ul><li>All methods in the <a href=\"/api-docs/sell/finances/resources/methods \" target=\"_blank \">Finances API</a></li><li><a href=\"/api-docs/sell/fulfillment/resources/order/methods/issueRefund \" target=\"_blank \">issueRefund</a> in the Fulfillment API</li><li><a href=\"/Devzone/XML/docs/Reference/eBay/GetAccount.html \" target=\"_blank \">GetAccount</a> in the Trading API</li><li>The following methods in the Post-Order API:<ul><li><a href=\"/Devzone/post-order/post-order_v2_inquiry-inquiryid_issue_refund__post.html \" target=\"_blank \">Issue Inquiry Refund</a></li><li><a href=\"/Devzone/post-order/post-order_v2_casemanagement-caseid_issue_refund__post.html \" target=\"_blank \">Issue case refund</a></li><li><a href=\"/Devzone/post-order/post-order_v2_return-returnid_issue_refund__post.html \" target=\"_blank \">Issue return refund</a></li><li><a href=\"/Devzone/post-order/post-order_v2_return-returnid_decide__post.html \" target=\"_blank \">Process Return Request</a></li><li><a href=\"/devzone/post-order/post-order_v2_cancellation-cancelid_approve__post.html \" target=\"_blank \">Approve Cancellation Request</a></li><li><a href=\"/devzone/post-order/post-order_v2_cancellation__post.html \" target=\"_blank \">Create Cancellation Request</a></li></ul></li></ul><span class=\"tablenote\"><b>Note:</b> For additional information about keypairs and creating Message Signatures, refer to <a href= \"/develop/guides/digital-signatures-for-apis \" target= \"_blank \">Digital Signatures for APIs</a>.</span>


## Installation & Usage

(re)generate sdk
```shell
docker run --rm -v "${PWD}:/local" openapitools/openapi-generator-cli:v5.0.1 generate 
\-i https://developer.ebay.com/api-docs/master/developer/key-management/openapi/3/developer_key_management_v1_oas3.json 
\-g php 
\ --git-user-id cdma-numiscorner
\--git-host github.com
\ --git-repo-id ebay-developer-key-management-api 
\--invoker-package 'OpenAPI\EbayDevKeyManagementClient'
\ --artifact-version 1.0
```

### Requirements

PHP 7.2 and later.

### Composer

To install the bindings via [Composer](https://getcomposer.org/), add the following to `composer.json`:

```json
{
  "repositories": [
    {
      "type": "vcs",
      "url": "https://github.com/cdma-numiscorner/ebay-developer-key-management-api.git"
    }
  ],
  "require": {
    "cdma-numiscorner/ebay-developer-key-management-api": "*@dev"
  }
}
```

Then run `composer install`

### Manual Installation

Download the files and include `autoload.php`:

```php
<?php
require_once('/path/to/OpenAPIClient-php/vendor/autoload.php');
```

## Getting Started

Please follow the [installation procedure](#installation--usage) and then run the following:

```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');



// Configure OAuth2 access token for authorization: api_auth
$config = OpenAPI\EbayDevKeyManagementClient\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');


$apiInstance = new OpenAPI\EbayDevKeyManagementClient\Api\SigningKeyApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$create_signing_key_request = new \OpenAPI\EbayDevKeyManagementClient\Model\CreateSigningKeyRequest(); // \OpenAPI\EbayDevKeyManagementClient\Model\CreateSigningKeyRequest

try {
    $result = $apiInstance->createSigningKey($create_signing_key_request);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling SigningKeyApi->createSigningKey: ', $e->getMessage(), PHP_EOL;
}

```

## API Endpoints

All URIs are relative to *https://apiz.ebay.com/developer/key_management/v1*

Class | Method | HTTP request | Description
------------ | ------------- | ------------- | -------------
*SigningKeyApi* | [**createSigningKey**](docs/Api/SigningKeyApi.md#createsigningkey) | **POST** /signing_key | 
*SigningKeyApi* | [**getSigningKey**](docs/Api/SigningKeyApi.md#getsigningkey) | **GET** /signing_key/{signing_key_id} | 
*SigningKeyApi* | [**getSigningKeys**](docs/Api/SigningKeyApi.md#getsigningkeys) | **GET** /signing_key | 

## Models

- [CreateSigningKeyRequest](docs/Model/CreateSigningKeyRequest.md)
- [Error](docs/Model/Error.md)
- [ErrorParameter](docs/Model/ErrorParameter.md)
- [QuerySigningKeysResponse](docs/Model/QuerySigningKeysResponse.md)
- [SigningKey](docs/Model/SigningKey.md)

## Authorization

### api_auth

- **Type**: `OAuth`
- **Flow**: `application`
- **Authorization URL**: ``
- **Scopes**: 
    - **https://api.ebay.com/oauth/api_scope**: View public data from eBay

## Tests

To run the tests, use:

```bash
composer install
vendor/bin/phpunit
```

## Author



## About this package

This PHP package is automatically generated by the [OpenAPI Generator](https://openapi-generator.tech) project:

- API version: `v1.0.0`
    - Package version: `1.0`
- Build package: `org.openapitools.codegen.languages.PhpClientCodegen`
