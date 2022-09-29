---
description: >-
  There are a couple of requests you can use to check the balance of a given
  token for a given account or you can check if an account has a number of
  different tokens.
---

# Token Holdings and Balance

{% hint style="warning" %}
Remember, for a given call to check the account holdings or an individual balance you need to be aware whether an account ID is valid for a given environment. As an example, the amount of accounts on testnet far exceeds that of mainnet, thus you may receive errors if you try to pass an incorrect accounts into different environments.
{% endhint %}

This returns back to Balance for a given token that belongs to a given account, you can use this as an alternative to balance lookups on mirror nodes, if balance requests are critical.

{% swagger baseUrl="https://hedera-serverless-consensus.vercel.app" path="/api/account/:id/:token_id" method="get" summary="Get Token Balance" %}
{% swagger-description %}
This endpoint allows you to get the token balance of a given account for a particular environment.
{% endswagger-description %}

{% swagger-parameter in="path" required="true" %}
account id in 0.0.x format
{% endswagger-parameter %}

{% swagger-parameter in="path" name="token_id" required="true" %}
token id in 0.0.x format
{% endswagger-parameter %}

{% swagger-parameter in="query" name="decimals" type="Number" %}
Set the number of expected decimals
{% endswagger-parameter %}

{% swagger-response status="200" description="Account balance response" %}
```
{
    "data": {
        "balance": "10000"
    }
}
```
{% endswagger-response %}

{% swagger-response status="401" description="Will ask to include a api-key, if invalid will return with "Unable to validate with the supplied 'x-api-key'"" %}
```
{
    "reason": "Please set \"x-api-key\" in your header"
}
```
{% endswagger-response %}

{% swagger-response status="500: Internal Server Error" description="Known issue: Account ID is not valid" %}
```javascript
{
    // Response
}
```
{% endswagger-response %}
{% endswagger %}

Perhaps you just want to know whether an account holds particular tokens, this could be helpful if you are a building service that requires one or many tokens (like NFTs) to be held to unlock access to particular feature of your service.

{% swagger baseUrl="https://hedera-serverless-consensus.vercel.app" path="/api/account/:id/holdings/:token_ids" method="get" summary="Get Account Holdings" %}
{% swagger-description %}
This endpoint allows you to know if a given account holds many different tokens or NFTS.
{% endswagger-description %}

{% swagger-parameter in="path" required="true" %}
account id in 0.0.x format
{% endswagger-parameter %}

{% swagger-parameter in="path" name="token_ids" required="true" %}
token id in 0.0.x,0.0.y,0.0.z format
{% endswagger-parameter %}

{% swagger-response status="200" description="Account balance response" %}
```
{
    "data": {
        "balance": "10000"
    }
}
```
{% endswagger-response %}

{% swagger-response status="401" description="Will ask to include a api-key, if invalid will return with "Unable to validate with the supplied 'x-api-key'"" %}
```
{
    "reason": "Please set \"x-api-key\" in your header"
}
```
{% endswagger-response %}

{% swagger-response status="500: Internal Server Error" description="Known issue: Account ID is not valid" %}
```javascript
{
    // Response
}
```
{% endswagger-response %}
{% endswagger %}
