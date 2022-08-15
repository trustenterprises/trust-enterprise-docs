---
description: >-
  The backbone for a permissioned marketplace for you to mint tokens, create
  accounts, and to send  to your users after purchase.
---

# Create a Marketplace

## Overview

Understand that decentralisation is hard, many people don't have experience to use blockchain applications to use apps like [Metamask](https://metamask.io/) and others. The role of this API and client is for you to build&#x20;

{% hint style="warning" %}
I'm going to assume that you know Laravel, creating of tables to link users to generated accounts. As we move forward there will be updates but for now this will be simple.
{% endhint %}

## Creating an account

Create and connect a hedera account to a user you have in your system, I would suggest either adding a new field on your **users** table or creating a new **hedera\_accounts** table for a one-to-many relationship.

In this case I am using a simple approach that a user can only have one hedera account, thus three new fields have been added to a user migration.

* encrypted\_key
* public\_key
* hedera\_id

### Imports

```
use Trustenterprises\LaravelHashgraph\LaravelHashgraph;
use Trustenterprises\LaravelHashgraph\Models\AccountCreateResponse;
```

### Code

```
$account = LaravelHashgraph::createAccount(); // Returns AccountCreateResponse

// Get the Authorised user from a controller.
$user = \Auth::user();

// Update the fields of the user.
$user->encrypted_id = $account->getEncryptedKey();
$user->public_key = $account->getPublicKey();
$user->hedera_id = $account->getAccountId();

// Persist to storage.
$user->save();
```

## Creating a token

Create a token that can be sent to a user's account after an event or a purchase.

{% hint style="info" %}
Recommend that you create a new table to hold the details of a minted token. Use the returned **tokenId** at the primary key.
{% endhint %}

### Imports

```
use Trustenterprises\LaravelHashgraph\LaravelHashgraph;
use Trustenterprises\LaravelHashgraph\Models\FungibleTokenResponse;
use Trustenterprises\LaravelHashgraph\Models\FungibleToken;
```

### Code

```
// The base token object.
$fungible_token = new FungibleToken('MATT', 'MATTHEW', 10, 'This is a memo');

// The response from hedera, via the API
$token = LaravelHashgraph::mintFungibleToken($fungible_token);

// Store this id against the details of the above object.
$token->getTokenId();
```

## Bequesting a token

Bequesting or sending a token to an account that has been generated, and linked to a user in your local database. This bypasses hedera's default association behaviour.

This is the magic element that provides a **permissioned marketplace**, the ability to send tokens of any asset to a user from any event.&#x20;

### Imports

```
use Trustenterprises\LaravelHashgraph\LaravelHashgraph;
use Trustenterprises\LaravelHashgraph\Models\BequestToken;
use Trustenterprises\LaravelHashgraph\Models\BequestTokenResponse;
```

### Code

```
// Assume the user and token from the previous steps.
$token_id = $token->getTokenId();

$encrypted_key = $user->encrypted_key;
$public_key = $user->public_key;
$hedera_id = $user->hedera_id;

$amount = 1;

// The object to bequest tokens to an account
$bequest = new BequestToken($encrypted_key, $token_id, $hedera_id, $amount);

// The response from hedera, to send tokens
$response = LaravelHashgraph::bequestToken($bequest);

// This transaction id can be tracked on a hedera explorer such as dragonglass.
$response->getTransactionId();

```
