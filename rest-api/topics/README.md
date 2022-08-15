---
description: >-
  Manage topics for sending consensus messages to the client. You may create,
  update and read the information of a given topic.
---

# Topics

## Topic routes

There are 3 routes that help to manage a given topic before sending consensus messages. The focus is that if you have a particular group of users or a particular app that you wish to have a separate topic to keep track of messages you can do so with different topics.

{% hint style="info" %}
Please note that currently the creation of new topics automatically set the admin key to be the public key of the account of the deployed client. This means that a topic may only be updated by that account, the memo can only be changed.
{% endhint %}

All routes required authentication through the **x-api-key** and a escaped JSON value can be injected into the memo to hold more information about the topic.

### Get topic info

Get the topic information using a supplied **topic\_id.**

{% content-ref url="get-topic-info.md" %}
[get-topic-info.md](get-topic-info.md)
{% endcontent-ref %}

### Create new topic

Create a topic with 2 optional values, the **memo** or the **enable\_private\_submit\_key** which stops any other account to successfully sent a consensus message to the topic.

{% content-ref url="creating-a-new-topic.md" %}
[creating-a-new-topic.md](creating-a-new-topic.md)
{% endcontent-ref %}

### Update a current topic

Update the memo of a given topic by providing a **memo** property to the body.

{% content-ref url="updating-a-topic.md" %}
[updating-a-topic.md](updating-a-topic.md)
{% endcontent-ref %}

