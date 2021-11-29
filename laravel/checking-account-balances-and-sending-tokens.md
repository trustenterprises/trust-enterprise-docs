---
description: >-
  In this flow, we are going to describe the process of checking an account
  balance and sending tokens to a hedera id. There are a number of applications
  of this including systems for access tokens and
---

# Checking account balances and sending tokens

## Overview

This process of sending tokens to an external account isn't permissioned, that is any hedera wallet can register with a system, and you can use these actions.

{% hint style="warning" %}
Under Hedera's APIs, sending of tokens requires an association of a given token, at this time we are focused on using the [Venly Wallet (Widget)](https://docs.venly.io/widget/) which provides 25 free associations for tokens per wallet.
{% endhint %}



## Check a token balance

Check a hedera token balance for any account, this focused on HTS tokens such that if you need to check the balance for access to a service or to gauge an account share of a staking pool.

{% hint style="info" %}
&#x20;Infrastructure testing needs to be conducted for high-volume account balance requests.
{% endhint %}

### Imports

```
use Trustenterprises\LaravelHashgraph\LaravelHashgraph;
use Trustenterprises\LaravelHashgraph\Models\AccountTokenBalanceResponse;
```

### Code

```
$account_id = '0.0.15657776'; // A venly-created account on testnet
$token_id = '0.0.15657534'; // Token already created

$token_balance = LaravelHashgraph::getTokenBalance($account_id, $token_id);

// Token value in whole numbers, ignoring the "decimals places" of a created token.
$token_balance->getAmount(); 
```

## Send a token to an account

Send a token to a hedera account, expects a SendToken object to be created at the payload. The response will tell you if the transfer succeeded or not, if the latter an error can be used.

This assumes that the token you are sending has been created with the mint token methods of the API/client and has custody over them.

{% hint style="info" %}
This method waits for the finality of the transfer transaction, thus you will receive an error that a transfer has failed that will describe the issue, if an originator account does not have enough balance to make the transfer or if there is an association error.



Expect the response to be between 2-3 seconds, jobs should be used.
{% endhint %}

### Imports

```
use Trustenterprises\LaravelHashgraph\LaravelHashgraph;
use Trustenterprises\LaravelHashgraph\Models\SendToken;
use Trustenterprises\LaravelHashgraph\Models\SendTokenResponse;
```

### Code

```
// Pre-generated Venly wallet (testnet) (maxes out at 25 assocs)
$account_id = '0.0.15657776'; // A venly-created account on testnet
$token_id = '0.0.15657534'; // Token already created
$amount = 0.000001;

$send_token = new SendToken($token_id, $account_id, $amount);
$token_sent = LaravelHashgraph::sendToken($send_token);

if ($token_sent->hasTransferSucceeded()) {
    // Continue action.
} else {
    $token_sent->getError();
}
```
