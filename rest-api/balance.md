---
description: Get the current account balance of the client
---

# Balance

{% swagger baseUrl="https://hedera-serverless-consensus.vercel.app" path="/api/account/balance" method="get" summary="Get Account Balance" %}
{% swagger-description %}
This endpoint allows you to get the account balance of the client
{% endswagger-description %}

{% swagger-parameter in="header" name="x-api-key" type="string" %}
The value set as API_SECRET_KEY in the client's environment.
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
{% endswagger %}

