---
description: >-
  Create a topic that automatically has a admin key set, only allowing for the
  serverless client to update them. You can a topic completely private for
  writes and updates and sending messages.
---

# Creating a new topic

{% api-method method="post" host="https://hedera-serverless-consensus.vercel.app" path="/api/consensus/topic/:id" %}
{% api-method-summary %}
Create new topic
{% endapi-method-summary %}

{% api-method-description %}
This endpoint will create a new topic that can be used to send messages to for a consensus timestamp. As this is an authenticated endpoint, **401** errors will be shown on incorrect authentication keys.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="x-api-key" type="string" required=true %}
The **API\_SECRET\_KEY** that is set in the clients environment.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="memo" type="string" %}
A memo that will be added to the topic, this can also be an escaped JSON string.
{% endapi-method-parameter %}

{% api-method-parameter name="enable\_private\_submit\_key" type="boolean" %}
Make sure that consensus messages can only be sent from the account that created the topic.
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Topic created with a memo.
{% endapi-method-response-example-description %}

```
{
    "data": {
        "memo": "topic memo information",
        "topic": "0.0.16091"
    }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=422 %}
{% api-method-response-example-description %}
This occurs if any of the variables are invalid for the API to process
{% endapi-method-response-example-description %}

```
{
    "errors": [
        "\"enable_private_submit_key\" must be a boolean"
    ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



