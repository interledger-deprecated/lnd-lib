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
const Lightning = new lndLib.Lightning({certPath, macaroonPath, lndAddress, protoPath});

```

* `[certPath]` Optional. Path to certificate. Defaults to `~/.lnd/tls.cert` on Linux and `~/Library/Application Support/Lnd/tls.cert` on Mac.  

* `[macaroonPath]` Optional. Macaroon Path. Defaults to `~/.lnd/admin.macaroon` on Linux and `~/Library/Application Support/admin.macaroon` on Mac.  

* `[lndAddress]` Optional. Lnd address. Defaults to `localhost:10009`. 

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
Lightning.connect({addr, pubKey, host, perm}).then((resp)=>{
 	.... 
})
```

* `[addr]` Optional. TODO..  

	*(need to either have `[addr]` or `[pubKey]` and `[host]`)*

* `[pubKey]` Optional. TODO..

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

`[addressType]`:

Either:

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
Lightning.openChannel(
	{
		nodePubkey,
		localFundingAmount, 
		pushSatoshis, 
		targetConf, 
		satoshisPerByte, 
		minHtlcMsat, 
		_private, 
		minHtlcMsat, 
		remoteCsvDelay
	},
	statusCallback
).then((resp)=>{
 	.... 
});
```

* `[nodePubkey]` TODO

*  `[localFundingAmount]` TODO
*  `[pushSatoshis]` Optional. TODO
*  `[targetConf]` Optional. TODO
*  `[satoshisPerByte]` Optional. TODO
*  `[_private]` Optional. TODO
*  `[minHtlcMsat]` Optional. TODO
*  `[remoteCsvDelay]` Optional. TODO
  
* `[statusCallback]` TODO


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

```
Lightning.addInvoice({amt}).then((resp)=>{
 	.... 
});
```

* `[amt]` TODO

#### decodePayReq
Decodes a payment request.

```
Lightning.decodePayReq({payReq}).then((resp)=>{
 	.... 
});
```

* `[payReq]` TODO

#### sendPayment
Sends a payment over Lightning.

```
Lightning.sendPayment({payReq}).then((resp)=>{
 	.... 
});
```

* `[payReq]` TODO


#### getChanInfo 
Returns the latest authenticated state for a particular channel.

```
Lightning.getChanInfo({chanId}).then((resp)=>{
 	.... 
});
```

* `[chanId]` TODO

#### closeChannel
Attempts to close an existing channel.

```
Lightning.closeChannel(
	{
		chanId, 
		channelPoint, 
		force, 
		targetConf, 
		satoshisPerByte
	}
).then((resp)=>{
 	.... 
});
```

* `[chanId]` TODO

* `[channelPoint]` TODO
* `[force]` TODO
* `[targetConf]` TODO
* `[satoshisPerByte]` TODO

#### disconnect
Disconnects from an existing peer.

```
Lightning.disconnect({pubKey}).then((resp)=>{
 	.... 
});
```

* `[pubKey]` TODO

## TODO:

Implement remaining lightning functionality.






