# Bitcore P2P

[![NPM Package](https://img.shields.io/npm/v/digibyte-js-p2p.svg?style=flat-square)](https://www.npmjs.org/package/digibyte-js-p2p)
[![Coverage Status](https://img.shields.io/coveralls/bitpay/bitcore-p2p.svg?style=flat-square)](https://coveralls.io/r/bitpay/bitcore-p2p?branch=master)

**The peer-to-peer networking protocol for DigiByte.**

`digibyte-js-p2p` adds [DigiByte protocol](https://en.bitcoin.it/wiki/Protocol_documentation) support for `digibyte-js`.

## Getting Started

```sh
npm install digibyte-js-p2p
```

In order to connect to the DigiByte network, you'll need to know the IP address of at least one node of the network, or use [Pool](./docs/pool.md) to discover peers using a DNS seed.

```javascript
var Peer = require('digibyte-js-p2p').Peer;

var peer = new Peer({host: '127.0.0.1'});

peer.on('ready', function() {
  // peer info
  console.log(peer.version, peer.subversion, peer.bestHeight);
});
peer.on('disconnect', function() {
  console.log('connection closed');
});
peer.connect();
```

Then, you can get information from other peers by using:

```javascript
// handle events
peer.on('inv', function(message) {
  // message.inventory[]
});
peer.on('tx', function(message) {
  // message.transaction
});
```

Take a look at this [guide](./docs/peer.md) on the usage of the `Peer` class.

## License

Code released under [the MIT license](LICENSE).

Copyright 2022 Renzo Diaz
Copyright 2013-2019 BitPay, Inc. Bitcore is a trademark maintained by BitPay, Inc.
