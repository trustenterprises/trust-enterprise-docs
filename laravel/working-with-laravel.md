---
description: >-
  Automatically capture the consensus trust timestamps in your local database,
  automatically using the webhook flow. Manage any trust process.
---

# Overview

[This Laravel package](https://github.com/trustenterprises/laravel-hashgraph) allows SaaS builders to integrate with distributed ledger technology, Hedera Hashgraph, at minimal effort and cost.

It is effectively **proof of anything** packaged up, for free, and with no overhead.

There are 2 methods to configure this package.

If you are just getting started with Trust Enterprises and you will use Laravel, [we recommend that you use this link](https://vercel.com/new/git/external?repository-url=https%3A%2F%2Fgithub.com%2Ftrustenterprises%2Fhedera-serverless-api&env=HEDERA_ACCOUNT_ID,HEDERA_PRIVATE_KEY,API_SECRET_KEY,HEDERA_NETWORK,WEBHOOK_URL&envDescription=Enter%20your%20account%20id%20and%20private%20key%20from%20the%20hedera%20portal.%20The%20API%20secret%20is%20your%20authentication%20key%20to%20communicate%20with%20your%20API%2C%20create%20a%20secure%20string%20of%20at%20least%2010%20characters.&envLink=https%3A%2F%2Fdocs.trust.enterprises%2Fdeployment%2Fenvironment-variables&redirect-url=https%3A%2F%2Fdocs.trust.enterprises%2Frest-api%2Foverview), which includes the **WEBHOOK\_URL** configuration when initially creating your client.

Alternatively, adding the **WEBHOOK\_URL** as a new environment variable in your project settings. You will have to **redeploy your client for the changes to take effect.**

> If you are testing locally use ngrok or localhost.run to create a tunnel to your local app.

![](../.gitbook/assets/screenshot-2020-10-13-at-13.43.04.png)

### A brief overview

A Laravel client library to automate adding webhooks, feeding the trust responses into your database automatically.

1. A fluent PHP API that communicates with the REST API.
2. Inbuilt database consensus table migrations that contain the bare bones of tables you need to have a stored log. 
3. The webhook flow will automatically store and validate all incoming consensus timestamp responses.
4. Custom events on insert events so that you may easily add additional logic if required.

## \*\*\*\*

