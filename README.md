# A substrate runtime module library (SRML) for Ethereum flavored WebAssembly (Ewasm) 

This project creates software for substrate-based blockchains to fully support the ewasm virtual machine and smart contracts. Ewasm, short for Ethereum flavored WebAssembly, is the next-generation on-chain execution engine for the Ethereum blockchains.

This project is funded by a [generous grant](https://medium.com/second-state/second-state-awarded-a-grant-to-bring-next-gen-ethereum-infrastructure-to-polkadot-ecosystem-6545fb2267fc) from the web3 foundation. You can [read more about the background here](https://medium.com/wasm/polkadot-is-getting-webassembly-based-ethereum-2-0-virtual-machine-from-second-state-dd2c3fd48f75). 

## Why

The Polkadot ecosystem needs on-chain smart contracts. The Substrate framework, which underlies blockchains in the Polkadot ecosystem supports Runtime Modules.

Runtime Modules are powerful, trusted code modules that must be installed and managed by node administrators. Similar code modules are called ABCI apps in Tendermint / Cosmos, and chaincode in Hyperledger.

Application developers do not want to create and manage a dedicated blockchain for each of their applications. Developers want to simply submit their code to the "cloud" and make them available as services.

On-chain virtual machines are ideally suited to provide a safe sandbox for user submitted untrusted code. 

## What

This project brings the next generation Ethereum virtual machine, known as the Ethereum flavored WebAssembly (Ewasm), into the Polkadot ecosystem. 

Building on top of the very popular WebAssembly technology, Ewasm is a high performance and flexible virtual machine for the future of the Ethereum ecosystem, and hence will be used by the majority of blockchain application developers. 

This project will bring Ethereum developers and applications into the Polkadot ecosystem, and expand the support for Ethereum protocol into Polkadot. 

## How

Key components and dependencies of this project include the following. 

1 A Solidity language compiler that supports the [Ethereum Environment Interface](https://ewasm.readthedocs.io/en/mkdocs/eth_interface/) (EEI). It creates EEI compatible host function calls in the generated bytecode to access the Ethereum system (ie account balances).

2 [A WebAssembly runtime and module](https://github.com/second-state/ssvm) that can handle EEI host function calls. It translates and passes the EEI calls as [EVMC](https://evmc.ethereum.org/) calls to the host blockchain environment. 

3 A Substrate host blockchain environment provides the Ethereum environment (ie the accounts) and returns values for the EVMC calls. 

4 The Substrate host blockchain environment also utilizes EVMC to start and manage the WebAssembly runtime when an incoming transaction requires execution of a smart contract. 

Implementing the EVMC-related functions (items 2-4) is the scope of this repository.



