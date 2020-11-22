---
description: Get the current account balance of the client
---

# Balance

{% api-method method="get" host="https://hedera-serverless-consensus.vercel.app" path="/api/account/balance" %}
{% api-method-summary %}
Get Account Balance
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to get the account balance of the client
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="x-api-key" type="string" required=true %}
The value set as API\_SECRET\_KEY in the client's environment.
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Account balance response
{% endapi-method-response-example-description %}

```
{
    "data": {
        "balance": "10000"
    }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}
Will ask to include a api-key, if invalid will return with "Unable to validate with the supplied 'x-api-key'"
{% endapi-method-response-example-description %}

```
{
    "reason": "Please set \"x-api-key\" in your header"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



