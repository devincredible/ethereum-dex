# Ethereum DEX

A decentralized exchange built with smart contracts powered by Ethereum, enabling secure P2P trading between Ether and ERC-20 tokens with an order book system and real-time price charts.

## Table of Contents

- [Getting Started](#getting-started)
- [The Project](#the-project)
- [Resources](#resources)

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### The repository

First, you will need to `clone` or `fork` the repository into your Github account:

```
$ git clone https://github.com/devincredible/ethereum-dex.git
```

### Installing

First, you will need to install the dependencies with: `npm install`.

Run the following command in your terminal after cloning the main repo:

```
$ npm install
```

Then, you will need to install Truffle globally by running the following command int your terminal:

```
$ npm install -g truffle
```

### Running the Tests

First, you will have to compile the smart contracts by running the following command in your terminal:

```
$ truffle compile
```

Then you will have to install and run Ganache to run your blockchain locally:

https://www.trufflesuite.com/ganache

Then, the tests that validate your solution can be executed by runing the following
command:

```
$ truffle test
```

### Deployment on Local Blockchain

Deploy the contracts on your Ganache local blockchain by running the following command:

```
$ truffle migrate
```

### Seed your Local Blockchain

Run the following script create some transactions on your smart contracts (orders, trades...):

```
$ truffle exec scripts/seed-exchange.js
```

### Opening the User Interface

First of all, it is required to install Metamask wallet as a browser extension: https://metamask.io/

Then you should configure Metamask to connect to your local blockchain run by Ganache. This requires the following:

- Open Metamask
- Open the Network Configuration panel
- Open Custom RPC
- Configure your private network by adding `http://localhost:7545` on the URL and `1337` as a chain ID.
- Import the first Ganache Account to Metamask by copying the Account Private Key from Ganache and pasting it on Metamask

Finally you just need to run the following command in your terminal to open the User Interface:

```
$ npm start
```

### Deployment on Public Network

In order to deploy your smart contract, you must create your .env file and specify:

- `PRIVATE_KEYS` --> Private Key of the account you are using to deploy (typically the first one in the list of Ganache)
- `INFURA_API_KEY` --> API key provided by Infura: https://infura.io

Then, you will need to run the following command (let's use the testnet Ropsten in this example, remember to request some Ether for your account using a faucet):

```
$ truffle migrate --network ropsten
```

And also seed your exchange by running this command:

```
$ truffle exec scripts/seed-exchange.js --network ropsten
```

Finally you can run the following command to generate the build artifacts of your User Interface and then deploy to your favourite host:

```
npm run build
```

### Technology stack

- `Solidity`
- `React`
- `Truffle`
- `Web3.js`
- `Ganache`
- `Node.js`
- `Metamask`

## The Project

This project consists of a decentralized exchange to allow users to make P2P trades between Ether and ERC-20 tokens. It includes:

- Smart contracts for ERC-20 token implementation
- A decentralized exchange contract with comprehensive order and trade execution logic
- JavaScript-based test suite for contract validation
- React.js frontend application for user interaction

### Project architecture

The user can access the application via web-browser, and he must have the Metamask wallet installed. This interface, built with React.js, relies on the web3.js library to communicate with the smart contracts through Metamask. This means that the data reflected on the front-end application is fetched from the Ethereum blockchain. Each action performed by the user (put a a buy order, cancel order, execute a trade...) creates a transaction on Ethereum, which will require Metamask confirmation and pay an small fee, and this transaction will permanently modify the state of the Token and Exchange smart contracts.

### Exchange features

There are several sections which have different functionalities for the end user:

#### Balance

Here is where the user can deposit / withdraw Ether or ERC-20 tokens in the Exchange. It also reflects the balances, not only exchange balances but also wallet balances.

#### New Order

The user can place either a buy order or a sell order at a chosen price. This order will be placed in the Order Book as soon as the transaction is completed.

#### Order Book

Here the user can see all the orders placed. Also, the user can execute the trade by only clicking in a particular order in this Order Book.

#### Price Chart

The Price Chart reflects the token price via candlestick chart.

#### My Transactions

This reflects the activity done by the user who connected the Metamask. It shows the trades executed by the user and also the placed orders.

#### Trades

This section contains the full list of trades executed by any user in this decentralized exchange.

## Resources

- [ethereum.org](https://ethereum.org/)
- [truffle suit](https://www.trufflesuite.com/)
- [node.js](https://nodejs.org/)
- [web3.js](https://web3js.readthedocs.io/)
- [react.js](https://reactjs.org/)
