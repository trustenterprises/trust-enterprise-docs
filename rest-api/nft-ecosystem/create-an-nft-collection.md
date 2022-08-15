---
description: >-
  Create an NFT Collection with a name, symbol, supply, and basic default
  royalties.
---

# Create an NFT Collection

### Overview

There are 3 required fields needed to create an NFT:

* symbol
* collection\_name
* supply

In addition, **royalties of 5% are automatically added, these may be turned off.** After all, we don't live in a web2 world anymore.

These are the optional fields you can use:

* allow\_custom\_fees (to disable royalties)
* royalty\_account\_id (the account that will receive royalties, defaults to the Treasury API account)
* royalty\_fee (set as 0.05, or 5%, by default)
* fallback\_fee (default set as 0, for simpler internal transfers)
* enable\_unsafe\_keys (**CONSIDERED DANGEROUS:** set the admin, freeze, and wipe keys)

{% swagger method="post" path="/api/nft" baseUrl="https://hedera-serverless-consensus.vercel.app" summary="" %}
{% swagger-description %}
Create an NFT collection
{% endswagger-description %}

{% swagger-parameter in="body" name="symbol" required="true" type="" %}
Symbol of the NFT collection
{% endswagger-parameter %}

{% swagger-parameter in="body" name="name" required="true" %}
Name of the NFT collection
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-api-key" required="true" %}
The 

**API_SECRET_KEY**

 from the client's environment variables.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="supply" type="Int" required="true" %}
Supply of the NFT collection
{% endswagger-parameter %}

{% swagger-parameter in="body" name="allow_custom_fees" type="boolean" %}
default true, enable custom/royalty fees
{% endswagger-parameter %}

{% swagger-parameter in="body" name="royalty_account_id" type="String" %}
Hedera account id to send royalties to 
{% endswagger-parameter %}

{% swagger-parameter in="body" name="royalty_fee" type="decimal" %}
Royalty percentage as a decimal for secondary sales
{% endswagger-parameter %}

{% swagger-parameter in="body" name="fallback_fee" type="decimal" %}
HBAR fallback for non-treasury transfers
{% endswagger-parameter %}

{% swagger-parameter in="body" name="enable_unsafe_keys" type="boolean" %}
**Considered Dangerous, if true, stops an NFT collection from being immutable**
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="NFT collection created" %}
```javascript
{
    // Response
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="Header Auth Missing/invalid" %}
```javascript
{
    // Response
}
```
{% endswagger-response %}

{% swagger-response status="422: Unprocessable Entity" description="Missing params in body" %}
```javascript
{
    // Response
}
```
{% endswagger-response %}
{% endswagger %}

