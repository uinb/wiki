# Core Features

If there is only one single word to summarize what Fusotao Protocol is, it is order matching verification. Fusotao is a verification protocol for order-book based matching systems, unlike trading on any other DEXs, the trading behaviors are never happened on-chain. Instead, the trading commands can be executed anywhere only if they are verifiable. Thus, users can trade their coins without bearing high latency and huge gas fees.

## Proof of Matching

Fusotao uses Sr25519 key-pair to represent an account. If you are already familier with the Polkadot, you must know that every account in Substrate-based chain is composed by two parts, the `free` and `reserved`.

In Fusotao Protocol, users can sign a `verifier#authorize` transaction to authorize some tokens to a registered DEX which is also represented by a ss58 address, then cause these tokens reserved. Once authorized, an associated event should be handled by the DEX. This step is just like transfering tokens to a CEX but the difference is that the ownership of tokens is still within the users' account and never transfered. To update the reserved balance, the DEX must prove that the modifications is valid. In another word, Fusotao Protocol can help users to get rid of human trust when trading on a order-book based platform. For more technical details, please read our [paper](https://www.fusotao.org/fusotao-greenbook.pdf).

[Galois](https://github.com/uinb/galois) is a sequential matching engine implementation reference, as well as the proving client of Fusotao Protocol. By using Galois, anyone can build a high-efficient matching system easily. If you are willing to run your own exchange service, please refer to the [Implement a Matching System Using Galois](/guide-to-implement-a-broker).

A validated proof submitted by provers will cause new $TAO generating by the protocol and distribute to the traders(the maker and taker). The specific amount of rewards depends on the total trading volume of current era(about 3 days, different from the era of block validation).

## Staking

Fusotao is an open network without any permissions, anyone can register as a prover by signing an on-chain extrinsic `verifier#register`. Before a registered prover can submit proofs, enough $TAO must be staked for it. Currently, in the [Fusotao Vodka Testnet](https://app.vodka.fusotao.org), it requires 80,000 $TAO to activate a prover.

As returns, the $TAO holders can earn transaction fees from the DEX they staking for. In the Vodka Testnet, the minimal staking amount is 100 $TAO.