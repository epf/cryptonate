cryptonate
==========

Converts between currencies using the [cryptonator.com API](https://www.cryptonator.com/api).

### Usage:
```
$ cryptonate -h
usage: cryptonate [-h] [-v] X Y [N]

Converts an amount of currency X to Y using the current exchange rate from
cryptonator. If no value is given an amount of 1 X is used. If invoked as X2Y,
the currencies X and Y are inferred.

positional arguments:
  X              the currency to convert from
  Y              the currency to convert to
  N              the amount of X to convert to Y (default: 1)

optional arguments:
  -h, --help     show this help message and exit
  -v, --verbose  display verbose output
```
  
### Examples:
(Assumes `cryptonate` is in your `$PATH`)
#### Invoking as `cryptonate`:
```
$ cryptonate DOGE GBP 50
0.006250

$ cryptonate -v DRK BTC
1 DRK = 0.00891338 BTC
```

#### Invoking as `X2Y`:
```
$ ln -s cryptonate btc2usd
```
(Assumes `btc2usd` and `cryptonate` are in your `$PATH`)
```
$ btc2usd -h
usage: btc2usd [-h] [-v] [N]

Converts an amount of currency BTC to USD using the current exchange rate from
cryptonator. If no value is given an amount of 1 BTC is used.

positional arguments:
  N              the amount of BTC to convert to USD (default: 1)

optional arguments:
  -h, --help     show this help message and exit
  -v, --verbose  display verbose output

$ btc2usd
586.68

$ btc2usd -v 0.25
0.25 BTC = 146.67 USD

$ btc2usd 0.00000001
0.000006
```

### Known issues:
* No error handling for connection issues (such as when cryptonator.com is down)
* No option to access the *full ticker* for lots of extra information
* No ability to know when BTC gets used as an intermediate currency (API limitation)

### Notes:

This is my first time really using the `argparse` module. Comments, critiques, and patches are welcome.
