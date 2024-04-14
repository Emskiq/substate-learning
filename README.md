# Substrate Learning

This is my local [Substrate](https://substrate.io/) node, used for learning Rust Smart contract development.

This marks the next step of my learning journey:  I am exploring the basics of Rust SC development and auditing.

The plan here remains similar: **_Sharing insights during the process of learning to solidify my knowledge and potentially help someone in the future._**

Having not delved deeply into Smart Contract development with Solidity beforehand, let alone auditing, I anticipate some initial struggles.

This is the [official page](https://docs.substrate.io/tutorials/), which offers valuable resources.

## Overview

Given the magnitude of these tutorials, I'll offer my opinion on which lessons should be completed and which ones can be skipped. A more in-depth review of each lesson follows in the next sections.

### Build a Blockchain
- [Build a local blockchain](https://docs.substrate.io/tutorials/build-a-blockchain/build-local-blockchain/) - Recommended.
- [Simulate a network](https://docs.substrate.io/tutorials/build-a-blockchain/simulate-network/) - Optional, but recommended.
- [Add trusted nodes](https://docs.substrate.io/tutorials/build-a-blockchain/add-trusted-nodes/) - Optional, but quick.
- [Authorize specific nodes](https://docs.substrate.io/tutorials/build-a-blockchain/authorize-specific-nodes/) - Recommended.
- [Monitor node metrics](https://docs.substrate.io/tutorials/build-a-blockchain/monitor-node-metrics/) - Skip.
- [Upgrade a running network](https://docs.substrate.io/tutorials/build-a-blockchain/upgrade-a-running-network/) - Recommended.

### Build Application Logic
- [Add a pallet to the runtime](https://docs.substrate.io/tutorials/build-application-logic/add-a-pallet/) - Recommended.
- [Specify the origin for a call](https://docs.substrate.io/tutorials/build-application-logic/specify-the-origin-for-a-call/) - Recommended.
- [Use macros in a custom pallet](https://docs.substrate.io/tutorials/build-application-logic/use-macros-in-a-custom-pallet/) - Recommended.
- [Add offchain workers](https://docs.substrate.io/tutorials/build-application-logic/add-offchain-workers/) - Skip.
- [Publish custom pallets](https://docs.substrate.io/tutorials/build-application-logic/publish-custom-pallets/) - Can be skipped, but quick.
- [Collectibles workshop](https://docs.substrate.io/tutorials/collectibles-workshop/) - Recommended for note-taking.
- 
### Build a Parachain

While the whole section contains minimal code, it is recommended to complete it for the new concepts and terminology that you will learn.

## Build a blockchain

This section covers the basics of working with Substrate-based blockchain nodes.

Initially, the abundance of information may seem overwhelming and tedious (_it was for me_), but the tutorials are foundational and essential.

### I) Build a local chain

This first tutorial lays the foundation for subsequent ones and is `100%` necessary. 

It provides instructions on starting the Substrate node locally and setting up the front-end template.

### II) Simulate a network

While this tutorial demonstrates simulating a private blockchain network with a set of private validators, it can be considered _optional_.

However it is a fast one, so _I suggest to not skip it_, maybe you would be granted with some knowledge that you have missed.

During exploration, I found myself delving into the CLI, which is used to start the node, for example:

```bash
./target/release/node-template purge-chain --base-path /tmp/alice --chain local
```

and discovered our favourite crate - [Clap](https://docs.rs/clap/latest/clap/)

### III) Add Trusted Nodes

Similar to the previous section, this can be skipped, but it's a quick one. However, if you're already familiar with the basic workflow of blockchain, I'd recommend skipping it.

Some concepts you might want to research on your own include:
- Key generation (SR and ED keys)
- Generating custom chain specifications
- Aura consensus

### IV) Authorize Specific Nodes

This is the first tutorial where you'll touch some Rust code, and I'd say it's a bit more complex.

I'd recommend doing this one, as it's your first hands-on experience with writing Substrate code—even if it's mostly copy and paste 😄

During this tutorial, the following concepts are covered:
- Peer ID and Account ID
- Compiling Rust code
- **Runtime** (important one)
- Dependencies (in `Cargo.toml`)
- `Config` trait

### V) Monitor Node Metrics

This tutorial can be easily skipped if you aren't interested in node metrics or setting up [Prometheus](https://prometheus.io/) endpoints linked with [Grafana](https://grafana.com/) UI.

While it's not a complete waste of time, if your focus is solely on development, you can skip it.

### VI) Upgrade a Running Network

This tutorial is important as it demonstrates how to upgrade your network while it's running.

Here, you'll utilize the [Sudo](https://paritytech.github.io/polkadot-sdk/master/pallet_sudo/index.html) and [Utility](https://paritytech.github.io/polkadot-sdk/master/pallet_utility/index.html) pallets.

> _There were some problems with the `utility` pallet. You can check my `runtime/Cargo.toml`_

This tutorial is relatively straightforward but essential. Pay attention while going through it.


## Build Application Logic

This section delves deeper into coding and Rust-related information. It serves as a basic introduction on how to integrate custom business logic through [pallets](https://docs.substrate.io/reference/frame-pallets/) (similar to Smart Contracts in Solidity).

For [Smart Contract development](https://docs.substrate.io/tutorials/smart-contracts/), you'll continue using the `substrate-node-template` that you've cloned and have been tinkering with since Lesson 1.

### I) Add a Pallet to the Runtime

This tutorial demonstrates a common method of adding a pallet to the [runtime](https://docs.substrate.io/learn/runtime-development/).

We'll be utilizing the [pallet_nicks](https://docs.rs/pallet-nicks/28.0.0/pallet_nicks/) crate, which allows for custom nicknames stored in the blockchain (similar to NFTs) by depositing a certain amount of crypto.

This tutorial sheds light on several important topics:
- [WebAssembly](https://wiki.polkadot.network/docs/learn-wasm) and `Cargo.toml` - providing insight into how Substrate handles the build process along with dependencies.
- `Config` trait - offering further in-depth information on this aspect.
- Adding a pallet to the runtime.

### II) Specify the Origin for a call

This tutorial is also crucial, so I highly recommend completing it.

It explains how to specify the originating account calling the functions exposed in the previous lesson (such as `set_name`, `clear_name`, etc.). It also covers concepts like:
- `ForceOrigin`, `RootOrigin`, `SignedOrigin` - defining the accounts capable of specific actions.
- `Sudo` events, `Sudid` - addressing error messages and their indexes in the dispatch.

### III) Macros in Custom Pallet

This tutorial introduces how to implement _your own custom logic_ for a pallet, specifically creating a simple Proof-of-Existence (POE) application.

For detailed instructions, refer to the [official lesson](https://docs.substrate.io/tutorials/build-application-logic/use-macros-in-a-custom-pallet/).

Concepts covered in this tutorial include:
- Setting up a custom pallet
- Basic pallet structure
- The `Config` trait
- Pallet `events`, `errors`, `storage`, and `callable functions`

### IV) Add Offchain Workers

This tutorial is skipped as it is outdated.

### V) Publish Custom Pallets

While not essential, this lesson demonstrates how to upload your custom logic using a simple git repository.

Though optional, I found it interesting as I didn't realize the process of exposing custom pallets was that straightforward.

### VI) Collectible Workshops

This page provides additional resources for further learning.

Personally, I plan to at least explore the provided resources. Who knows, there might be the next big thing that will spark my interest and keep me engaged in the future.

## Build a Parachain

This section focuses on moving beyond solo-chain development and introduces the concept of Parachains, one of the main features of [Polkadot](https://wiki.polkadot.network/docs/learn-parachains).

Note: I wouldn't say that the whole section is useless, but I definitely cannot see any immediate benefit in learning the concepts presented in the tutorials. What will be important, I believe, are the new concepts I have learned as well as all the new terminology.
