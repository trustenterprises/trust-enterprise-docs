---
description: >-
  The REST API provides a number of resources to create marketplaces, consume to
  check the status of your account, update topics and send messages for generate
  timestamp consensus.
---

# Overview

## Postman Documentation&#x20;

If you live and die by your love of Postman for API development, we provide a collection with examples that you can start using now. You'll need to create a new environment with fields for **domain** and **api\_key**

[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/416758-2c026d8f-795d-48c7-8554-4bbc17f797ad?action=collection%2Ffork\&collection-url=entityId%3D416758-2c026d8f-795d-48c7-8554-4bbc17f797ad%26entityType%3Dcollection#?env%5BTrust%20Enterprises%5D=W3sia2V5IjoiZG9tYWluIiwidmFsdWUiOiJodHRwczovL2hlZGVyYS1zZXJ2ZXJsZXNzLWNvbnNlbnN1cy52ZXJjZWwuYXBwIiwiZW5hYmxlZCI6dHJ1ZX0seyJrZXkiOiJhcGlfc2VjcmV0X2tleSIsInZhbHVlIjoiMTIzNDU2NzhhYmMiLCJlbmFibGVkIjp0cnVlfV0=)

## **The Routes**

In all routes swap out the ** **_**hedera-serverless-consensus.vercel.app**_ for your URL.

## Build a token marketplace

A permissioned marketplace at your fingertips, link your users to tokens that you sell, without them having to touch or have any blockchain experience. &#x20;

### Create a token&#x20;

A token can be created to be linked to a frontend of a marketplace or online shopfront.

{% content-ref url="tokens/create-a-token.md" %}
[create-a-token.md](tokens/create-a-token.md)
{% endcontent-ref %}

### Create an account for a user

Every user is required to have an account in tokens to be sent.

{% content-ref url="accounts.md" %}
[accounts.md](accounts.md)
{% endcontent-ref %}

### Bequest a token to a user

Transfer a token that has been purchased to a user, the bequest feature manages all token associations by default so all you need to do is use this endpoint when ready, like verifying a payment.

{% content-ref url="tokens/bequesting-a-token.md" %}
[bequesting-a-token.md](tokens/bequesting-a-token.md)
{% endcontent-ref %}

## Confirm your deployment

### **Deployment Status**

Want to check the status of your client use **/api/status** remember to update **HIDE\_STATUS** in your environment to **FALSE** if you want to hide this behaviour.

{% content-ref url="status.md" %}
[status.md](status.md)
{% endcontent-ref %}

### Account Balance

Fetch the current account balance connected to the deployment, useful for checking that the configuration of the deployed service is valid.

{% content-ref url="balance.md" %}
[balance.md](balance.md)
{% endcontent-ref %}

## Manage topics and timestamped messages

Topics and messages allow you to add "trusted" proof that an event has happened.

### Managing Topics

Create, update and get the info for a topic that you use to send your consensus messages to.

{% content-ref url="topics/" %}
[topics](topics/)
{% endcontent-ref %}

### **Sending Consensus Messages**

Send a message to that you wish to get a trusted consensus timestamp for, you may provide an option for whether the message should be asynchronous or wait for finality to be reached.

{% content-ref url="consensus-messages.md" %}
[consensus-messages.md](consensus-messages.md)
{% endcontent-ref %}

##



