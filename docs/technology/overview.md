# Important Concepts

The following is a reference list for commonly used and/or core concepts in Security Labs. For a more guided tour around out technology and theoretical concepts, visit [here](../#introduction) 
<!-- or our guide [...] TODO -->

## **Cryptographic token**
by <u>_cryptographic_</u> token we mean any piece of <u>_organized data_</u> which serves the purpose of singling out some <u>_property_</u> to just one entity (person, agent, etc; depending on the context), usually with **cryptographic guarantees** that it only belongs to that entity; i.e. cryptographic binding. 

For example, a private key in a [public-key cryptosystem](https://en.wikipedia.org/wiki/Public-key_cryptography) attributes the keyholder a unique ability to produce signed messages. The cryptographic binding here is the computational intractability of forging a signature if you're not the keyholder. The same applies to delegated signing keys or Decentrally generated keys. Cryptographic tokens are the basis for decentralizing identity, access control and operations in Web3, but are also the source of the trade-off between Web3 benefits and usability.

Not all cryptographic tokens needs to be decentralized, though: Simple username and password pairs on a centralized database are one example, since they give access control based on the central authority's backend rules to each specific user. Here we have binding which depends on the trust on said centralized party.

In general, we called them "cryptographic" since their structure <u>_hides information_</u> that allow asymmetric capabilities to the holders, and **losing them** means losing said capabilities.

## **Usability**
It's common to say that Web3 has an "onboarding" problem, referring to the process of bringing new users into some specific user experience, but frequently leaving aside the fact that, even if onboarded, dApps' user experience by itself is lacking proper polish. When we talk about _good usability_ on Security Labs, we refer to the property of a dApp to allow its users to operate without any special knowledge (about private keys, blockchain, tokens, etc.) with web2-like UX.

## **Key Management Abstraction**
Key Management Abstraction (KMA) let anyone store cryptographic tokens for later retrieval through simple and intuitive authentication interface to mitigate risk currently associated to private keys: 

1. **Loss risk**: Risk of losing your private key, losing in the process access to all associated assets.
2. **Theft risk**: Risk of your private key being held by another unintended person/agent, which could imply loss of assets or inappropriate use of identity, even if you still hold access to them yourself.
3. **Unavailability risk**: Risk of private key not being available in some specific dApp context, commonly when choosing a different browser or device.
4. **Usability risk**: Risk of getting users stuck on the dApp user-flow due to export/import or other managing aspects of the private key, commonly encountered when trying to use different devices or dApps with what could be interpreted by the user as "the same account", but really being subtly more complicated under-the-hood due to Web3's nature.

We abstract key management operations like private key storage and retrieval by expressing users' identities over a decentralized and permission-less infrastructure as a map between **intuitive authentication methods** (i.e. traditional web2 authentication, preferably biometrics, behavior-based and hardware-based) to **cryptographic tokens**.

## **State change authentication scheme**

Described more deeply and technically on our [whitepaper](https://docsend.com/view/dbk48wukd3ivd3ad), **State Change Authentication Schemes (SCAS)** is a family of authentication methods designed by Security Labs to fully describe how traditional authentication schemes can leverage decentralized systems properties to add a [decentralization-driven security](../overview#decentralization-driven-security) layer over intuitive UX to which users are already familiar. 

These provide an interface data structure called **State Change Authentication Token (SCAT)**, inside which general authentication information is stored mixed with a [cryptographic token](../overview#cryptographic-token) shard, allowing the network to pinpoint securely when to react to retrieval requests. Any authentication method, like traditional biometrics, hardware-based, password/pin-based, etc. can be used to interface with SCAS throught a SCAT to provide decentralized protection without jeopardizing already accepted user-experience.

## **State-Change Authentication Token**
Our own **cryptographic data-structure** in charge of holding **shares of cryptographic tokens** to be secured along with enough **authentication information** for observers (our network nodes) to authenticate users through a challenge-response procedure, verified distributively across several of them, **without jeopardizing** its contents.

Apart from the cryptographic token share, coming from a perfect-security splitting procedure and further secured, it contains standardized information about the authentication token (e.g. biometric data, hardware key, etc.) as a dynamical system's state space being evolved uniquely by said token, providing a general framework for time-distributed authentication methods (e.g. behavioral biometrics, on-chain identity, etc.). 

## **Decentralization-driven security**
Decentralization comes with several benefits, few obvious ones such as **data redundancy** and **integrity**, **robustness against some attacks** that would be very effective against **single points of failure**, etc. Nevertheless, its security (meaning, its resistance against behaving unexpectedly, given the effort of an adversary) is usually based solely on cryptographic primitives with **fixed security** levels given a **threat model** and **chosen parameters**.

This is by no means bad or weak in most cases, but it doesn't always scale naturally with the system size. Sometimes even on the contrary, scaling some networks can make them less secure by exposing more "weak links". When a system scales its security level along with its size, we call it **decentralizartion-driven security**, and it's a security property we designed our network to have.

## **Token Bound Accounts**
Token Bound Accounts, abbreviated TBA, are the result of a smart-contract-based strategy to append account functionality (assets holding and transferring) to Non-Fungible Tokens. This is done through a permission-less and owner-less registry contract which assign proxy interfaces for account operations when called (signed) by the NFT owner. 

This has several use cases such as:

1. **Dynamic Gaming Avatars**: ERC-6551-enabled NFTs in online multiplayer games serve as dynamic avatars, representing players' in-game achievements, items, and reputation within the gaming community. These avatars evolve as players progress, reflecting their growing reputation.
2. **Music Album NFTs**: Musicians release NFT albums that collectors can expand over time with new tracks. Reputation is based on the artist's recognition, track rarity, and collector engagement, such as reviews or recommendations.
3. **Digital Identity and Passports**: ERC-6551-backed NFTs serve as digital identity passports, accumulating reputation points based on online interactions, contributions to Decentralized Autonomous Organizations (DAOs), and participation in online events.
4. **DeFi Smart Profiles for Traders**: Traders use NFTs with ERC-6551 to create dynamic trading profiles, including historical performance and strategies. Other traders assess the reputation of these profiles to decide whether to buy strategies or collaborate.
5. **Decentralized Content Creation**: Content creators mint NFTs representing their work, such as articles or artwork. These NFTs accrue reputation points based on views, likes, and engagement, allowing users to co-create and personalize content.
6. **DAO Participation Badges**: NFTs with ERC-6551 are awarded to active participants in Decentralized Autonomous Organizations (DAOs). Holding these badges provides voting power and influence in decentralized governance.
7. **Airdrop Facilitation**: NFTs equipped with ERC-6551 facilitate efficient and targeted airdrops. Projects distribute tokens or assets based on reputation or community involvement, ensuring airdrops reach genuinely engaged users.
8. **Asset-Based Reward Systems**: NFTs with ERC-6551 enable asset-based reward systems for content creators or project contributors. Streaming rewards or revenue shares are sent directly to NFT-backed addresses, simplifying income distribution.
9. **Interoperable Reputation Scores**: ERC-6551 can be adapted for cross-chain functionality, allowing reputation and assets to flow seamlessly across different blockchain networks.
10. **Community-Based Governance**: NFTs representing governance tokens use ERC-6551 to enhance community-based decision-making processes. Users with higher reputation scores gain more influential voting power in decentralized governance.
11. **Trustworthy Identity Verification**: NFT-backed identities with ERC-6551 are used for trust verification across services and platforms, particularly valuable for Know Your Customer (KYC) processes.
