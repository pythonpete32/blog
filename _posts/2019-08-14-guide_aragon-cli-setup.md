---
title: 'Guide: AragonCLI setup'
published: true
---

Aragon CLI is a extremely powerful tool. If you are developing Aragon apps, administrating a DAO, or a power user the cli is an indispensable tool. there are many things you cant do through the front end application that require the use of the CLI.

<br>

## [](#header-2) Operating system

I use Lubuntu but this should work on any Ubuntu/Debian setup. I haven't tested this on Mac but it should work too. If you're using windows :grimacing: this will probably work with Linux subsystem for windows but do your self a favour and just make the switch to Linux

<br>

## [](#header-2) Update your system

First things first, update and upgrade your system

<br>

```
sudo apt-get update && sudo apt-get upgrade
```

<br>

## [](#header-2) Install global libraries

Install the dependencies some if which are not obvious from the inevitable error messages you will run into if you just try to `npm install @aragon/cli`

<br>

```
sudo apt install build-essential git python
```

<br>

## [](#header-2) Install zsh (optional)

While not necessary, you will be spending a lot of time in the terminal so you might as well make it look sexy. Along with zsh we will be installing `oh-my-zsh`, other than a good looking terminal, it makes life much easier with auto-completion and a bunch of plugins.

If your using a cloud machine you will probably not have a password as you will be using ssh to connect. You will need it when installing `oh-my-zsh`.

<br>

```sh
sudo passwd [your user name]
```

<br>

Then install zsh

<br>

```sh
sudo apt install zsh
```

<br>

Now you can install the `oh my zsh` plugin

<br>

```sh
curl -Lo install.sh https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh
sh install.sh
```

It's worth exploring the plugins and themes on the [official repo](https://github.com/robbyrussell/oh-my-zsh/blob/master/README.md) but for now we can move

<br>

## [](#header-2) Install NVM

While you can just install node manually, NVM makes managing your node installation much easier. Further more you can have more than one version installed at the same time, which is handy as some packages are not always compatible with all node versions. I'm using `10.15.3` this works well with everything and is a LTS version. If you skipped the above step replace `zsh` with `bash` at the end of the command

<br>

```sh
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | zsh
```

<br>

Open a new terminal window and install node

<br>

```sh
nvm install 10.15.3
```

<br>

## [](#header-2) Install Aragon CLI

<br>

```sh
npm i -g @aragon/cli
```

<br>

Since version `6.0.0` ipfs is not including with the cl so install it with

<br>

```sh
aragon ipfs install
```

<br>

## [](#header-2) Setting up cli

Finally we need to set up a private key for use with the cli.

Warning: **DO NOT USE A KEY YOU ALREADY HAVE REAL FUNDS IN**

Create a new key and get some test net sth from the [rinkeby faucet](https://faucet.rinkeby.io/)

Some times the `~/.aragon` file is not included in the installation which is a problem because that's where out private key goes.

<br>

```sh
cd ~/.aragon
```

<br>

If you get `file not found` run the dev chain first `aragon devchain` and try again

Once your in the `~/.aragon` folder you need to crate a file that holds your private key.

have a separate key for rinkeby ETH, when interacting with your DAO on the main net, i highly advise using a hardware wallet and frame

Create a new the file for your rinkeby key

<br>

```sh
nano ~/.aragon/rinkeby_key.json
```

<br>

This will open a blank file, copy and paste the following replacing the text with your private key

<br>

```js
{
"rpc": "https://rinkeby.infura.io",
"keys": ["put-your-priv-key-here"]
}
```

<br>

now test out your configuration by launching a DAO on rinkeby

<br>

```sh
dao new --environment aragon:rinkeby
```
