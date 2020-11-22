---
description: >-
  Send a consensus message to hedera through your API with the option of using
  webhooks for waiting synchronously for finality.
---

# Consensus Messages

{% api-method method="post" host="https://hedera-serverless-consensus.vercel.app" path="/api/consensus/message/" %}
{% api-method-summary %}
Create new consensus message
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to send a message to a topic id, you may simply broadcast the message, or wait for consensus to be reached using  **allow\_synchronous\_consensus.**   
  
If you are using testnet or mainnet environments there will be a **explorer\_url** property linking to an external hashgraph explorer for the given transaction.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authentication" type="string" required=true %}
The **API\_SECRET\_KEY** from th e client's environment variables.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="reference" type="string" required=false %}
A reference to an internal app idenitier so that after the response it will be easier to link.
{% endapi-method-parameter %}

{% api-method-parameter name="allow\_synchronous\_consensus" type="boolean" required=false %}
Wait for consensus to be finished to finality before receiving a response.
{% endapi-method-parameter %}

{% api-method-parameter name="topic\_id" type="string" required=true %}
The id of the topic you want to sent the message to.
{% endapi-method-parameter %}

{% api-method-parameter name="message" type="string" required=true %}
The string message that is sent to received a consensus response.
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
New message sent to a topic, using a **topic\_id** and **message.**
{% endapi-method-response-example-description %}

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
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

**WARNING**: if you have a **WEBHOOK\_URL** set in your client it is recommended that you **do not set** the **allow\_synchronous\_consensus** to false due to the implications of the NodeJS event loop with AWS Lambda.

