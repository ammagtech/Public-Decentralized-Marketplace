# Decentralized Marketplace

A decentralized marketplace package provides generic methods which helps with not only the connectivity but with the complete interaction with the blockchain. This package contains some generic methods which are being described below:

### `signMessage(message)`

Connection method of metamask which takes 'message' as parameter. It can be anything of a user, or a simple string which will show up on the connection popup on metamask.

### `mint(payload, contractAddress)`

To mint a NFT and give rights to the marketplace is a must to send it to the blockchain. Before Selling or Opening the NFT for bidding, it needs to be minted first. After minting, the data of that particular item can't be changed.

This method takes in 2 parameters. Lets talk about these:
'payload' is of array type which contains an object

 payload = [
              {
                to: ownerAddress,
                uri: ownerImage
                  ? ownerImage
                  : ownerAddress,
                tokenId: nftTokenId,
              },
            ];

'to' is a paramter which should have the ownerAddress of that item which is about to get minted to the blockchain. This field is of address type.
'uri' is basically a unique string of a user. It either takes the 'Image' string of the user or the Address as unique value(recommended is that address is being provided)
'tokenId' is the Id of that particular item. Its of integer type

'contractAddress' is the address of the contract. Look at the end of the documentation for info about contracts.


### `sellNftMarket(payload, contractAddress, payloadMarket)`

SellNftMarket has 2 smart contract methods:
1- approve
2- openMarketForFixedType

approve funtion approves the item first
openMarketForFixedType function opens the order of that particular item which is being approved. These function runs in a sequence 

sellNftMarket takes in 3 parameters:

payload = {
                approved: marketAddress,
                tokenId: nftTokenId,
          };

'approved' is basically the address of the market against which we are approving. More info about market address can be found at the end of the documentation.
'tokenId' is the Id of that particular item. Its of integer type

'contractAddress' is the address which has the sellNftMarket function. More info at the end of the documentation.

And finally we have this 'payloadMarket' as parameter which is an object


payloadMarket = {
                nftContractId: contractAddress,
                tokenId: nftTokenId,
                price: NewPrice,
              };

'nftContractId' is an address against which we are opening the order
'tokenId' is the Id of the item
'price' is the price at which we are opening the order. Its of integer type



### `buyNftMarket(payload)`

This method, by its name is a method for buying an item(which is being approved and sent to the blockchain first, basically the sellNftMarket method is being implemented on that item then we can buy it)

payload = {
            contractAddress: address,
            nftContractId: contractAddress,
            tokenId: nftTokenId,
            price: sellPrice,
          };

'contractAddress' is the parameter which contains the function buyNftMarket. Further info is provided at the end
'nftContractId' is the contractAddress of the user who is the owner of the item. 
'price' is the price of integer type at which the item is selling at.


### `cancelNft(payload)`

This method takes in payload object which. It is used to cancel the listing of the item from the blockchain.

contractPayload = {
          contractAddress: contractAddress,
          nftContractId: contractAddress,
          tokenId: nftTokenId,    
        };

'contractAddress' is the address which contains the cancelNft function
'nftContractId' is the address against which the item was approved and being put on the blockchain
'tokenId' is the Id of the item

### `openForAuction(payload)`

openForAuction has 2 smart contract methods:
1- approve
2- openMarketForAuctionType

approve funtion approves the item first
openMarketForAuctionType function opens the order of that particular item which is being approved and the bidding can be done on it. These function runs in a sequence 

openForAuction takes in 3 parameters:

payload = {
          nftContractId: contractAddress,
          tokenId: nftTokenId,
          minPrice: minAmount,
          maxPrice: maxAmount,
          contractAddress: address,
        };

'nftContractId' is basically the address of the market against which we are approving. More info about market address can be found at the end of the documentation.
'tokenId' is the Id of that particular item. Its of integer type
'minPrice' is the minimum amount which can be bid on the item
'maxAmount' is the maximum amount which can be bid on the item
'contractAddress' is the address which has the openMarketForAuctionType function. More info at the end of the documentation.

### `acceptBid(payload)`

openForAuction has 2 smart contract methods:
1- approve
2- openMarketForAuctionType

approve funtion approves the item first
openMarketForAuctionType function opens the order of that particular item which is being approved and the bidding can be done on it. These function runs in a sequence 

openForAuction takes in 3 parameters:

payload = {
          contractAddress: address,
          tokenId: nftTokenId,
          price: price,
          buyerAddress: buyerAddress,
          nftContractAddress: contractAddress,
        };

'contractAddress' is the address which has the acceptBid function. More info at the end of the documentation.
'tokenId' is the Id of that particular item. Its of integer type
'price' is the amount which is being bid on the item
'buyerAddress' is the address of the buyer
'nftContractAddress' is the address of the nft which has bid on




###  Addresses
WBNB => 0x6cfB4Daf6b2AbbfE7c0db97F0013bfB76E43D276
Custom MarketplaceNFT => 0xEdb8Ed342Fb457177F8e440F0924Df3964A51C63
lib Marketplace => 0x21795B124105b939d451cb713C83a4488A7A2a93

These are are list of addresses which contains all the BSC smart contract functions used in this package.

