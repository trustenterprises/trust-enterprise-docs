---
description: >-
  Create a hedera account for a user, this will provide you will the capability
  to send tokens to a user.
---

# Accounts



{% swagger baseUrl="https://hedera-serverless-consensus.vercel.app" path="/api/account/create/" method="post" summary="Create new account" %}
{% swagger-description %}
This endpoint allows you to create a user, you can then link the response **accountId** to an actor you have in your system.

You'll also receive an **encryptedKey** and **publicKey**, that you should store in your database.

The **encryptedKey** can be decrypted with your **API\_SECRET\_KEY.**
{% endswagger-description %}

{% swagger-parameter in="header" name="Authentication" type="string" required="true" %}
The 

**API_SECRET_KEY**

 from th e client's environment variables.
{% endswagger-parameter %}

{% swagger-response status="200" description="New account to link to a user" %}
```
{
    "data": {
        "accountId": "0.0.2838629",
        "encryptedKey": "4cc0ccd5446023a2:4e584643658b020a8b2fbfeceb293e00fdaf6cb41bdc3438379e6f6acbc4efeb516320e82b1d9102594f975f4b6ef8444f960017611035598297defb26b19b08a34e8f366639ee72bb265567b7f585597fd459eedfa8c1c6e40e68f439efff9a18f2ccd71cee260ea0f125c4aad730e2",
        "publicKey": "302a300506032b6570032100cebb39dbfc486ec10e6c415233f12572e2abd3d1ac3687308f1953deaef92643"
    }
}
```
{% endswagger-response %}
{% endswagger %}
