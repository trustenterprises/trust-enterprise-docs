---
description: >-
  The REST API provides a number of resources to consume to check the status of
  your account, update topics and send messages for generate timestamp
  consensus.
---

# Overview

## Postman Documentation 

If you live and die by your love of Postman for API development, we provide a collection with examples that you can start using now. You'll need to create a new environment with fields for **domain** and **api\_key.**

[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/e61a0c42e7d572890996)

## **The Routes**

In all routes swap out the ****_**hedera-serverless-consensus.vercel.app**_ for your URL.

### **Deployment Status**

Want to check the status of your client use **/api/status** remember to update **HIDE\_STATUS** in your environment to **FALSE** if you want to hide this behaviour.

{% page-ref page="status.md" %}

### Account Balance

Fetch the current account balance connected to the deployment, useful for checking that the configuration of the deployed service is valid.

{% page-ref page="balance.md" %}

### Managing Topics

Create, update and get the info for a topic that you use to send your consensus messages to.

{% page-ref page="topics/" %}

### **Sending Consensus Messages**

Send a message to that you wish to get a trusted consensus timestamp for, you may provide an option for whether the message should be asynchronous or wait for finality to be reached.

{% page-ref page="consensus-messages.md" %}





