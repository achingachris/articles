---
title: "How to set up Rust and NEAR for Blockchain/Web3 Development"
datePublished: Wed Jun 08 2022 12:25:59 GMT+0000 (Coordinated Universal Time)
cuid: cl45ke5qw0027jznv1b5ra0al
slug: how-to-set-up-rust-and-near-for-blockchainweb3-development
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1654691126464/SaxrXg6XO.png
tags: ubuntu, rust, blockchain, web3, 2articles1week

---

[Near](https://near.org/) protocol is a decentralized application platform that gives developer-friendly features to build and develop smart contracts. 

Near offers the platform to build smart contracts in Rust and deploy them. By default, Near supports Rust and AssemblyScript. Rust is recommended for its greater developer experience when it comes to memory allocation and a minimal runtime, among [other great reasons](https://ink.substrate.io/why-rust-for-smart-contracts/).

## Installing Rust (Ubuntu/Linux)

To install Rust, follow the steps below:

### Install Curl

If you don't have curl installed, use the scripts below:

```shell
sudo apt update
sudo apt install curl
```

### Install Rust

To install Rust, paste and run the script below on your terminal:

```shell
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

Configure your shell using:

```shell
source $HOME/.cargo/env
```

To confirm a successful installation, run the following in a terminal:

```shell
rustup
```


![Screenshot from 2022-06-08 14-55-45.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1654689365450/CyP1W2Fgo.png align="left")


After that, run

```shell
sudo apt-get install build-essential
```

Add `wasm` target to your toolchain

```shell
rustup target add wasm32-unknown-unknown
```

To test out for the installation, create a simple `Hello, World!` program in rust:

On an empty folder create a file named: `main.rs` and add the following:

```rs
fn main() {
    println!("Hello, world!");
}
```

Save the file and compile the code using:

```shell
rustc main.rs
```

Run the simple program:

```shell
./main
```

If Hello, world! did print, congratulations! You have successfully installed Rust


![Screenshot from 2022-06-08 15-05-51.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1654689993225/8IDCvcmFw.png align="left")

## Installing `near-cli`

To install the`near-cli` simply use:

```shell
npm install -g near-cli
```

More on `near-cli` can be found [here](https://docs.near.org/docs/tools/near-cli).

## Conclusion
The post takes you through installing Rust and `near-cli` for blockchain development.

## Resources:

- [Near CLI](https://docs.near.org/docs/tools/near-cli)
- [Installing Rust](https://www.rust-lang.org/tools/install)

