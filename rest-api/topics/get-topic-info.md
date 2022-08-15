---
description: Get the information for a given topic.
---

# Get topic info

{% swagger baseUrl="https://hedera-serverless-consensus.vercel.app" path="/api/consensus/topic/:id" method="get" summary="Get topic information" %}
{% swagger-description %}
Get detailed topic information.  There is currently a development effort in checking that a topic exists before attempting to fetch a receipt.

\



{% endswagger-description %}

{% swagger-parameter in="path" name="id" type="string" %}
The id of the topic
{% endswagger-parameter %}

{% swagger-parameter in="header" name="x-api-key" type="string" %}
The value set as 

**API_SECRET_KEY**

 in the client's environment.
{% endswagger-parameter %}

{% swagger-response status="200" description="Topic information received" %}
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
{% endswagger-response %}
{% endswagger %}
