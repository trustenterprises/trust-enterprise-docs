---
description: >-
  Create a topic that automatically has a admin key set, only allowing for the
  serverless client to update them. You can a topic completely private for
  writes and updates and sending messages.
---

# Creating a new topic

{% swagger baseUrl="https://hedera-serverless-consensus.vercel.app" path="/api/consensus/topic/:id" method="post" summary="Create new topic" %}
{% swagger-description %}
This endpoint will create a new topic that can be used to send messages to for a consensus timestamp. As this is an authenticated endpoint, 

**401**

 errors will be shown on incorrect authentication keys.
{% endswagger-description %}

{% swagger-parameter in="header" name="x-api-key" type="string" %}
The 

**API_SECRET_KEY **

that is set in the clients environment.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="memo" type="string" %}
A memo that will be added to the topic, this can also be an escaped JSON string.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="enable_private_submit_key" type="boolean" %}
Make sure that consensus messages can only be sent from the account that created the topic.
{% endswagger-parameter %}

{% swagger-response status="200" description="Topic created with a memo." %}
```
{
    "data": {
        "memo": "topic memo information",
        "topic": "0.0.16091"
    }
}
```
{% endswagger-response %}

{% swagger-response status="422" description="This occurs if any of the variables are invalid for the API to process" %}
```
{
    "errors": [
        "\"enable_private_submit_key\" must be a boolean"
    ]
}
```
{% endswagger-response %}
{% endswagger %}

