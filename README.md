# lnd-lib

[![Greenkeeper badge](https://badges.greenkeeper.io/interledgerjs/lnd-lib.svg)](https://greenkeeper.io/)

# Installation

Install the package via `npm`:

```
npm install install lnd-lib --save 
```
# Introduction

Draws heavily on <https://github.com/lightningnetwork/lnd/blob/master/docs/grpc/javascript.md>, and <https://api.lightning.community/>. 

# Usage

```
const lndLib = require('lnd-lib');
const Lightning = new lndLib.Lightning(args);

```

##### args:

`{certPath, macaroonPath, lndAddress, protoPath}`

* `[certPath]` Optional. Path to certificate. Defaults to `~/.lnd/tls.cert` on Linux and `~/Library/Application Support/Lnd/tls.cert` on Mac.  

* `[macaroonPath]` Optional. Macaroon Path. Defaults to `~/.lnd/admin.macaroon` on Linux and `~/Library/Application Support/admin.macaroon` on Mac.  

* `[lndAddress]` Optional. Lnd address. Defaults to `localhost:10009`. 
*  
* `[protoPath]` Optional. Path to `rpc.proto`. Defaults to `./rpc.proto` (included in this repo).

## Methods

#### initialize

Fetches certificate, rpc.proto etc. and creates sets up an RPC connection to LND.  

```
Lightning.initialize().then((resp)=>{
 	.... 
})
```
  
#### connect

Connects to another LND peer.

```
Lightning.connect(args).then((resp)=>{
 	.... 
})
```

###### args:

`{addr, pubkey, host, perm}`

* `[addr]` Optional. TODO..  

	*(need to either have `[addr]` or `[pubkey]` and `[host]`)*

* `[pubkey]` Optional. TODO..

* `[host]` Optional. TODO..  
* `[perm]` Optional. TODO..

  
#### getInfo
Returns basic information related to the Lightning node.
 
```
Lightning.getInfo().then((resp)=>{
	.... 
})
```


#### walletBalance 
Returns the wallet's balance (total utxos, confirmed and unconfirmed).

```
Lightning.walletBalance().then((resp)=>{
 	.... 
});
```


#### newAddress
Generates a new wallet address.

```
Lightning.newAddress(addressType).then((resp)=>{
 	.... 
});
```
###### addressType:
Optional. Either:

* `Lightning.addressType.p2wkh` or 

* `Lightning.addressType.np2wkh`. 

* Defaults to `Lightning.addressType.p2wkh` 



#### listPeers
Returns a list of all connected peers.

 ```
 Lightning.listPeers().then((resp)=>{
 	.... 
});
 ```

#### openChannel
Attempts to open a channel to an existing peer.
 
```
Lightning.openChannel(args,statusCallback).then((resp)=>{
 	.... 
});
```

###### args:

`{nodePubkey, localFundingAmount, pushSatoshis, targetConf, satoshisPerByte, minHtlcMsat, _private, minHtlcMsat, remoteCsvDelay}`

* `[nodePubkey]` TODO

*  `[localFundingAmount]` TODO
*  `[pushSatoshis]` TODO
*  `[targetConf]` TODO
*  `[satoshisPerByte]` TODO
*  `[_private]` TODO
*  `[minHtlcMsat]` TODO
*  `[remoteCsvDelay]` TODO

###### statusCallback:

TODO


#### channelBalance
Returns the total channel balance for all open channels.

```
Lightning.channelBalance().then((resp)=>{
 	.... 
});
```

#### listChannels
Returns a list of all open channels.

```
Lightning.listChannels().then((resp)=>{
 	.... 
});
```

#### addInvoice
Adds a new invoice, expressing intent for a future payment.

#### decodePayReq
Decodes a payment request.

#### sendPayment
Sends a payment over Lightning.

#### getChanInfo 
Returns the latest authenticated state for a particular channel.

#### closeChannel
Attempts to close an existing channel.

#### disconnect
Disconnects from an existing peer.

## TODO:

Implement remaining lightning functionality.






