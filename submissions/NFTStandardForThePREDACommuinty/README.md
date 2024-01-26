I present an exclusive NFT standard for the PREDA community, offering the unique features:

This NFT standard is designed by leveraging PREDA's core features. It stores NFT information in the corresponding address states, enabling parallel processing when transferring different NFTs.

Each instance of an NFT contract is termed as a collection. Here, you have the flexibility to define general properties for NFTs, including the total supply and permissions for minting NFTs. The issuance number of each NFT can be individually set to accommodate various scenarios.

Furthermore, all NFTs share a common parameter, 'tradable,' determining their tradability. This feature essentially mirrors the functionality of SoulBound NFTs in Ethereum.

In my contracts, I've used PREDA's interface functions to define three types of NFTs: BaseNFT, ClaimableNFT, and BatchOperationableNFT. The PREDA community can also implement interfaces for these NFT types to meet their customization needs.

The BaseNFT contract provides fundamental abilities for transferring and authorizing. On top of that, the ClaimableNFT contract, as what its name suggests, adds the capability to claim NFTs.

Moreover, frequent scenarios in NFT usage involve batch transfer and airdrop. The BatchOperationableNFT contract enhances these functionalities on top of BaseNFT.

For your convenience, test scripts are available in the file folder.

Let's bring new excitement to the NFT world!






