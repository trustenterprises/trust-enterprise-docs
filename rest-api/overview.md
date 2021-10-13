---
description: >-
  The REST API provides a number of resources to consume to check the status of
  your account, update topics and send messages for generate timestamp
  consensus.
---

# Overview

## Postman Documentation 

If you live and die by your love of Postman for API development, we provide a collection with examples that you can start using now. You'll need to create a new environment with fields for **domain **and **api_key**

[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/416758-2c026d8f-795d-48c7-8554-4bbc17f797ad?action=collection%2Ffork\&collection-url=entityId%3D416758-2c026d8f-795d-48c7-8554-4bbc17f797ad%26entityType%3Dcollection#?env%5BTrust%20Enterprises%5D=W3sia2V5IjoiZG9tYWluIiwidmFsdWUiOiJodHRwczovL2hlZGVyYS1zZXJ2ZXJsZXNzLWNvbnNlbnN1cy52ZXJjZWwuYXBwIiwiZW5hYmxlZCI6dHJ1ZX0seyJrZXkiOiJhcGlfc2VjcmV0X2tleSIsInZhbHVlIjoiMTIzNDU2NzhhYmMiLCJlbmFibGVkIjp0cnVlfV0=)

## **The Routes**

In all routes swap out the** **_**hedera-serverless-consensus.vercel.app **_for your URL.

### **Deployment Status**

Want to check the status of your client use **/api/status **remember to update **HIDE_STATUS **in your environment to **FALSE** if you want to hide this behaviour.

{% content-ref url="status.md" %}
[status.md](status.md)
{% endcontent-ref %}

### Account Balance

Fetch the current account balance connected to the deployment, useful for checking that the configuration of the deployed service is valid.

{% content-ref url="balance.md" %}
[balance.md](balance.md)
{% endcontent-ref %}

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



