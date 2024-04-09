# Substrate Learning

This is my local [Substrate](https://substrate.io/) node, used for learning Rust Smart contract development.

This marks the next step of my learning journey: I exploring the basics of Rust SC development and auditing.

The plan here remains similar: **_Sharing insights during the process of learning to solidify my knowledge and potentially help someone in the future._**

Having not delved deeply into Smart Contract development with Solidity beforehand, let alone auditing, I anticipate some initial struggles.

This is the [official page](https://docs.substrate.io/tutorials/), which offers valuable resources.

## Build a blockchain

### Overiew:

This section covers the basics of working with Substrate-based blockchain nodes.

Initially, the abundance of information may seem overwhelming and tedious (_it was for me_), but the tutorials are foundational and essential.

#### I) Build a local chain

This first tutorial lays the foundation for subsequent ones and is `100%` necessary. 

It provides instructions on starting the Substrate node locally and setting up the front-end template.

#### II) Simulate a network

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

#### IV) Authorize Specific Nodes

This is the first tutorial where you'll touch some Rust code, and I'd say it's a bit more complex.

I'd recommend doing this one, as it's your first hands-on experience with writing Substrate code—even if it's mostly copy and paste 😄

During this tutorial, the following concepts are covered:
-..
-..


#### V) Monitor node metrics
