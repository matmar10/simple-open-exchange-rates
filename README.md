Simple Open Exchange Rates
==========================

Extremely simple way to convert rates between currencies using rates at [OpenExchangeRates.org](https://openexchangerates.org).

Pulls the exchange rate remotely and saves locally to a text file.

# Getting Started

Register for a client key at [OpenExchangeRates.org](https://openexchangerates.org/signup/free)

Install the package:

```
npm install currency-converter
```

Use it:

```
var cc = require('currency-converter')({
  CLIENTKEY: YOUR_OPEN_EXCHANGE_RATES_KEY, [fetchInterval: 3600000]
});
```

__NOTE: Default fetchInterval value is set to one hour.__

# Usage

This module makes it __extremely__ easy for you to convert currencies.

The very basic input takes in two parameters. _convertFrom_ & _convertTo_ must be valid country codes. See list <a href='http://www.localeplanet.com/api/auto/currencymap.html'> here</a>.

The module fetches live rates on initialize, saves it locally, and retrieves locally saved rates by default, unless otherwise specified.

## .convert(amount, convertFrom, convertTo, [live])

Converts an amount specified to a specific currency. _live_ is an optional parameter
that uses live rates from [openexchangerates.org](https://openexchangerates.org/signup/free)

Response:

```JavaScript
const converted = await cc.rates(1, 'USD', 'EUR');
// {
//    "currency": "EUR",
//    "symbol": "€",
//    "amount": 0.76
// }
```

## .rates(convertFrom, convertTo, [live])

Returns the conversion rate between two currencies:

```JavaScript
const rate = await cc.rates('USD', 'EUR');
// 0.76
```

Fetch the live rate:

```JavaScript
const rate = await cc.rates('USD', 'EUR', true);
// 0.76
```

## .currencies

The map of currency codes to info about the currency

```JavaScript
cc.currencies.EUR
// {
//    "currency": "EUR",
//    "symbol": "€",
//    "amount": 0.76
// }
```

## .shutdown

Stop the periodic polling for rates.

```JavaScript
cc.shutdown();
```

If you don't do this, your script will never terminate normally since
there will be a dangling timeout.

# Credits

A fork of [dmamaril/npm-currency-converter](https://github.com/dmamaril/npm-currency-converter) but that project is unmaintained.
