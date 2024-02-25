<!-- <h1 align="center">Aleo Workshop</h1> -->
<img alt="workshop" width="1412" src="./resources/readme.png">
<h3 align="center">📜 A starter guide to build applications on Aleo 📜</h3>

<p align="center">
    <a href="https://twitter.com/AleoHQ"><img src="https://img.shields.io/twitter/url/https/twitter.com/AleoHQ.svg?style=social&label=Follow%20%40AleoHQ"></a>
    <a href="https://aleo.org/discord"><img src="https://img.shields.io/discord/700454073459015690?logo=discord"/></a>
</p>

## Table of Contents
- [Workshop Preparation Guide](#workshop-preparation-guide)
    - [Prerequisites](#prerequisites)
    - [Installation](#installation)
- [IDE Support](#ide-support)
    - [VSCode](#vscode-preferred)
    - [Sublime Text](#sublime-text)
    - [IntelliJ IDEA](#intellij-idea)
- [Testnet Credits](#testnet-credits)
- [Application Walkthroughs](#application-walkthrough)
    - [🪙 Token](#-token) ([Source Code](./src))
- [Local Development](#local-development)
- [Testnet Development](#testnet-development)
- [Useful Links](#useful-links)



## Workshop Preparation Guide

The following steps will install Aleo and Leo on your machine. This workshop is compatible on macOS, Linux, and Windows machines.

### Prerequisites

This workshop requires the following prerequisites.

- Install `git` with [bit.ly/start-git](https://bit.ly/start-git)
- Install `Rust`with [bit.ly/start-rust](https://bit.ly/start-rust)

### Installation
Follow the instructions at the following links to install the required software.

#### snarkOS
https://github.com/AleoHQ/snarkOS

#### snarkVM
https://github.com/AleoHQ/snarkVM

#### Leo
https://developer.aleo.org/leo/installation/

#### Leo Wallet
https://chromewebstore.google.com/detail/leo-wallet/nebnhfamliijlghikdgcigoebonmoibm

<img alt="install_leo_wallet" width="1400" src="./resources/Install_Leo_Wallet.png"/>

## IDE Support

This workshop requires one of the following IDEs.
- [VSCode](https://bit.ly/start-vscode)
- [Sublime Text](https://bit.ly/start-sublime)
- [IntelliJ IDEA](https://bit.ly/start-intellij)

### VSCode (Preferred)

Start by installing `VSCode` with [bit.ly/start-vscode](https://bit.ly/start-vscode).

#### Next, in VSCode, open the **VSCode Marketplace**, type **Leo** into the search bar, and proceed to install the Leo plugin.
![Leo VSCode](./resources/VSCode_Leo.png)

### Sublime Text

<details><summary>Installation Steps</summary>

Start by installing `Sublime Text` with [bit.ly/start-sublime](https://bit.ly/start-sublime).

#### Next, in Sublime Text, install [Package Control](https://packagecontrol.io):
- On Windows/Linux: `ctrl + shift + p`, type **Install Package Control**, and press **Enter**.
- On macOS: `cmd + shift + p`, type **Install Package Control**, and press **Enter**.

#### Next, in Sublime Text, install [LSP](https://packagecontrol.io/packages/LSP):
- On Windows/Linux: `ctrl + shift + p`, select **Package Control: Install Package**, type **LSP**, and press **Enter**.
- On macOS: `cmd + shift + p`, select **Package Control: Install Package**, type **LSP**, and press **Enter**.

#### Lastly, in Sublime Text, install [LSP-leo](https://packagecontrol.io/packages/LSP-leo):
- On Windows/Linux: `ctrl + shift + p`, select **Package Control: Install Package**, type **LSP-leo**, and press **Enter**.
- On macOS: `cmd + shift + p`, select **Package Control: Install Package**, type **LSP-leo**, and press **Enter**.

</details>

### IntelliJ IDEA

<details><summary>Installation Steps</summary>

Start by installing `IntelliJ IDEA` with [bit.ly/start-intellij](https://bit.ly/start-intellij).

#### Next, in IntelliJ IDEA, open the **IntelliJ Marketplace** and select `Plugins`:
- On Windows/Linux: `ctrl + ,` and select `Plugins` on the left hand bar
- On macOS: `cmd + ,` and select `Plugins` on the left hand bar

Lastly, type **Leo** into the search bar, and install the official Leo plugin.

</details>


---
## Receiving Testnet Credits

There are currently 2 possible ways to get testnet credits.

1) Request from https://discord.com/channels/913160862670397510/1202322326230937640

2) Request from https://dev.puzzle.online/faucet

---
## Application Walkthrough

This workshop walks through the following application:
- [token](./) - A transparent & shielded custom token in Leo


### 🪙 Token

A transparent & shielded custom token in Leo.
We will create an application that allows you to mint private and public tokens.

##### Learning objectives
- Understand how to store information and modify state privately in records
- Understand how to store information publicly using mapping.
- Learn how to deploy a Leo program onto the Aleo testnet.
- Learn how to make public to private and private to public calls.




---

## Usage

Clone the repo
```
git clone https://github.com/Aleo-DevRel-Ambassadors/zkWorkshop_SG_NTU_240226.git
```

Enter the directory
```
cd zkWorkshop_SG_NTU_240226
```

Run some Leo CLI commands

```
leo run create_record
```


## Local Development

### Start a local devnet
Go to your snarkOS folder

Run
```
./devnet.sh
```

You should see

<img alt="local Node" width="1412" src="./resources/SnarkOS_Local.png"/>

--- 

### To deploy your program:

```
snarkos developer deploy <PROGRAM_NAME> --private-key <PRIVATE_KEY> --query "http://localhost:3033" --path ".build/" --broadcast "http://localhost:3033/testnet3/transaction/broadcast" --priority-fee 0

```
Example:

```
snarkos developer deploy my_token_1402.aleo --private-key APrivateKey1zkpBjpEgLo4arVUkQmcLdKQMiAKGaHAQVVwmF8HQby8vdYs --query "http://localhost:3033" --path "./build/" --broadcast "http://localhost:3033/testnet3/transaction/broadcast" --priority-fee 0
```

### To execute a function of your program

```
snarkos developer execute <PROGRAM_NAME> <FUNCTION_NAME> <INPUT_ARGUMENTS> --private-key <PRIVATE_KEY> --query "http://localhost:3033" --broadcast "http://localhost:3033/testnet3/transaction/broadcast"

```

Example:

```
snarkos developer execute my_token_1402.aleo create_record --private-key APrivateKey1zkpBjpEgLo4arVUkQmcLdKQMiAKGaHAQVVwmF8HQby8vdYs --query "http://localhost:3033" --broadcast "http://localhost:3033/testnet3/transaction/broadcast" 
```

### To scan for your records

```
snarkos developer scan -v <VIEW_KEY> --start 0 --end 1 --endpoint "http://localhost:3033"

```

Example:

```
snarkos developer scan -v AViewKey1iKKSsdnatHcm27goNC7SJxhqQrma1zkq91dfwBdxiADq --start 0 --end 1 --endpoint "http://localhost:3033"

```

---

## Testnet Development

Similar steps as above, but using different API endpoints and specifying record

Query: https://api.explorer.aleo.org/v1
Broadcast: https://api.explorer.aleo.org/v1/testnet3/transaction/broadcast

For Haruka's Aleo Explorer
Query: https://explorer.hamp.app


Deploy Command

```
snarkos developer deploy <PROGRAM_NAME> --private-key <PRIVATE_KEY> --query "https://api.explorer.aleo.org/v1" --path "./build/" --broadcast "https://api.explorer.aleo.org/v1/testnet3/transaction/broadcast" --priority-fee 0

```

Example

```
snarkos developer deploy my_token_1402.aleo --private-key "<PRIVATE_KEY>" --query "https://api.explorer.aleo.org/v1" --path "./build/" --broadcast "https://api.explorer.aleo.org/v1/testnet3/transaction/broadcast" --priority-fee 0
```

Execute Example
```
snarkos developer execute my_token_1402.aleo mint_private snarkos developer execute my_token_2602.aleo mint_private "{  owner: aleo1752ryjqhanf8m7dxn2dxralh8vuszp20ywqgttl68ue36kgsg5zs28j6yg.private,  amount: 10u64.private,
  _nonce: 33448326606935668906782998632395801444176995256723808316320437367514472280group.public 
}" 21u64 --private-key APrivateKey_YOUR_PRIVATE_KEY --query "https://explorer.hamp.app" --broadcast "https://api.explorer.aleo.org/v1/testnet3/transaction/broadcast" --priority-fee 0
```

## Useful Links
- [Learn Leo](https://developer.aleo.org/leo/)
- [Developer Documentation](https://developer.aleo.org/testnet/getting_started/overview)
- Aleo Explorers
    - [Aleo Explorer](https://explorer.aleo.org)
    - [Haruka's Aleo Explorer](https://explorer.hamp.app)
    - [Aleo123](https://aleo123.io)
- Aleo Resources
  - [Leo Playground](https://play.leo-lang.org)
  - [Aleo SDK] (https://aleo.tools/account)