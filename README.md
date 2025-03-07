## Bluesnap PHP Library

**NOTE FROM AUTHOR** this library is not production ready as my company decided against using bluesnap shortly after starting this project. Please feel free to fork it and make it fit your needs, all endpoints are working as of June 2017, however the library is missing several features that bluesnap offers. Development and maintence on this project has been discontinued. 

**NOTE FROM PERFECTPANEL** just updated requirements of guzzlehttp/guzzle up to version ^7.5. Original package: `tdanielcox/bluesnap-php`.

---------------------------------

This (unofficial) library standardizes and simplifies working with the bluesnap api. 

All the standard api documentation is applicable to this library. 

View the bluesnap documentation here: https://developers.bluesnap.com/v8976-JSON/docs

This library currently supports:

- CardTransactions
- VaultedShoppers
- Vendors
- Subscriptions
- Plans (Subscriptions)
- Refunds
- Reports

### Installation

Install this package with composer

```shell
composer require perfectpanel/extlib-bluesnap-php
```

### Usage

Initialize the library in your class constructor 

```php
public function __construct()
{
    $environment = 'sandbox'; // or 'production'
    \tdanielcox\Bluesnap\Bluesnap::init($environment, 'YOUR_API_KEY', 'YOUR_API_PASSWORD');
}
```

Create a New Transaction

```php
public function createTransaction()
{
    $response = \tdanielcox\Bluesnap\CardTransaction::create([
        'creditCard' => [
            'cardNumber' => '4263982640269299',
            'expirationMonth' => '02',
            'expirationYear' => '2018',
            'securityCode' => '837'
        ],
        'amount' => 10.00,
        'currency' => 'USD',
        'recurringTransaction' => 'ECOMMERCE',
        'cardTransactionType' => 'AUTH_CAPTURE',
    ]);

    if ($response->failed())
    {
        $error = $response->data;
        
        // handle error
    }

    $transaction = $response->data;
    
    return $transaction;
}
```

#### See [examples](https://github.com/tdanielcox/bluesnap-php/tree/master/examples) for further details on using the library

## License
This package is licensed under the [MIT License](https://github.com/tdanielcox/bluesnap-php/blob/master/LICENSE)
