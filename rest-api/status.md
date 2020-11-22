---
description: Get the current status of the deployed client
---

# Status

{% api-method method="get" host="https://hedera-serverless-consensus.vercel.app" path="/api/status" %}
{% api-method-summary %}
Get Status
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to get the current status of the client, this information can be hidden by setting **HIDE\_STATUS** in your environment variables.  
  
**Note:** The **authenticationKey** could return as false if it is shorter then 10 characters.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
The current status of the deployed client.
{% endapi-method-response-example-description %}

```
{
    "message": "Your environment status for your client",
    "environment_status": {
        "hederaAccountId": true,
        "hederaPrivateKey": true,
        "authenticationKey": true
    },
    "meta": {
        "hint": "Hide this status endpoint by setting \"HIDE_STATUS=TRUE\" in your environment"
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



