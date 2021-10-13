---
description: Create a token with a name, symbol, supply, and memo.
---

# Create a token

{% swagger baseUrl="https://hedera-serverless-consensus.vercel.app" path="/api/token" method="post" summary="Create new token" %}
{% swagger-description %}
This endpoint allows you to create a token with a name, symbol, supply, and memo. 

The memo is an important feature to allow linking but not exclusive to: Hedera Topic IDs (dynamic NFTs), decentralised identity (DIDs), or IPFS (dStorage) images/files.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authentication" type="string" required="true" %}
The 

**API_SECRET_KEY **

from th e client's environment variables.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="symbol" required="true" %}
Symbol of the token
{% endswagger-parameter %}

{% swagger-parameter in="body" name="name" required="true" %}
Name of the token
{% endswagger-parameter %}

{% swagger-parameter in="body" name="supply" type="Number" required="true" %}
Number of tokens to mint, whole.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="memo" %}
Attached memo to a token, for linking to external content or for dynamic NFT purposes.
{% endswagger-parameter %}

{% swagger-response status="200" description="New token that has been minted, capability to send to send to accounts." %}
```
{
    "data": {
        "name": "Matt token",
        "symbol": "MATT",
        "memo": "abc",
        "reference": "basic.fungible",
        "supply": "100",
        "supplyWithDecimals": "100000000",
        "tokenId": "0.0.2839273"
    }
}
```
{% endswagger-response %}
{% endswagger %}
