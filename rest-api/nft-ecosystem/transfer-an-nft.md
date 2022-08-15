---
description: Attempt a transfer of your NFT, from your treasury, to any account on Hedera
---

# Transfer an NFT

### Overview

This is the simplest of transfer methods the API can process, a couple of things will happen:

* We'll check that the Treasury owns and can send your NFT to an account
* We'll attempt to send the NFT to an account, if it fails then a error will query to whether an account has associated with said NFT id.

{% swagger method="post" path="/api/nft/transfer" baseUrl="https://hedera-serverless-consensus.vercel.app" summary="" %}
{% swagger-description %}
Transfer a specific NFT that the treasury owns to an account. 
{% endswagger-description %}

{% swagger-parameter in="header" name="x-api-key" required="true" %}
The 

**API_SECRET_KEY**

 from the client's environment variables.
{% endswagger-parameter %}

{% swagger-parameter in="body" required="true" name="token_id" %}
Hedera token id to send
{% endswagger-parameter %}

{% swagger-parameter in="body" name="receiver_id" required="true" %}
Hedera account to send the NFT to
{% endswagger-parameter %}

{% swagger-parameter in="body" name="serial_number" required="true" %}
Serial number of the NFT to send
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="NFT sent to account, you may check a mirrornode/explorer after 5- 10 seconds." %}
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

{% swagger-response status="422: Unprocessable Entity" description="Missing params or required treasury state for transfer" %}
```javascript
{
    // Response
}
```
{% endswagger-response %}
{% endswagger %}
