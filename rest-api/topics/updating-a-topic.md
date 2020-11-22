---
description: Update a topic with a different memo that is more suitable for your use case.
---

# Updating a topic

{% api-method method="put" host="https://hedera-serverless-consensus.vercel.app" path="/api/consensus/topic/:id" %}
{% api-method-summary %}
Update a topic
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to update the memo of the topic, only from the original creator of the topic.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The id of the topic.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authentication" type="string" required=true %}
The **API\_SECRET\_KEY** from the  client environment variables.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="memo" type="string" required=false %}
The memo that you want to update the topic id to.
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Cake successfully retrieved.
{% endapi-method-response-example-description %}

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
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



