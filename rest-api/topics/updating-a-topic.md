---
description: Update a topic with a different memo that is more suitable for your use case.
---

# Updating a topic

{% swagger baseUrl="https://hedera-serverless-consensus.vercel.app" path="/api/consensus/topic/:id" method="put" summary="Update a topic" %}
{% swagger-description %}
This endpoint allows you to update the memo of the topic, only from the original creator of the topic.
{% endswagger-description %}

{% swagger-parameter in="path" name="id" type="string" %}
The id of the topic.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authentication" type="string" %}
The 

**API_SECRET_KEY **

from the  client environment variables.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="memo" type="string" %}
The memo that you want to update the topic id to.
{% endswagger-parameter %}

{% swagger-response status="200" description="Cake successfully retrieved." %}
```
{
    "data": {
        "memo": "Updated memo",
        "topic_id": "16091",
        "accountId": {
            "shard": 0,
            "realm": 0,
            "account": 1156
        },
        "validStart": {
            "seconds": 1598827049,
            "nanos": 719000000
        }
    }
}
```
{% endswagger-response %}
{% endswagger %}

