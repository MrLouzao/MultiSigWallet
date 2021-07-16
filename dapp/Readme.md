Ethereum Multisignature Wallet UI
===================

A web user interface for the [MultiSigWallet](https://github.com/gnosis/MultiSigWallet).

Requirements
-------------
* Node v8 (Confirmed working on v8.17.0 - will not work on current LTS v12.13.0)
* [Grunt-cli](http://gruntjs.com/getting-started#installing-the-cli)

Install
-------------
```
# For Ubuntu/Debian you need to install libusb development headers
apt install -y libusb-1.0-0-dev

# Latest NodeJS (v16) does NOT appear to work correctly.
# You should use NVM and install Node v8.17.0 for best results: https://github.com/nvm-sh/nvm
# Tested by @louzao on 2021-Jul-16 with v8.17.0 with success
nvm install v8.17.0

git clone https://github.com/gnosis/MultiSigWallet.git
cd MultiSigWallet/dapp

# node-gyp is required for 'npm install' to work correctly
npm install -g node-gyp@4.0.0

npm install -g grunt-cli@1.3.2
npm install arr-flatten@1.1.0
npm install
```

@Vogelito recommened to use the version 10 for Node but the Desktop application crashes using a higher version than 8.17.0
due to NODE_MODULES version and library ethereumjs-wallet.

To run development **browser** mode:

```
grunt
```

To run development in **Desktop** (Electron) mode:

```
npm run start-electron
```


Detected issues when using npm install
-------------

When using NPM install, make sure that you are running the proper version of node. If not, problems can arise.

Potential issue detected on package-lock.json is one related to bignumber.js dependency, in which the package-lock.json
appends the dependency name as a preffix of the dependency as follows:

```
"bignumber.js": "bignumber.js@git+https://github.com/debris/bignumber.js.git#94d7146671b9719e00a09c29b01a691bc85048c2",
```

The first part of the URL should be removed to get a successful compilation.The final package-lock.json should be as follows:

```
"bignumber.js": "git+https://github.com/debris/bignumber.js.git#94d7146671b9719e00a09c29b01a691bc85048c2",
```

Replace for all bignumber coincidences.


Test
-------------
```
npm install -g ganache-cli@6.4.3

npm test
```

Build
-------------

Web version

```
npm run build-libs-web
```

Desktop version

```
npm run build-libs-electron
```
