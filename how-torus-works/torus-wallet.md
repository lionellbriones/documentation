# Torus Wallet

To make our key management solution usable for DApps, we provide a Web3 interface that interfaces with an iframe that holds the private key for the user in a separate javascript context. All communications to nodes, third-party authentication servers, as well as message signing, are done in this separate javascript iframe context that is loaded on some [tor.us](https://tor.us) subdomain.

As such, Torus wallet consists of a javascript Web3 SDK \([torus-embed](https://github.com/torusresearch/torus-embed)\) and the site that is loaded in the iframe \([torus-website](https://github.com/torusresearch/torus-website)\).

## Integrity hashes

To ensure content integrity for the Torus wallet, all imported files in the Torus wallet are integrity hashed, and the resulting javascript SDK also has an integrity hash. We also go one step further to ensure that it's not possible for the Torus development team to modify the wallet after release by ensuring that the torus-embed SDK keeps an integrity hash of a particular static release of torus-website, and checks that the iframe's contents matches this integrity hash. As long as you do not update your installed version of the torus-embed javascript, even if the Torus team hosts a malicious version of torus-website, your torus-embed SDK will refuse to load it. We also use integrity hashes for our service workers to the same effect. Both of these are not currently natively supported by browsers at the moment but we use a fetch-validate-cache-and-load method to achieve this.

These integrity hashes help to ensure that the Torus wallet front-end cannot be freely modified by the Torus team post-release. All releases are versioned and will always be accessible at app.tor.us/vX.XX.XX.

## Popups

Unfortunately, modals are prone to clickjacking attacks. For security reasons, we have implemented all user confirmation screens as popups.

