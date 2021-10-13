---
description: >-
  Send a token to an account that you have previously generated. This feature
  allows you to create decentralised experiences with onchain proof where a user
  requires no prior blockchain experience.
---

# Bequesting a token

{% hint style="warning" %}
This feature is in beta and there will be unexpected side effects if the body parameters aren't used.
{% endhint %}

{% swagger baseUrl="https://hedera-serverless-consensus.vercel.app" path="/api/token/bequest" method="post" summary="Send/bequest a token to an account" %}
{% swagger-description %}
This endpoint allows you to send a token to user as a permissioned function, provide the encrypted keys and ids of the receiver and token.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authentication" type="string" required="true" %}
The 

**API_SECRET_KEY **

from th e client's environment variables.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="encrypted_receiver_key" required="true" %}
Encrypted private key of receiver
{% endswagger-parameter %}

{% swagger-parameter in="body" name="token_id" required="true" %}
ID of token to send
{% endswagger-parameter %}

{% swagger-parameter in="body" name="receiver_id" type="String" required="true" %}
Account id of receiving account
{% endswagger-parameter %}

{% swagger-parameter in="body" name="amount" required="true" type="Number" %}
amount of tokens to send
{% endswagger-parameter %}

{% swagger-response status="200" description="Token sent to user" %}
```
{
    "data": {
        "amount": "1",
        "receiver_id": "0.0.2120537",
        "transaction_id": "0.0.1156@1634128052.72220023"
    }
}
```
{% endswagger-response %}

{% swagger-response status="422: Unprocessable Entity" description="Encrypted key too short" %}
```javascript
{
    "errors": [
        "\"encrypted_receiver_key\" length must be 241 characters long"
    ]
}
```
{% endswagger-response %}
{% endswagger %}
