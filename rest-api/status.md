---
description: Get the current status of the deployed client
---

# Status

{% swagger baseUrl="https://hedera-serverless-consensus.vercel.app" path="/api/status" method="get" summary="Get Status" %}
{% swagger-description %}
This endpoint allows you to get the current status of the client, this information can be hidden by setting 

**HIDE_STATUS**

 in your environment variables.

\




\




**Note:**

 The 

**authenticationKey**

 could return as false if it is shorter then 10 characters.
{% endswagger-description %}

{% swagger-response status="200" description="The current status of the deployed client." %}
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
{% endswagger-response %}
{% endswagger %}

