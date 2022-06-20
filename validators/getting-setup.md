---
description: Instruction to install the rebusd binary
order: 1000
---

# Rebusd Installation and setup

## Choose an Operating System

The operating system you use for your node is entirely your personal preference. You will be able to compile the `rebusd` daemon on most modern linux distributions and recent versions of macOS.

{% hint style="info" %}
For the tutorial, it is assumed that you are using an Ubuntu LTS release.

If you have chosen a different operating system, you will need to modify your commands to suit your operating system.
{% endhint %}

## Install pre-requisites

```bash
# update the local package list and install any available upgrades
sudo apt-get update && sudo apt upgrade -y

# install toolchain and ensure accurate time synchronization
sudo apt-get install make build-essential gcc git jq chrony -y
```

## Install Go

Follow the instructions [here](https://golang.org/doc/install) to install Go.

For an Ubuntu LTS, you can probably use:

```bash
wget https://golang.org/dl/go1.17.1.linux-amd64.tar.gz
sudo tar -C /usr/local -xzf go1.17.1.linux-amd64.tar.gz
```

Please install Go v1.17 or later.

Unless you want to configure in a non standard way, then set these in the `.profile` in the user's home (i.e. `~/`) folder.

```bash
export GOROOT=/usr/local/go
export GOPATH=$HOME/go
export GO111MODULE=on
export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin
```

After updating your `~/.profile` you will need to source it:

```bash
source ~/.profile
```

## Build Rebus from source

```bash
git clone https://github.com/rebuschain/rebus.core
cd rebus.core
git fetch
git checkout <version-tag>
```

The `<version-tag>` will need to be set to either a [testnet `chain-id`](joining-the-testnets.md#current-testnets) or the latest [mainnet version tag](joining-mainnet.md).

{% hint style="warning" %}
For genesis, the mainnet version tag will be `v1.0.0` - i.e:

```bash
git checkout v1.0.0
```
{% endhint %}

Once you're on the correct tag, you can build:

```bash
# in rebus dir
make install
```

To confirm that the installation has succeeded, you can run:

```bash
rebusd version
```

## Connecting to the network

To connect to the Rebus network you can either run your own node or connect to a public node's RPC endpoint. To find a public node to connect to consider looking in the Rebus [Discord](https://discord.gg/QcWPfK4gJ2). Connecting to a public node requires the least configuration but you should be sure that you trust whatever node that you choose.

If you choose to run your own node see either [Joining Mainet](joining-mainnet.md) or [Joining Testnets](joining-the-testnets.md) depending on what chain you would like to work on.

