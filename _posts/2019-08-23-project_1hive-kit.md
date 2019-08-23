---
title: "Project: 1Hive kit"
published: true
---

## [](#header-2) Plan

so the plan is to develop a kit for 1Hive. start with 1-8,

1. Deploy a fresh dao
2. Deploy the organizations membership token Bee
3. Deploy a voting app instance tied to the Bee this voting app will serve as the root authority in the organization
4. Deploy a Token Manager instance to manage the Bee token to our dao
5. Deploy the organization's contribution token Honey
6. Install a token manager to manage Honey
7. Deploy a second voting app instance tied to Honey. This voting app will have authority of finances.
8. Install a vault and the finance app
9. Install Projects and Allocations + dependencies

## [](#header-2) Permissions (1-8)

| Application       | Permission | Grantee | Manager |
| :---------------- | :--------- | :------ | :------ |
| Token Man (BEE)   |            |         |         |
| Token Man (HONEY) |
| Voting (BEE)      |
| Voting (HONEY)    |
| Vault             |
| Finance           |

## [](#header-2) References

- [Templates intro](https://hack.aragon.org/docs/templates-intro)

* [Company Template](https://github.com/aragon/dao-templates/blob/master/templates/company-board/contracts/CompanyBoardTemplate.sol)

-
