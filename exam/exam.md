### University: ITMO University
### Faculty: FICT
### Course: Introduction to distributed technologies
### Year: 2022/2023
### Group: K4110c
### Author: Tretiakova Anastasia Vladimirovna

# Question 1: Параметры ERC20, примеры программного кода.

ERC-20 is a technical standard used to issue and implement tokens on the Ethereum blockchain. 
The ERC-20 standard makes it easier for developers to predict with more accuracy the interaction between different tokens and applications. It also defines how ERC-20 tokens are transferred within the Ethereum blockchain and how their respective supply and address balances are being consistently recorded. 
The ERC-20 gives developers a list of rules to follow, which enables seamless functioning within the larger Ethereum platform. Numerous decentralized applications (DApps) and services support ERC-20 tokens, making it easier for community members and businesses to adopt and use them on a wide range of applications (such as cryptocurrency wallets, decentralized exchanges, games, and so forth).
Although the majority of tokens on the Ethereum network follow the ERC-20 standard, there are some exceptions. Ether (ETH), for instance, was created before the standard and does not comply with it yet. This led to the creation of the so-called Wrapped Ether (WETH) - which is an ERC-20 token that represents Ether at a 1:1 ratio (1 WETH = 1 ETH). WETH allows users to trade their ETH to other ERC-20 tokens on decentralized exchanges.

6 main functions: 
* function totalSupply() public view returns (uint256) --total number of tokens in the contract
* function balanceOf(address _owner) public view returns (uint256 balance) --shows the balance of address tokens upon request
* function transfer(address _to, uint256 _value) public returns (bool success) --transfers tokens from one user to another, you need to specify the address of the recipient and the amount of the transfer.
* function transferFrom(address _from, address _to, uint256 _value) public returns (bool success) --Like transfer, but they do not have to be owned by the person accessing the contract.In other words, you can authorize another person or other contract to transfer funds on your behalf. Another use case involves automatic payment for subscription-based services.
* function approve(address _spender, uint256 _value) public returns (bool success) --can limit the number of tokens that a smart contract can withdraw from your balance
* function allowance(address _owner, address _spender) public view returns (uint256 remaining) --along with the approve function to check how many tokens he can still withdraw

There may also be others - name, symbol, and decimal, but they are not so important.
All of these functions work within the programming language that underlies Ethereum.

Contract ERC-20. It can be used to request a general token offer, check balances, transfer funds, and grant permissions to other DApps to manage tokens.
The main advantage of ERC-20 tokens is flexibility. Using them, you can also implement additional features and set certain parameters according to your needs.

Cade contract for issuing a token: https://github.com/masTechDeveloper/ERC20-Standard-Token

# Question 2: Экосистема Polkadot и ее архитектура. Типы и роли узлов в экосистеме.

Polkadot is a protocol that connects blockchains — allowing value and data to be sent across previously incompatible networks (Bitcoin and Ethereum, for example). The DOT token is used for staking and governance; it can be bought or sold on Coinbase and other exchanges. 

The Polkadot protocol is designed to allow unrelated blockchains to securely talk to each other, so that value or data can flow between. It’s also designed to be speedy and scalable, via the use of many parallel blockchains (or “parachains”) that take much of the processing demand off of the main blockchain.   

The Polkadot token (DOT) serves two main functions within the Polkadot network: it’s a governance token, which allows holders to have a say in the future of the protocol, and it’s used  for staking, which is the way the Polkadot network verifies transactions and issues new DOT. DOT can be bought and sold on exchanges like Coinbase as part of your investment strategy. 

The relay chain is responsible for achieving consensus and transaction delivery among parachains. Parachains are application-specific blockchains within the Polkadot network. Each parachain is an entire blockchain in and of itself, with its own logic and features.

Polkadot uses a proof-of-stake consensus mechanism (as opposed to the proof-of-work system Bitcoin uses) to secure the network, verify transactions, and create and distribute new DOT. There are several ways DOT holders can interact with staking system — depending on how much time, technical knowledge, and money they want to devote. 

Validators do the most work — it’s a major commitment, and requires technical knowhow. To become a validator, you need to run a node (one of the computers that makes up the network) with little to no downtime and stake a substantial amount of your own DOT. In exchange, you get the right to verify legitimate transactions, add new “blocks” of transactions to the relay chain, and potentially earn newly created DOT, a cut of transaction fees, and tips. (On the flip side, you can also forfeit some or all of your staked DOT for acting maliciously, making a mistake, or even having technical difficulties). 

Nominators allow regular investors to participate in staking indirectly. You can delegate some of your DOT to a validator you trust to behave according to the rules. In exchange, you get a cut of DOT earned by your chosen validators. Be careful with who you choose: you also can forfeit some of your stake if your validator breaks the rules.

There are also two specialized roles that typically require less of a commitment than becoming a full validator but more technical skill than is required to be a nominator: Collators keep track of valid parachain transactions and submit them to the relay chain validators. Fishermen help find and report bad behavior across the network. 

By staking and participating in the network via any of the above roles, you may be able to receive DOT rewards. DOT holders also have a say in the governance of the network and are able to vote on proposed software upgrades.