---
description: >-
  Understand our process for building NFTs ecosystems completely through our API
  endpoints, from creation, minting, metadata creation, to advanced transfer
  features.
---

# NFT Ecosystem

We built out this feature on the API to answer one question...

### What if you could build your entire NFT ecosystem through an API?

Naturally, that would be really cool, we're not going to handle full blown image or media uploads by default, this is handled through [the tools provided by nft.storage](https://nft.storage/docs/quickstart/#uploading-files--directories-via-the-nftup-application), or [using NFTup](https://nft.storage/docs/quickstart/#uploading-files--directories-via-the-nftup-application) for directories.

But with that said, V2 of the API provided these additional features:

* NFT creation, with automatic royalty fees of 5%
* Simple NFT minting with batch built-in
* Metadata generation with strict validation based on the [HIP412 specification](https://hips.hedera.com/hip/hip-412)
* Mirrornode compatibility, with retryable logic, in case [nodes have throttled](https://docs.hedera.com/guides/mirrornet/hedera-mirror-node)
* NFT token transfers
* **Exclusive** NFT pass claiming functionality, for ensuring that community members that own a pass can always claim their project tokens with no off-chain storage requirements

All this of course as a simple REST API developer tool for any developer, at any skill level.

For interrogating NFT data during development we recommend using [Gomint's NFT explorer](https://gomint.me/explore/NFT/?tokenId=0.0.732556\&network=mainnet) or [Hashscan](https://hashscan.io/#/) before viewing assets in [Hashpack](https://www.hashpack.app/).

## Understanding the basic flow

Below is the flow to take to start creating NFTs through the API, we will go into more details in the corresponding pages:

### Create an NFT

An NFT can be created, before minting, to be viewable on hashgraph ledger.

{% content-ref url="create-an-nft-collection.md" %}
[create-an-nft-collection.md](create-an-nft-collection.md)
{% endcontent-ref %}

### Generate Metadata

Metadata is what we refer to a structure [that conforms to HIP412](https://hips.hedera.com/hip/hip-412), to ensure that it is processable for down-stream clients such as wallets like [Hashpack](https://www.hashpack.app/). Upon successful validation you will be provided a **CID** as a unique reference to an IPFS pin for minting NFTs.

{% content-ref url="generate-metadata.md" %}
[generate-metadata.md](generate-metadata.md)
{% endcontent-ref %}

{% hint style="info" %}
Based on feedback we might add metadata helpers for dealing with the output from mass images uploads through the tools provided through NFT storage.
{% endhint %}

### Mint an NFT

Minting a token with an amount and a CID, see above, you may also **batch mint 10** at a time if the CID you have used is the same

{% content-ref url="mint-an-nft.md" %}
[mint-an-nft.md](mint-an-nft.md)
{% endcontent-ref %}

### Transfer an NFT to an account

Lastly, you may transfer NFTs to an expected account, this is an attempted transfer and will check. If the treasury can send the NFT and will provide an additional general error if an account hasn't been associated with a given token.

{% content-ref url="transfer-an-nft.md" %}
[transfer-an-nft.md](transfer-an-nft.md)
{% endcontent-ref %}

### Claimable NFTs through Gated NFT passes

This is **our exclusive functionality** that enables projects to create NFT passes for their community and then automatically assign child tokens to their pool of NFT passes, through a fair claiming flow.

{% content-ref url="claiming-nfts-through-passes.md" %}
[claiming-nfts-through-passes.md](claiming-nfts-through-passes.md)
{% endcontent-ref %}



## Postman Documentation&#x20;

As before see the documentation in your local postman

[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/416758-2c026d8f-795d-48c7-8554-4bbc17f797ad?action=collection%2Ffork\&collection-url=entityId%3D416758-2c026d8f-795d-48c7-8554-4bbc17f797ad%26entityType%3Dcollection#?env%5BTrust%20Enterprises%5D=W3sia2V5IjoiZG9tYWluIiwidmFsdWUiOiJodHRwczovL2hlZGVyYS1zZXJ2ZXJsZXNzLWNvbnNlbnN1cy52ZXJjZWwuYXBwIiwiZW5hYmxlZCI6dHJ1ZX0seyJrZXkiOiJhcGlfc2VjcmV0X2tleSIsInZhbHVlIjoiMTIzNDU2NzhhYmMiLCJlbmFibGVkIjp0cnVlfV0=)
