---
title: 'Guide: Redemptions set up guide'
published: true
---


## [](#header-2) Deploy a fresh dao

Head over to the [rinkeby DAO launcher](rinkeby.aragon.org) and create a DAO with the democracy kit


Ensure the account used within  [Aragon CLI](https://hack.aragon.org/docs/cli-intro.html) has a token in your DAO. If you used the same account to create the DAO you already have one. You can follow my [setup guide here](_posts/2019-08-14-guide_aragon-cli-setup.md)


Go to the settings tab where you will find the addresses for the DAO and its apps. For legibility of subsequent commands will set bash environment variable for these addresses:

<br>

```
dao=[your DAO address]
token=[your Token-manager address]
voting=[your Voting-app address]
vault=[your Vault-app address]
```

<br>

## [](#header-2) Install Redemptions App

Redemptions has been published to APM on rinkeby at `redemptions.open.aragonpm.eth`

To deploy to an organization you will use the Aragon CLI

<br/>

```sh
aragon dao install $dao redemptions.open.aragonpm.eth --app-init-args $vault $token --environment aragon:rinkeby
```
<br/>

The default setup of the democracy DAO is for a vote of the token holders to take place before actions are executed. Head over to the voting app and you will see a new vote 


## [](#header-2) Set up Permissions

Before the Redemptions app displays in the UI you must set a permission on it. First, get the address of the Redemptions app 

<br/>

```sh
dao apps $dao --all --environment aragon:rinkeby
```
<br/>

Next, copy the proxy address of the permissionless app and create another environment variable

<br/>

 ```sh
redemptions=[redemptions-address]
```

<br/>

Three permissions need to be created for the Redemptions app to function properly

- `REDEEM_ROLE`
- `ADD_TOKEN_ROLE`
- `REMOVE_TOKEN_ROLE`

After setting one of these roles the Redemptions App will appear in the UI

<br/>

```sh
dao acl create $dao $redemptions REDEEM_ROLE $token $voting --environment aragon:rinkeby
```

<br/>

This grants token holders the permission to redeem tokens and sets the voting app as the controller. Again like the rest of the commands that change state, you must first vote before the action takes affect.

<br/>

```sh
dao acl create $dao $redemptions ADD_TOKEN_ROLE $voting $voting --environment aragon:rinkeby
```

<br/>

This grants the voting app the permission to add tokens to the list of redeemable tokens and sets it as the controller 

<br/>

```sh
dao acl create $dao $redemptions REMOVE_TOKEN_ROLE $token $voting --environment aragon:rinkeby
```

<br/>

This grants the voting app the permission to remove tokens from the list of redeemable tokens and sets it as the controller 

<br/>

The Redemptions app must also have the `TRANSFER_ROLE` permission on `Vault` and the `BURN_ROLE` permission on the `Token Manager`.

<br/>

```sh
dao acl create $dao $token BURN_ROLE $redemptions $voting --environment aragon:rinkeby
```
<br/>

```sh
dao acl create $dao $vault TRANSFER_ROLE $redemptions $voting --environment aragon:rinkeby
```

<br/>

## [](#header-2) Testing the Redemptions app
Before we test out Redemptions, we are going to need some tokens to redeem and some assets to redeem them for 

Go back to the settings tab and press the request tokens button a few times. This will deposit some tokens into the vault. 

Open the finance app and you will see a number of deposits, you will need the contract address of the tokens you want to add to redemptions. 

Choose one of the transactions and view it on etherscan, find the contract address, copy it and head over to the redemptions app.

Click add token and paste in the contract address.



