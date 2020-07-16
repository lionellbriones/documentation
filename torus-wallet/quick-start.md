---
description: >-
  The iFrame wallet allows any application to seamlessly support their user's
  interactions with Ethereum (and similar EVM chains). OAuth logins,
  fiat-to-crypto and much more listed in features.
---

# Quick Start

## Integrate via:

### [npm package](https://www.npmjs.com/package/@toruslabs/torus-embed)

```markup
npm i @toruslabs/torus-embed
```

{% tabs %}
{% tab title="Basic" %}
```javascript
import Torus from "@toruslabs/torus-embed";
import Web3 from "web3";

const torus = new Torus();
await torus.init();
await torus.login(); // await torus.ethereum.enable()
const web3 = new Web3(torus.provider);
```
{% endtab %}

{% tab title="More Options" %}
```javascript
import Torus from "@toruslabs/torus-embed";
import Web3 from "web3";

const torus = new Torus({
  buttonPosition: "top-left" // default: bottom-left
});
await torus.init({
  buildEnv: "production", // default: production
  enableLogging: true, // default: false
  network: {
    host: "kovan", // default: mainnet
    chainId: 42, // default: 1
    networkName: "Kovan Test Network" // default: Main Ethereum Network
  },
  showTorusButton: false // default: true
});
await torus.login(); // await torus.ethereum.enable()
const web3 = new Web3(torus.provider);
```
{% endtab %}
{% endtabs %}

### Script Tag

The code snippet below sets Torus Wallet as the default login method for the DApp, paste the following script to the &lt;body&gt; of index.html.

```markup
<script src="https://cdn.jsdelivr.net/npm/@toruslabs/torus-embed"></script>
```

```markup
<script src="https://unpkg.com/@toruslabs/torus-embed"></script>
```

The script tag creates a `window.torus` object. You can initialize it and use it as above.

### IPFS

You can also choose in load the embed via IPFS

```markup
<script src="https://ipfs.io/ipfs/QmVrWpAivFzEN6GGerdURNXfssr5YpHjTtZopHHGQ6AHmU"></script>
```

## Examples

Please refer to the [examples](https://github.com/torusresearch/torus-embed/tree/master/examples) folder for sample implementations or the Class documentation for further init options.

## Web3/ether.js

Integrating with the Torus Wallet gives you a provider, which can be wrapped by the Web3. This instance functions similar to that as Metamask's web3 provider, and we have taken great care to make it compatible with Metamask's [Web3 APIs](https://web3js.readthedocs.io/en/1.0/).

## Development Environment

If you are developing with the Torus Wallet in a local environment/with ganache, https is necessary to interact with app.tor.us. Check out [the steps here](https://docs.tor.us/developing-with-torus/ganache) to get started.

In general, the Torus wallet integration only works in a secure browser environment, as it needs access to browser APIs like window.open and window.crypto.

