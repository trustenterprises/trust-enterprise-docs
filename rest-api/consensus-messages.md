---
description: >-
  Send a consensus message to hedera through your API with the option of using
  webhooks for waiting synchronously for finality.
---

# Consensus Messages

{% swagger baseUrl="https://hedera-serverless-consensus.vercel.app" path="/api/consensus/message/" method="post" summary="Create new consensus message" %}
{% swagger-description %}
This endpoint allows you to send a message to a topic id, you may simply broadcast the message, or wait for consensus to be reached using 

**allow_synchronous_consensus.**

 

\


****

\


****

If you are using testnet or mainnet environments there will be a 

**explorer_url**

 property linking to an external hashgraph explorer for the given transaction.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authentication" type="string" %}
The 

**API_SECRET_KEY**

 from th e client's environment variables.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="reference" type="string" %}
A reference to an internal app idenitier so that after the response it will be easier to link.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="allow_synchronous_consensus" type="boolean" %}
Wait for consensus to be finished to finality before receiving a response.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="topic_id" type="string" %}
The id of the topic you want to sent the message to.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="message" type="string" %}
The string message that is sent to received a consensus response.
{% endswagger-parameter %}

{% swagger-response status="200" description="New message sent to a topic, using a topic_id and message." %}
```
{
    "data": {
        "reference": "my reference",
        "topic_id": "16091",
        "transaction_id": "0.0.1156@1598828456.197000000",
        "explorer_url": "https://ledger-testnet.hashlog.io/tx/0.0.1156@1598828456.197000000",
        "consensus_timestamp": {
            "seconds": 1598828466,
            "nanos": 501124002
        }
    }
```
{% endswagger-response %}
{% endswagger %}

**WARNING**: if you have a **WEBHOOK\_URL** set in your client it is recommended that you **do not set** the **allow\_synchronous\_consensus** to false due to the implications of the NodeJS event loop with AWS Lambda.
