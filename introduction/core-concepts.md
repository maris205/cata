# For NFT!

At present, NFT is the hottest topic in the blockchain field, with very strong storage and query requirements, which also motivates and guides the design and development of CATA project.&#x20;

CATA has designed a set of interaction protocols for Flow's Cadence contract layer, enabling integration and full traceability of token transactions and data storage, providing a one-stop solution for NFT publishing, storage, management and distribution. It is fully compatible with Cadence's resource-oriented capabilities, allowing Cadence developers to easily connect NFT contracts to storage facilities.&#x20;

****:checkered\_flag: **The code of this part will be released soon as our first major milestone.**

## **NFT is more than just token**

_**The source data is the underlying assets of NFT, so it should be treated as a part of NFT.**_&#x20;

For the storage of the source data, the following requirements need to be met_**:**_

1. **Storage:** Data should be stored persistently, and be available all the time.
2. **Retrieval:** Data should always be ready for flexible retrieval. (e.g., I can search for all the movie NFTs starring Robert Downey Jr. …)
3. **Security:** Ownership and rights management & protection from malicious behaviors. (e.g., manipulation, piracy…).

## Challenges in NFT Storage

#### **The dilemma between Usability and Cost**

* On-chain storage is flexible in business logic, but with limitations of available space
* Decentralized storage scheme(e.g. IPFS) can hold massive data, but with weak interactivity

#### **Exhibition > Storage**&#x20;

* Most decentralized storage solutions are pure storage with no query capability

#### **Copy minter**

* No copyright protection in web world

## Full life-cycle solution for NFT storage on Flow <img src="../.gitbook/assets/flow.png" alt="" data-size="line">

The current NFT scenario relies on blockchain networks (e.g., Flow or ETH) to build a marketplace, and the storage of metadata often relies on centralized storage solutions (e.g., AWS), or the content is stored on a decentralized storage protocol (such as IPFS), and then is associated with the on-chain marketplace through additional operations, which brings a bad impact on the user experience of NFT. The CATA storage protocol spans from the circulation layer on blockchain, the Minerva metadata layer, to the underlying file system layer, and covers the business logic of NFT data storage, the associations between the on-chain and off-chain world, and the entire process of token circulation. It provides a one-stop NFT experience.

![Figure 1: the architecture of the CATA's solution for NFT storage](<../.gitbook/assets/image (10).png>)

![Figure 2: Data structures](<../.gitbook/assets/image (2).png>)

![Figure 3: Work flow](<../.gitbook/assets/image (14).png>)

****
