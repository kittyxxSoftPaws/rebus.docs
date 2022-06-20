---
description: >-
  In this section, we will gear up your workspace for developing, deploying and
  enjoying smart contracts on Cosmos SDK.
---

# Smart Contracts Installation

{% hint style="info" %}
For developing complex smart contracts, you will likely want to run a full node on a testnet. See the validators section under [Joining Testnets](../validators/joining-the-testnets.md) for more information.
{% endhint %}

## Go

You can setup golang by following the [official documentation](https://github.com/golang/go/wiki#working-with-go). The latest versions of `rebusd` require go version `v1.16`.

## Rust

Assuming you have never worked with rust, you will first need to install some tooling. The standard approach is to use `rustup` to maintain dependencies and handle updating multiple versions of `cargo` and `rustc`, which you will be using.

## Installing Rust in Linux and Mac

First, [install rustup](https://rustup.rs/). Once installed, make sure you have the wasm32 target:

```bash
rustup default stable
cargo version
# If this is lower than 1.59.0+, update
rustup update stable

rustup target list --installed
rustup target add wasm32-unknown-unknown
```

## Installing Rust in Windows 10

{% hint style="info" %}
If working on a validator or a server, you should use Linux if possible. You will have a much better time...
{% endhint %}

First, download and execute `rustup-init.exe` from [rustup.rs](https://rustup.rs/) or [rust-lang.org](https://www.rust-lang.org/tools/install).

If requested, manually download and install Visual C++ Build Tools 2019, from [here](https://visualstudio.microsoft.com/visual-cpp-build-tools). Make sure "Windows 10 SDK" and "English language pack" are selected.

Continue running `rustup-init.exe`, and proceed with the installation.

Optionally:

* Download and install [gvim](https://www.vim.org/download.php#pc), and modify the Env vars to add \<gvim folder> to the PATH.
* Download and install [git for windows](https://git-scm.com/download/win). Modify the Env vars to add \<git folder>\bin to PATH.
* Turn on Developer Mode (Settings -> Update and Security: For Developers) and enable Device Discovery, to be able to [access the Windows 10 server through ssh](https://www.ctrl.blog/entry/how-to-win10-ssh-service.html#section-mssshserv-enable).

Install the wasm32 target:Copy

```bash
rustup default stable
cargo version
# If this is lower than 1.59.0, update
rustup update stable

rustup target list --installed
rustup target add wasm32-unknown-unknown
```

For those new to rust, the `stable` channel comes out every 6 weeks with a stable release.

## Building Rebus for testnet use

A testnet running [the Rebus chain](https://github.com/rebuschain/rebus.core) is usually in operation for you to test contracts on. Generally speaking though, it's quicker to work locally. See the local development setup instructions below.

Use go 1.17.x for compiling the `rebusd`executable if you are building from source. If you already are running a validator node, it's likely `rebusd` is already accessible. If `which rebusd` shows output, then you're probably good to go.

```bash
# clone rebus repo
git clone https://github.com/rebuschain/rebus.core.git && cd rebus.core

# get current testnet tag
git fetch --tags
git checkout v4.0.0

# build rebus executable
make build && make install

which rebusd
```

{% hint style="info" %}
If you have any problems here, check your `PATH`. `make install` will copy `rebusd` to `$HOME/go/bin` by default, please make sure that is set up in your `PATH` as well, which should be the case in general for building Go code from source.
{% endhint %}

## Getting started with writing contracts

There are two tutorials provided here in the docs, which will give you an overview of working with smart contracts and their basic functions. However if you are an experienced programmer wanting to immediately start writing CosmWasm contracts, then we recommend [working through their excellent tutorial](https://docs.cosmwasm.com/dev-academy/develop-smart-contract/intro).

## Running locally

Read this page for more information on running locally.

{% embed url="https://docs.rebusnetwork.io/development/rebusd-local-dev-setup" %}