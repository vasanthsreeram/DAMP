# DAMP
Decentralised Autonomous Marketplace protocol

Centralised NFT Marketplaces such as Opensea and Rarible currently have issues such as high commission fees and censorship of certain NFTs. In order to prevent these issues, we propose DAMP to list, buy, and sell NFTs. There will be no one party controlling the marketplace with DAMP and as a result, commission fees and censorship of certain NFTs can be prevented. We utilise the Nano network in DAMP because Nano allows for feeless transfers and instant transactions. 

We have included a brief, yet detailed explanation of DAMP below. 
# Step 1: Minting of NFT

NFT Project owner chooses an NFT to list on DAMP. They then get the hash of the NFT using SHA256. The NFT Project's main Nano address must then send a micro-transaction to the Nano address with the same hash as the NFT. The micro-transaction also indicates the starting price of the NFT in ETH. 

<details>
<summary>How Nano address is created</summary>
    Source: https://github.com/alecrios/nano-address-validator/blob/master/README.md
</details>

# Step 2: Listing of NFT

DAMP finds NFTs by crawling owners’ Nano addresses and identifying the NFT hashes. Using the hash, it searches the NFTs on IPFS and lists the NFTs in the marketplace. 

# Step 3: Buying and Selling 

