---
description: >-
  After receiving your Metadata CID you may mint an NFT, based on your
  collection,
---

# Mint an NFT

### Overview&#x20;

Minting an NFT to a collection is simple, only a **CID** from IPFS is required, however you may also batch your mints in sets of 10 if they use the same CID.

{% swagger method="get" path="/api/nft/:token_id/mint" baseUrl="https://hedera-serverless-consensus.vercel.app" summary="" %}
{% swagger-description %}
Mint an NFT to a collection, you may only mint in batches of 10, up to the limit of the collection.
{% endswagger-description %}

{% swagger-parameter in="path" name="token_id" required="true" %}
token_id of the nft collection
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-api-key" required="true" %}
The 

**API_SECRET_KEY**

 from the client's environment variables.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="cid" required="true" %}
IPFS CID that has been generated through the metadata route 
{% endswagger-parameter %}

{% swagger-parameter in="body" name="amount" type="int" %}
Default to 1, maximum batch mint of 10.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Token has been minted into collection" %}
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

{% swagger-response status="422: Unprocessable Entity" description="Missing CID from body" %}
```javascript
{
    // Response
}
```
{% endswagger-response %}
{% endswagger %}
