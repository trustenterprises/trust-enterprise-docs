---
description: Get the information for a given topic.
---

# Get topic info

{% api-method method="get" host="https://hedera-serverless-consensus.vercel.app" path="/api/consensus/topic/:id" %}
{% api-method-summary %}
Get topic information
{% endapi-method-summary %}

{% api-method-description %}
Get detailed topic information.  There is currently a development effort in checking that a topic exists before attempting to fetch a receipt.  
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The id of the topic
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="x-api-key" type="string" required=true %}
The value set as **API\_SECRET\_KEY** in the client's environment.
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Topic information received
{% endapi-method-response-example-description %}

```
{
    "data": {
        "topicMemo": "topic memo information",
        "runningHash": {
           ...
        },
        "sequenceNumber": 0,
        "expirationTime": {
            "seconds": 1606715551,
            "nanos": 990716007
        },
        "adminKey": {
           ...
        },
        "submitKey": {
           ...
        },
        "autoRenewPeriod": 7890000,
        "autoRenewAccount": null
    }

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

