IN PROGRESS

# Solidity-NFT-Minting-Contract
This contract allows you to lazy mint a NFT collection on the Ethereum or Polygon blockchains.

With a few simple customization you will be able to deply this contract onto one of these networks so people can pay to mint your NFTs.

<h2>CUSTOMIZE</h2>

First you will need to customize the code to suit your project. Things you will need to decide:

- cost - What you want to charge for each NFT. Will be ETH or MATIC depending which chain you deploy on.
- maxMintAmount - The maximum number of NFTs the contract can produce.
- maxMintAmount - The max number of NFTs from your collection that can be minted per transaction
- numTokenOnDeploy - The number of NFTs you want to give yourself when you deploy the contract.
- owner1 and owner2 - The wallet addresses you want to send your portion of the NFTs to AND the wallets that get paid when you withdraw any funds used for purchase.

These are all in the initial contract variables (numTokenOnDeploy is in the contructor).
