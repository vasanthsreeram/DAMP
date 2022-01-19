# Decentralised Autonomous Marketplace Protocol (DAMP)
Decentralised Autonomous Marketplace Protocol

Centralised NFT Marketplaces such as Opensea and Rarible currently have issues such as high commission fees and censorship of certain NFTs. In order to prevent these issues, we propose DAMP to list, buy, and sell NFTs. There will be no one party controlling the marketplace with DAMP and as a result, commission fees and censorship of certain NFTs can be prevented. We utilise the Nano network in DAMP because Nano allows for feeless transfers and instant transactions. 

We have included a brief, yet detailed explanation of DAMP below. 
# Step 1: Minting of NFT

NFT Project owner chooses an NFT to list on DAMP. They then get the hash of the NFT using SHA256. The NFT Project's main Nano address must then send a micro-transaction to the Nano address with the same hash as the NFT. The micro-transaction also indicates the starting price of the NFT in ETH. 

<details>
<summary>How the Nano address is created with the hash</summary>
    <details>
        <summary>Details on the Nano Address Format</summary>
        nano3t6k35gi95xu6tergt6p69ck76ogmitsa8mnijtpxm9fkcm736xtoncuohr3 
        └─┬─┘└────────────────────────┬─────────────────────────┘└──┬───┘
        A                             B                             C.
        A ---> Prefix - An address must begin with either nano (modern prefix) or xrb (legacy prefix).
        Because Nano was originally named RaiBlocks, the prefix xrb was used (the x denoting a non-national currency, per the ISO 4217 currency code standard). After rebranding, the nano_ prefix was introduced. As of Nano Node v19, the legacy prefix is deprecated, though it will continue to be supported.
        B ---> Public Key - An address must contain a 52-character encoded public key, which begins with either 1 or 3.
        A raw address is a 256-bit unsigned integer in hexadecimal format. This is translated into a 260-bit number (padded at the start with four zeros) and encoded into a human-friendly string using a special base32 algorithm. This algorithm divides the 260-bit number into 52 5-bit segments and maps each segment to a character in an alphabet (13456789abcdefghijkmnopqrstuwxyz) that omits characters easily confused for others (02lv). Because the first segment is padded with zeros, its pattern is either 00000 (1) or 00001 (3). Thus, the encoded public key always begins with one of those characters.
        C ---> Checksum - An address must contain an 8-character encoded checksum of the public key.
        The address contains a checksum of the public key in order to prevent typographical errors. A hash is generated from the unencoded public key using Blake2b with an 8-bit digest, which is then encoded using the same base32 algorithm as the public key and appended to the address. Thus, the final 8 characters of an address must match the derived checksum of the public key.
        <a href="https://github.com/alecrios/nano-address-validator/blob/master/README.md">Source<a> 
    </details>
    By using the Nano Address format, we can encode the IPFS file hash into the B portion of the address. This wallet can be used to store the owner details of this specific NFT that is linked to on the IPFS.
    
</details>

# Step 2: Listing of NFT

DAMP finds NFTs by crawling owners’ Nano addresses and identifying the NFT hashes. Using the hash, it searches the NFTs on IPFS and lists the NFTs in the marketplace. 

# Step 3: Buying and Selling 

Once the NFT is listed buyers would want to start bidding on the NFT. They will send the amount they promise and a key from a pre-generated transaction key pair. 
Once the NFT has been transferred, the buyer’s wallet will send the encoded amount with the hash key to the image wallet.
The seller then validates the transaction by sending the encoded amount and response hash key to the image wallet. 
This keypair exchange will be proof of new ownership in the Nano network. 

A good analogy is that the encoded amount sent by the buyer is him handing the money to the seller, and the seller’s encoded amount sent to the image wallet is the seller taking the money and putting it into his pocket. 

This ensures the trustless nature of the protocol.

<details>
<summary>Hashing for the Transaction keys</summary>
    <a href="https://en.wikipedia.org/wiki/Pearson_hashing">Pearson Hashing<a> is used to obtain the hash for the transaction as it is light and only takes up 8bits.
    The verification can be done for a given transaction by applying the pearson hashing algorithm on the seller's transaction hash to obtain the buyer's hash.
</details>
