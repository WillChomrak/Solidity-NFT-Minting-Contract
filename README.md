IN PROGRESS

This README assumes you have the Metamask Wallet extension installed in your browser. I will explain the code with the intention that it will be used on the Polygon network, but it will work exactly the same on Ethereum and the Ethereum network. 

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

<h2>COMPILE</h2>

We are going to deploy this contract using the remix IDE. I experimented with Brownie for Python and it seemed like a useful package for smart contracts but I found Remix to be much simpler. Go to https://remix.ethereum.org/. You can past the NFT-Minter.sol code right into the IDE. Click throught the tabs on the left side menu. We will be using the "Compile" and "Deploy" tabs. Click into the Compile tab. Make sure that in the contract selection drop-down "NFT-Minter.sol" is selected (for me it was defaulting to "Ownable.sol") and click the big Compile button.

Tip: Open up a txt doc for storing some data we are going to need later. Scroll down to the bottom of the Solidity Compiler left-hand sidebar. Click on the little Copy ABI button and paste this into your text doc. If you plan on verifying your contract or if you plan on making the Web3 enabled minting website (code coming soon) you will need this.

<h2>DEPLOY</h2>

Click into the "Deploy" tab on the left-hand menu. Set the Environment drop-down to "Injected Web3". This will then open up your Metamask and ask for you to sign-in. Set your Metamask network to "Polygon Mainnet". Connect the Metamask account that you wish to be "owner1" in the contract to Remix. Ensure you've got some MATIC in that wallet. After connecting the right account to Remix you should see the public key for that wallet in the "Account" drop-down back in the "Deploy & Run Transactions" left-hand menu. Ensure that account is selected. Select the "NFT-Minter.sol" contract in the Contract drop-down. 

Now you are almost ready to click the "Deploy" button. In order to deploy this contract you will need to set the \_name, \_symbol, \_initBaseUri, and numTokenCreate. You will see a accordion menu apear beneath the Deploy button, this will give you four text fields to submit these four items. The \_name and \_symbol are the name and symbol for the collection, these will be read by exchanges. numTokenCreate is simply the number of tokens you want sent to each of the owner1 and onwer2 wallet addresses when the contract deploys.

\_initBaseUri is VERY IMPORTANT. This is the CID address from the metadata directory you uploaded to Pinata using my Python-NFT-Collection-Generator repository instructions. If you do not enter this EXACTLY your smart contract will not be connected to your NFT artwork. You must type "ipfs://<YourCID>". Cut "<YourCID>" and replace it with your actual CID. Your CID can be found in your Pinata account. Remember it is the CID for your metadata directory, not for your images directory.
  
Once you have entered all 4 constructor parameters correctly - click that deploy button. Metamask will once again ask for your confirmation and this time will charge you for the transaction. Once deployed, you will see your new contract under the "Deployed Contracts". Click the arrow to expand and interact with it.
 
Tip: Copy the contract address and paste it at the top of that same txt doc when you pasted your contract ABI.

Congratulations! You've successfully deployed your contract! You should have some cool new NFTs in your Metamask wallet. (You have to "Import Token" before they apear in your wallet. If you don't know how to do this a quick Google search will show you)
  
You should now be able to see your NFTs on Opensea.io! Head over to the website and log in with the same wallet address you used to deploy your contract. If can take some time before Opensea loads the images and metadata, but your should be able to see the contract and number of tokens you own right away. Great!

This is cool, but how do can people buy your NFTs? Next I'm going to post the code for a fully functioning Web3 enabled React website for you to make some sweet sales!
