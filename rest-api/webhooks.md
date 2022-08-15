---
description: >-
  Using webhooks provides a mechanism to be sent consensus responses from your
  client without having to wait for consensus. Currently in development.
---

# Webhooks

## Using webhooks in the deployment

In your Vercel deployment set **WEBHOOK\_URL** to the **POST** route that you wish to send all messages and redeploy your API.

{% hint style="info" %}
Make sure that your **POST** route **\*\*responds with the status code of** 200.\*\*
{% endhint %}

## Proving the source of messages

The concern of webhooks combined with trust is proving that the message came from the correct source.

In the request there will be a header including an **x-signature** this will be a **HMAC hash** of the body and the **API\_SECRET\_KEY** using the SHA256 algorithm.

To trust the source of the message you'll need to match the signature by creating a hash of the body and **API\_SECRET\_KEY** in your server and comparing.

{% hint style="info" %}
Without verifying the signature at this step you cannot be sure that the message you received is valid. Otherwise anyone that knew your webhook route could fake a consensus response.
{% endhint %}

## Example Webhook implementation

We provide an example webhook implementation that you can copy for your needs, this is found in the [postman documentation](https://www.getpostman.com/collections/e61a0c42e7d572890996) and the[ implemented handler is on github](https://github.com/trustenterprises/hedera-serverless-consensus/blob/master/app/handler/exampleWebhookHandler.js) for inspiration.

The route of the webhook for the project is **/api/webhook.**

To conform your webhook to our standards and testing mechanism the behaviour is as follows.

* The webhook will only respond to a **POST** request
* The webhook requires a **x-signature** in its header, this is a **HMAC SHA256** signature.
* The webhook is a valid signature of the entire payload body.

If the incorrect HTTP method is used to request the webhook the status code will be **405 (Method Not Allowed).**

If the **x-signature** cannot be verified with the payload a status code **400 (Bad Request)** will be returned.
