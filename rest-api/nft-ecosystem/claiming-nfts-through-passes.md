---
description: >-
  [pounding on the desk] This is it! I'm telling you this is it! - Jeremy Irons
  (Margin Call)
---

# Claiming NFTs through Passes

### Overview

This feature extends the current Hedera capability by adding the concept of relationships between NFTs, a NFT pass can be a parent, while child NFTs can be linked for distribution to any holder. While the ledger automatically keeps state with no off-chain storage.

Or as a user story...

> As a project with an NFT pass, I want to be able to generate future NFTs that my community may be able to claim.

Or for an art project...

> As an artist I want to have an NFT pass to build a community with so I can reward my pass owners with future peridoic drops.

### How it works

There is a fair bit of logic to make this work, we rely on Mirrornodes to read currently minted NFTs and respective holders.

* Check that an account owns an NFT, or many.
* Check that the minted and supply of the child NFT matches the parent NFT pass.
* Check that a child NFT has been fully pre-minted.
* Check that the child NFT serial is held by treasury
* Attempt to send, or receive a generic association failure error.

{% swagger method="post" path="/api/nft/claim" baseUrl="https://hedera-serverless-consensus.vercel.app" summary="" %}
{% swagger-description %}
Enable an account to claim an NFT through a pass they own.
{% endswagger-description %}

{% swagger-parameter in="header" name="x-api-key" required="true" %}
The 

**API_SECRET_KEY**

 from the client's environment variables.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="token_id" required="true" %}
Hedera token id to send
{% endswagger-parameter %}

{% swagger-parameter in="body" name="receiver_id" required="true" %}
Hedera account to send the NFT to
{% endswagger-parameter %}

{% swagger-parameter in="body" name="serial_number" required="true" %}
Serial number of the NFT to send
{% endswagger-parameter %}

{% swagger-parameter in="body" name="nft_pass_token_id" required="true" %}
Hedera token id of pass to send
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

{% swagger-response status="422: Unprocessable Entity" description="Missing params, NFT or required treasury state for transfer" %}
```javascript
{
    // Response
}
```
{% endswagger-response %}
{% endswagger %}
