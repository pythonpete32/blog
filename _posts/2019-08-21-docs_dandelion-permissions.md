---
title: Dandelion Permissions 
published: false
---


```sh
dao=0xe28cD3aFB5db1C6CCc28da836a79B169Ac70a358
tokens=0xD978B6EdBa49FC9BE0DbbDAe31d599e336741E7D
voting=0x03AB01a1EcC29653aBeCc6560C8C53d08a155Dc9
finance=0x1B10B0A8d00B7F4e1Ad0Ae998C6D7Eb6082E8525
vault=0x37c2162fE7Ab27e86583dC63CE807A6c26A30705
```


| Application   | Permission                 | Grantee       | Manager|
|:--------------|:-------------------------- |:------------- |:-------|
| Token Request | SET_TOKEN_MANAGER_ROLE     | Voting        | Voting |
| Token Request | SET_VAULT_ROLE             | Voting        | Voting |
| Token Request | FINALISE_TOKEN_REQUEST_ROLE| Voting        | Voting |
| Redemptions   | REDEEM_ROLE                | Token Manager | Voting |
| Redemptions   | ADD_TOKEN_ROLE             | Voting        | Voting |
| Redemptions   | REMOVE_TOKEN_ROLE          | Voting        | Voting |
| Lock App      | CHANGE_DURATION_ROLE       | Voting        | Voting |
| Lock App      | CHANGE_AMOUNT_ROLE         | Voting        | Voting |
| Vault         | TRANSFER_ROLE              | Redemptions   | Voting |
| Token Manager | BURN_ROLE                  | Redemptions   | Voting |
| Voting        | CREATE_VOTE_ROLE           | Token Request | Voting |