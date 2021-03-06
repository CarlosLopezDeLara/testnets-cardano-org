---
parent: 2020-05-05_16-12-19_installing-and-running-the-cardano-node
title: Building a node from source
description: Shelley testnet
order: 2
external_href: ""
last_updated: 2020-05-19T16:19:01.000Z
redirects:
  - from: /en/shelley-haskell/get-started/installing-and-running-the-cardano-node/building-the-node-from-source/
    type: 301
---
## Building a node from source
By building and running a node directly from the source code, you can ensure that you get all the latest code updates.

The following instructions presume that you will be running your node on a Linux system and are using cabal. For more information, see the [supported platforms](shelley/about/supported-platforms/) page. You can run a node on any platform by [using a virtual machine](/shelley/get-started/installing-and-running-the-cardano-node/running-the-node-on-an-aws-instance/).

To build and run a node from source, you need the following packages and tools:

* the Haskell platform and Haskell build-tool cabal
* the version control system git
* the gcc C-compiler
* C++ support for gcc
* developer libraries for the the arbitrary precision library gmp
* developer libraries for the compression library zlib
* developer libraries for systemd and ncurses

You can install these dependencies as follows:

```shell
sudo yum update -y
sudo yum install git gcc gmp-devel -y
sudo yum install zlib-devel systemd-devel ncurses-devel -y
curl -sSL https://get.haskellstack.org/ | sh
```

If you are using a different flavor of Linux, you will need to use the package manager suitable for your platform, instead of yum, and the names of the packages you need to install might differ.

How to build and run the node from source:

1. In the terminal, run the following git command to clone the Cardano node repository and download the source code:
   ```shell
   git clone https://github.com/input-output-hk/cardano-node.git
   ```
1. Download the latest source code from the [releases page](https://github.com/input-output-hk/cardano-node/releases) to this folder. After the download has finished, you can check the contents using the following command:
   ```shell
   ls cardano-node
   ```
1. Change your working directory to the folder in which the source code was downloaded using the following command:
   ```shell
   cd cardano-node
   ```
1. You should check out the latest release, for example tag 1.11.0 using the following command:
   ```shell
   git fetch --all --tags
   git checkout tags/1.11.0
   ```
5. Build the source code using Cabal by running the following command:
   ```shell
   build all
   ```
Please note that building the node may take some time, possibly several hours.  
6. Run the following command to initialize the node:
   ```shell
   ./scripts/shelley-testnet-live.sh
   ```

You should now have a Cardano node running on your machine, connected to the Shelley testnet.
