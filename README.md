# lnd-lib

[![Greenkeeper badge](https://badges.greenkeeper.io/interledgerjs/lnd-lib.svg)](https://greenkeeper.io/)

## Installation

Install the package via `npm`:

```
npm install install lnd-lib --save 
```

## Usage

```
const lndLib = require('lnd-lib');
const Lightning = new lndLib.Lightning(...args);

```

### Arguments

* `[certPath]` Optional. Path to certificate. Defaults to `~/.lnd/tls.cert` on Linux and `~/Library/Application Support/Lnd/tls.cert` on Mac.  

* `[macaroonPath]` Optional. Macaroon Path. Defaults to `~/.lnd/admin.macaroon` on Linux and `~/Library/Application Support/admin.macaroon` on Mac.  

* `[lndAddress]` Optional. Lnd address. Defaults to `localhost:10009`.  
* `[protoPath]` Optional. Path to `rpc.proto`. Defaults to `./rpc.proto` (included in this repo).



