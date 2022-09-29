---
description: Manage tokens through minting and sending to your users.
---

# Tokens

### Understanding Tokens

On Hedera tokens are managed through SDKs, this API wraps the NodeJS SDK and allows any developer or individual exploring nocode applications a simple entry point to get started.

{% hint style="info" %}
Currently the API is opinionated with sane defaults to make everything super simple, but feel free to extend and modify the API code to meet whatever needs you require for your usecase.
{% endhint %}

We are just focused on minting and sending/bequesting of tokens to a user, in a permissioned setting. Imagine a scenerio where your users don't have experience with blockchain but you need a UX that is as friendly as possible for everyone.

For the developers out there I recommend digging into the API code and changing the behaviour as you see fit, the architecture and testing suite of the API is strong and delivers an incredible foundational layer.

{% hint style="info" %}
[Release 2.2.0](https://github.com/trustenterprises/hedera-serverless-api/releases/tag/2.2.0) finally adds support for explicitly setting external token decimals instead of relying on defaults 😅
{% endhint %}

### Minting Tokens

A token can be created to be linked to a frontend of a marketplace or online shopfront.

{% content-ref url="create-a-token.md" %}
[create-a-token.md](create-a-token.md)
{% endcontent-ref %}

### Bequesting/Sending Tokens

Transfer a token that has been purchased to a user, the bequest feature manages all token associations by default so all you need to do is use this endpoint when ready, like verifying a payment.

{% content-ref url="bequesting-a-token.md" %}
[bequesting-a-token.md](bequesting-a-token.md)
{% endcontent-ref %}
