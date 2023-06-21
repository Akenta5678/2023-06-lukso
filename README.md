# ✨ So you want to run an audit

This `README.md` contains a set of checklists for our audit collaboration.

Your audit will use two repos:

- **an _audit_ repo** (this one), which is used for scoping your audit and for providing information to wardens
- **a _findings_ repo**, where issues are submitted (shared with you after the audit)

Ultimately, when we launch the audit, this repo will be made public and will contain the smart contracts to be reviewed and all the information needed for audit participants. The findings repo will be made public after the audit report is published and your team has mitigated the identified issues.

Some of the checklists in this doc are for **C4 (🐺)** and some of them are for **you as the audit sponsor (⭐️)**.

---

# Repo setup

## ⭐️ Sponsor: Add code to this repo

- [ ] Create a PR to this repo with the below changes:
- [ ] Provide a self-contained repository with working commands that will build (at least) all in-scope contracts, and commands that will run tests producing gas reports for the relevant contracts.
- [ ] Make sure your code is thoroughly commented using the [NatSpec format](https://docs.soliditylang.org/en/v0.5.10/natspec-format.html#natspec-format).
- [ ] Please have final versions of contracts and documentation added/updated in this repo **no less than 24 hours prior to audit start time.**
- [ ] Be prepared for a 🚨code freeze🚨 for the duration of the audit — important because it establishes a level playing field. We want to ensure everyone's looking at the same code, no matter when they look during the audit. (Note: this includes your own repo, since a PR can leak alpha to our wardens!)

---

## ⭐️ Sponsor: Edit this README

Under "SPONSORS ADD INFO HERE" heading below, include the following:

- [ ] Modify the bottom of this `README.md` file to describe how your code is supposed to work with links to any relevent documentation and any other criteria/details that the C4 Wardens should keep in mind when reviewing. ([Here's a well-constructed example.](https://github.com/code-423n4/2022-08-foundation#readme))
  - [ ] When linking, please provide all links as full absolute links versus relative links
  - [ ] All information should be provided in markdown format (HTML does not render on Code4rena.com)
- [x] Under the "Scope" heading, provide the name of each contract and:
  - [x] source lines of code (excluding blank lines and comments) in each
  - [x] external contracts called in each
  - [x] libraries used in each
- [ ] Describe any novel or unique curve logic or mathematical models implemented in the contracts
- [ ] Does the token conform to the ERC-20 standard? In what specific ways does it differ?
- [ ] Describe anything else that adds any special logic that makes your approach unique
- [ ] Identify any areas of specific concern in reviewing the code
- [ ] Review the Gas award pool amount. This can be adjusted up or down, based on your preference - just flag it for Code4rena staff so we can update the pool totals across all comms channels.
- [ ] Optional / nice to have: pre-record a high-level overview of your protocol (not just specific smart contract functions). This saves wardens a lot of time wading through documentation.
- [ ] See also: [this checklist in Notion](https://code4rena.notion.site/Key-info-for-Code4rena-sponsors-f60764c4c4574bbf8e7a6dbd72cc49b4#0cafa01e6201462e9f78677a39e09746)
- [ ] Delete this checklist and all text above the line below when you're ready.

---

[![Twitter](https://img.shields.io/twitter/follow/lukso_io)](https://twitter.com/lukso_io)
[![Telegram](https://img.shields.io/badge/Telegram-555?logo=telegram)](https://t.me/LUKSO)
[![Discord](https://img.shields.io/badge/Discord-555?logo=discord)](https://discord.com/invite/lukso)
[![Contracts](https://img.shields.io/badge/Contracts-555)](https://github.com/lukso-network/lsp-smart-contracts)
[![LIPs](https://img.shields.io/badge/LIPs-555)](https://github.com/lukso-network/LIPs)
[![Docs](https://img.shields.io/badge/Docs-555)](https://docs.lukso.tech)

# LUKSO audit details

- Total Prize Pool: $100,000 USDC
  - HM awards: $70,000 USDC
  - Analysis awards: $4,250 USDC
  - QA awards: $2,000 USDC
  - Bot Race awards: $6,250 USDC
  - Gas awards: $2,000 USDC
  - Judge awards: $9,000 USDC
  - Lookout awards: $6,000 USDC
  - Scout awards: $500 USDC
- Join [C4 Discord](https://discord.gg/code4rena) to register
- Submit findings [using the C4 form](https://code4rena.com/contests/2023-06-lukso/submit)
- [Read our guidelines for more details](https://docs.code4rena.com/roles/wardens)
- Starts June 20, 2023 20:00 UTC
- Ends July 05, 2023 20:00 UTC

## Automated Findings / Publicly Known Issues

Automated findings output for the audit can be found [here](add link to report) within 24 hours of audit opening.

_Note for C4 wardens: Anything included in the automated findings output is considered a publicly known issue and is ineligible for awards._

[ ⭐️ SPONSORS ADD INFO HERE ]

# Overview

## LSP0ERC725Account

_[LSP0ERC725Account]_ is an advanced smart contract-based account that offers a comprehensive range of essential features. It provides generic data storage, a generic execution medium, and a universal function to be notified about different actions, such as token transfers, followers, information, etc .. Also it offers extensibility where you can add functions to the account as extensions after deployment to support new standards and functions, and also providing a full secure ownership control.

## LSP14Ownable2Step

_[LSP14Ownable2Step]_ is an advanced ownership module designed to enable contracts to have a clear ownership structure. It introduces a crucial feature of two-step processes for both ownership transfer and renouncement, which significantly reduces the likelihood of accidental or unauthorized changes to the contract's ownership. This enhanced security mechanism ensures that ownership actions require deliberate and careful confirmation, minimizing the risk of unintended transfers or renouncements. Using a two-step process where the new owner has to accept ownership ensures that the contract is always owned by an address that has control over it since the new owner explicitly accepts ownership, proving that it has control over its address.

## LSP20CallVerification

_[LSP20CallVerification]_ is an innovative module designed to simplify access control rules verification within smart contracts. By implementing a standardized approach, this module enables seamless validation of whether an address possesses the necessary permissions to initiate a specific call.

_Please provide some context about the code being audited, and identify any areas of specific concern in reviewing the code. (This is a good place to link to your docs, if you have them.)_

# Scope

_List all files in scope in the table below (along with hyperlinks) -- and feel free to add notes here to emphasize areas of focus._

_For line of code counts, we recommend using [cloc](https://github.com/AlDanial/cloc)._

## Summary

| Scope                         | code | Standard Specifications           | Standard Documentation                                    |
| ----------------------------- | ---- | --------------------------------- | --------------------------------------------------------- |
| ERC725                        | 428  | [ERC-725]                         | [ERC725]                                                  |
| LSP0ERC725Account             | 406  | [LSP-0-ERC725Account]             | [LSP0ERC725Account]                                       |
| UniversalProfile              | 33   | [LSP-3-UniversalProfile-Metadata] | [UniversalProfile]                                        |
| LSP1UniversalReceiverDelegate | 200  | [LSP-1-UniversalReceiver]         | [LSP1UniversalReceiver] & [LSP1UniversalReceiverDelegate] |
| LSP4DigitalAssetMetadata      | 86   | [LSP-4-DigitalAsset-Metadata]     | [LSP4DigitalAsset]                                        |
| LSP6KeyManager                | 1236 | [LSP-6-KeyManager]                | [LSP6KeyManager]                                          |
| LSP7DigitalAsset              | 656  | [LSP-7-DigitalAsset]              | [LSP7DigitalAsset]                                        |
| LSP8IdentifiableDigitalAsset  | 964  | [LSP-8-IdentifiableDigitalAsset]  | [LSP8IdentifiableDigitalAsset]                            |
| LSP14Ownable2Step             | 99   | [LSP-14-Ownable2Step]             | [LSP14Ownable2Step]                                       |
| LSP17ContractExtension        | 69   | [LSP-17-ContractExtension]        | [LSP17ContractExtension]                                  |
| LSP20CallVerification         | 60   | [LSP-20-CallVerification]         | [LSP20CallVerification]                                   |
| EIP191Signer                  | 9    |                                   |                                                           |
| LSP2Utils                     | 33   | [LSP-2-ERC725YJSONSchema]         | [LSP2ERC725YJSONSchema]                                   |
| LSP5Utils                     | 106  | [LSP-4-DigitalAsset-Metadata]     | [LSP5ReceivedVaults]                                      |
| LSP10Utils                    | 101  | [LSP-10-ReceivedVaults]           | [LSP10ReceivedVaults]                                     |
| SUM                           | 4486 |                                   |                                                           |

---

## Contracts in scope

This is the complete list of the contracts in scope for this contest.

There are 3 type of contracts per LSP standard:

- **`Core` contracts**: contain the core implementation logic of the LSP standard.

_Example: `LSP7DigitalAssetCore.sol` contains the core logic of the LSP7 standard_.

- **Standard contracts**: standard version of the LSP standard, deployable via `constructor(...)`. They are written with the same name as the standard.

_Example: `LSP0ERC725Account.sol`_.

- **`Init` contracts**: proxy version of the LSP standard, to be used as base contracts behind proxies. Should be initialized via the public `initialize(...)` function.

_Example: `LSP0ERC725AccountInit.sol`_

- **`InitAbstract` contracts**: same as `Init` but without a public `initialize(...)` function. To be inherited for customization.

_Example: `LSP6KeyManagerInitAbstract.sol`_

> **Note:** the separation between `Core`, `Init` and `InitAbstract` does not apply to LSP14, LSP17 and LSP20.

| Contract                                              | SLOC | Purpose                                                                                                                                           | Libraries used                                                                                                                                                                                                |
| ----------------------------------------------------- | ---- | ------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **LSP0ERC725Account**                                 |      |                                                                                                                                                   |                                                                                                                                                                                                               |
| [`LSP0ERC725AccountCore.sol`]                         | 331  | Core implementation of the LSP0 standard, a smart contract based account.                                                                         | `@openzeppelin/contracts`: \[[`ECDSA.sol`], [`ERC165Checker.sol`], [`Address.sol`]\] `@erc725/smart-contracts/`: \[[`ERC725YCore.sol`], [`ERC725XCore.sol`], [`OwnableUnset.sol`], [`ERC725.constants.sol`]\] |
| [`LSP0Utils.sol`]                                     | 23   | Utility functions to query metadata keys from the ERC725Y storage of an LSP0ERC725Account.                                                        |                                                                                                                                                                                                               |
| [`LSP0ERC725AccountInitAbstract.sol`]                 | 12   | Abstract Proxy version of the LSP0 standard without a public `initialize(...)` function.                                                          | `@openzeppelin/contracts-upgradeable`: [`Initializable.sol`]                                                                                                                                                  |
| [`ILSP0ERC725Account.sol`]                            | 11   | Interface that describes the standard functions and events defined in the LSP0 standard.                                                          |                                                                                                                                                                                                               |
| [`LSP0ERC725Account.sol`]                             | 11   | Standard version of the LSP0 standard.                                                                                                            |                                                                                                                                                                                                               |
| [`LSP0ERC725AccountInit.sol`]                         | 10   | Proxy version of the LSP0 standard.                                                                                                               |                                                                                                                                                                                                               |
| [`LSP0Constants.sol`]                                 | 8    | Contains the standard ERC725Y metadata keys and LSP1 type IDs defined in the LSP0 Standard as well as `bytes4` ERC165 interface ID.               |                                                                                                                                                                                                               |
| **UniversalProfile**                                  |      | **These 3 x contracts are implementations of LSP0 + set the metadata keys defined in the LSP3 standard on deployment/initialization.**            |                                                                                                                                                                                                               |
| [`UniversalProfileInitAbstract.sol`]                  | 12   | Abstract Proxy version without a public `initialize(...)` function.                                                                               |                                                                                                                                                                                                               |
| [`UniversalProfile.sol`]                              | 11   | Standard version.                                                                                                                                 |                                                                                                                                                                                                               |
| [`UniversalProfileInit.sol`]                          | 10   | Proxy version.                                                                                                                                    |                                                                                                                                                                                                               |
| **LSP1UniversalReceiverDelegate**                     |      |                                                                                                                                                   |                                                                                                                                                                                                               |
| [`LSP1UniversalReceiverDelegateUP.sol`]               | 107  | Core implementation of the optional extension of LSP1 Universal Receiver Delegate to be used for a Universal Profile.                             | `@openzeppelin/contracts/`: \[[`ERC165.sol`], [`ERC165Checker.sol`]\]                                                                                                                                         |
| [`LSP1Utils.sol`]                                     | 71   | Library of utility functions to interact with contracts that implement the LSP1 interface.                                                        | `@openzeppelin/contracts/`: \[[`Address.sol`], [`ERC165Checker.sol`]\]                                                                                                                                        |
| [`ILSP1UniversalReceiver.sol`]                        | 14   | Interface that describe the standard function defined in the LSP1 standard.                                                                       |                                                                                                                                                                                                               |
| [`LSP1Constants.sol`]                                 | 4    | Contains the standard ERC725Y metadata keys defined in the LSP1 Universal Receiver standard, as well as its ERC165 interface ID.                  |                                                                                                                                                                                                               |
| [`LSP1Errors.sol`]                                    | 4    | Custom errors related to the internal logic of `LSP1UniversalReceiverDelegateUP.sol`.                                                             |                                                                                                                                                                                                               |
| **LSP4DigitalAssetMetadata**                          |      |                                                                                                                                                   |                                                                                                                                                                                                               |
| [`LSP4DigitalAssetMetadataInitAbstract.sol`]          | 30   | Abstract Proxy version of the LSP4 standard, without a public `initialize(...)` function.                                                         |                                                                                                                                                                                                               |
| [`LSP4DigitalAssetMetadata.sol`]                      | 25   | Standard version of LSP4 standard.                                                                                                                | `@erc725/smart-contracts`: [`ERC725Y.sol`], `solidity-bytes-utils`: [`BytesLib.sol`]                                                                                                                          |
| [`LSP4Compatibility.sol`]                             | 14   | Contains backward compatible getters from ERC721Metadata that query the LSP4 metadata keys from the ERC725Y storage.                              | `@erc725/smart-contracts`: [`ERC725YCore.sol`]                                                                                                                                                                |
| [`LSP4Constants.sol`]                                 | 8    | Contains the standard ERC725Y metadata keys defined in the LSP4 Digital Asset Metadata standard.                                                  |                                                                                                                                                                                                               |
| [`ILSP4Compatibility.sol`]                            | 6    | Interface for `name()` and `symbol()`.                                                                                                            |                                                                                                                                                                                                               |
| [`LSP4Errors.sol`]                                    | 3    | Custom errors related to the internal logic of `LSP4DigitalAssetMetadata.sol` and `LSP4DigitalAssetMetadataInitAbstract.sol`.                     |                                                                                                                                                                                                               |
| **LSP6KeyManager**                                    |      |                                                                                                                                                   |                                                                                                                                                                                                               |
| [`LSP6SetDataModule.sol`]                             | 381  | Logic used for verifying `ERC725Y.setData()` & `ERC725Y.setDataBatch()` permissions.                                                              | `@erc725/smart-contracts`: [`ERC725Y.sol`]                                                                                                                                                                    |
| [`LSP6KeyManagerCore.sol`]                            | 352  | Core implementation of the LSP6 standard, a smart contract that acts as a controller for an an ERC725 account.                                    | `@openzeppelin/contracts`: \[[`ERC165.sol`], [`ECDSA.sol`], [`Address.sol`]\]                                                                                                                                 |
| [`LSP6ExecuteModule.sol`]                             | 218  | Logic used for verifying `ERC725X.execute()` & `ERC725X.executeBatch()` permissions.                                                              | `@erc725/smart-contracts`: [`ERC725Y.sol`], `solidity-bytes-utils`: [`BytesLib.sol`], `@openzeppelin/contracts/`: [`ERC165Checker.sol`]                                                                       |
| [`LSP6Utils.sol`]                                     | 145  | Library of utility functions to read, write and handle permissions for controllers.                                                               |                                                                                                                                                                                                               |
| [`LSP6Constants.sol`]                                 | 40   | Contains the standard ERC725Y metadata keys and permissions defined in the LSP6 Key Manager standard, as well as its ERC165 interface ID.         |                                                                                                                                                                                                               |
| [`ILSP6KeyManager.sol`]                               | 27   | Interface that describes the standard functions and events defined in the LSP6 Key Manager standard.                                              |                                                                                                                                                                                                               |
| [`LSP6Errors.sol`]                                    | 25   | Custom errors related to the internal logic of `LSP6KeyManagerCore` and the modules in the `contracts/LSP6KeyManager/LSP6Modules/*.sol` folder`.  |                                                                                                                                                                                                               |
| [`LSP6OwnershipModule.sol`]                           | 17   | Logic used for verifying `ERC725.acceptOwnership()` & `ERC725.transferOwnership()` permissions.                                                   |                                                                                                                                                                                                               |
| [`LSP6KeyManagerInitAbstract.sol`]                    | 11   | Abstract Proxy version of the LSP6 standard, without a public `initialize(...)` function.                                                         | `@openzeppelin/contracts-upgradeable`: [`Initializable.sol`]                                                                                                                                                  |
| [`LSP6KeyManager.sol`]                                | 10   | Standard version of LSP6 standard.                                                                                                                | Same as `LSP6KeyManagerCore.sol`                                                                                                                                                                              |
| [`LSP6KeyManagerInit.sol`]                            | 10   | Proxy version of the LSP6 standard.                                                                                                               | Same as `LSP6KeyManagerCore.sol` + `LSP6KeyManagerInitAbstract.sol`                                                                                                                                           |
| **LSP7DigitalAsset**                                  |      |                                                                                                                                                   |                                                                                                                                                                                                               |
| [`LSP7DigitalAssetCore.sol`]                          | 197  | Core implementation of the LSP7 standard, a smart contract that represents a fungible token.                                                      | `@openzeppelin/contracts`: [`ERC165Checker.sol`]                                                                                                                                                              |
| [`LSP7CompatibleERC20InitAbstract.sol`]               | 85   | Extension (Abstract Proxy version without a public `initialize(...)` function) - of the `ILSP7CompatibleERC20` interface.                         |                                                                                                                                                                                                               |
| [`LSP7CompatibleERC20.sol`]                           | 69   | Extension (Standard version) - of the `ILSP7CompatibleERC20` interface.                                                                           |                                                                                                                                                                                                               |
| [`ILSP7DigitalAsset.sol`]                             | 42   | Interface that describes the standard functions and events defined in the LSP7 Digital Asset standard.                                            |                                                                                                                                                                                                               |
| [`LSP7DigitalAssetInitAbstract.sol`]                  | 27   | Abstract Proxy version of the LSP7 standard, without a public `initialize(...)` function.                                                         | `@erc725/smart-contracts`: [`ERC725YCore.sol`]                                                                                                                                                                |
| [`LSP7CappedSupply.sol`]                              | 27   | Extension (Standard version) - to define a maximum total supply of tokens.                                                                        |                                                                                                                                                                                                               |
| [`LSP7CappedSupplyInitAbstract.sol`]                  | 27   | Extension (Abstract proxy version) - to define a maximum total supply of tokens.                                                                  |                                                                                                                                                                                                               |
| [`LSP7DigitalAsset.sol`]                              | 21   | Standard version of the LSP7 standard.                                                                                                            | `@erc725/smart-contracts`: [`ERC725YCore.sol`]                                                                                                                                                                |
| [`LSP7MintableInitAbstract.sol`]                      | 21   | Preset deployable contract (Abstract proxy version without a public `initialize(...)` function) - same as `LSP7Mintable.sol`.                     |                                                                                                                                                                                                               |
| [`LSP7CompatibleERC20MintableInitAbstract.sol`]       | 19   | Preset deployable contract (Abstract Proxy version without a public `initialize(...)` function) - same as `LSP7Mintable.sol`.                     |                                                                                                                                                                                                               |
| [`LSP7Mintable.sol`]                                  | 19   | Preset deployable contract (Standard version) - contains a public `mint(...)` only callable by the owner.                                         |                                                                                                                                                                                                               |
| [`LSP7CompatibleERC20Mintable.sol`]                   | 17   | Preset deployable contract (Standard version) - same as `LSP7CompatibleERC20.sol` with a public `mint(...)` function only callable by the owner.  |                                                                                                                                                                                                               |
| [`LSP7Errors.sol`]                                    | 16   | Custom errors related to the internal logic of `LSP7DigitalAssetCore.sol`.                                                                        |                                                                                                                                                                                                               |
| [`LSP7CompatibleERC20MintableInit.sol`]               | 16   | Preset deployable contract (Abstract Proxy version without a public `initialize(...)` function) - same as `LSP7CompatibleERC20Mintable.sol`       |                                                                                                                                                                                                               |
| [`LSP7MintableInit.sol`]                              | 15   | Preset deployable contract (Proxy version) - same as `LSP7Mintable.sol`                                                                           |                                                                                                                                                                                                               |
| [`ILSP7CompatibleERC20.sol`]                          | 10   | Interface to enable backward compatibility between LSP7 and the functions from the ERC20 standard.                                                |                                                                                                                                                                                                               |
| [`ILSP7Mintable.sol`]                                 | 10   | Interface for a public `mint(...)` function for a LSP7 fungible token.                                                                            |                                                                                                                                                                                                               |
| [`LSP7Burnable.sol`]                                  | 7    | Standard extension that implements a public `burn(...)` function to burn a specified `amount` of tokens.                                          |                                                                                                                                                                                                               |
| [`LSP7BurnableInitAbstract.sol`]                      | 7    | Abstract Proxy extension that implements a public `burn(...)` function to burn a specified `amount` of tokens.                                    |                                                                                                                                                                                                               |
| [`LSP7Constants.sol`]                                 | 4    | Contains the standard LSP1 type IDs defined in the LSP7 Digital Asset standard, as well as its ERC165 interface ID.                               |                                                                                                                                                                                                               |
| **LSP8IdentifiableDigitalAsset**                      |      |                                                                                                                                                   |                                                                                                                                                                                                               |
| [`LSP8IdentifiableDigitalAssetCore.sol`]              | 222  | Core implementation of the LSP8 standard, a smart contract that represents a non-fungible token.                                                  | `@openzeppelin/contracts`: \[[`EnumerableSet.sol`], [`ERC165Checker.sol`]\]                                                                                                                                   |
| [`LSP8CompatibleERC721InitAbstract.sol`]              | 179  | Extension (Abstract Proxy version) - of the `ILSP8CompatibleERC721` interface, without a public `initialize(...)` function.                       | `@openzeppelin/contracts`: [`EnumerableSet.sol`], `solidity-bytes-utils`: [`BytesLib.sol`]                                                                                                                    |
| [`LSP8CompatibleERC721.sol`]                          | 177  | Extension (Standard version) - of the `ILSP8CompatibleERC721` interface.                                                                          | `@openzeppelin/contracts`: [`EnumerableSet.sol`], `solidity-bytes-utils`: [`BytesLib.sol`]                                                                                                                    |
| [`ILSP8IdentifiableDigitalAsset.sol`]                 | 45   | Interface that describes the standard functions and events defined in the LSP8 Identifiable Digital Asset standard.                               |                                                                                                                                                                                                               |
| [`LSP8EnumerableInitAbstract.sol`]                    | 34   | Extension (Abstract proxy version) - to enable enumerating over the list of tokenIds.                                                             |                                                                                                                                                                                                               |
| [`LSP8Enumerable.sol`]                                | 32   | Extension (Standard version) - to enable enumerating over the list of tokenIds.                                                                   |                                                                                                                                                                                                               |
| [`LSP8CappedSupplyInitAbstract.sol`]                  | 29   | Extension (Abstract proxy version without a public `initialize(...)` function) - to define a maximum total supply of tokens.                      |                                                                                                                                                                                                               |
| [`LSP8CappedSupply.sol`]                              | 27   | Extension (Standard version) - to define a maximum total supply of tokens.                                                                        |                                                                                                                                                                                                               |
| [`LSP8IdentifiableDigitalAssetInitAbstract.sol`]      | 25   | Abstract Proxy version of the LSP8 standard without a public `initialize(...)` function.                                                          | `@erc725/smart-contracts`: [`ERC725YCore.sol`]                                                                                                                                                                |
| [`LSP8MintableInitAbstract.sol`]                      | 25   | Preset deployable contract (Abstract proxy version without a public `initialize(...)` function) - same as `LSP8Mintable.sol`                      |                                                                                                                                                                                                               |
| [`ILSP8CompatibleERC721.sol`]                         | 23   | Interface to enable backward compatibility between LSP8 and functions from the ERC721 standard.                                                   |                                                                                                                                                                                                               |
| [`LSP8IdentifiableDigitalAsset.sol`]                  | 21   | Standard version of the LSP8 standard.                                                                                                            | `erc725/smart-contracts`: [`ERC725YCore.sol`]                                                                                                                                                                 |
| [`LSP8CompatibleERC721MintableInitAbstract.sol`]      | 19   | Preset deployable contract (Abstract Proxy version without a public `initialize(...)` function) - same as `LSP8Mintable.sol`.                     |                                                                                                                                                                                                               |
| [`LSP8Mintable.sol`]                                  | 18   | Preset deployable contract (Standard version) - contains a public `mint(...)` only callable by the owner.                                         |                                                                                                                                                                                                               |
| [`LSP8CompatibleERC721Mintable.sol`]                  | 17   | Preset deployable contract (Standard version) - same as `LSP8CompatibleERC721.sol` with a public `mint(...)` function only callable by the owner. |                                                                                                                                                                                                               |
| [`LSP8CompatibleERC721MintableInit.sol`]              | 16   | Preset deployable contract (Abstract Proxy version without a public `initialize(...)` function) - same as `LSP8CompatibleERC721Mintable.sol`      |                                                                                                                                                                                                               |
| [`LSP8Errors.sol`]                                    | 14   | Custom errors related to the internal logic of `LSP8IdentifiableDigitalAssetCore.sol`.                                                            |                                                                                                                                                                                                               |
| [`LSP8MintableInit.sol`]                              | 14   | Preset deployable contract (Proxy version) - same as `LSP8Mintable.sol`                                                                           |                                                                                                                                                                                                               |
| [`LSP8Burnable.sol`]                                  | 11   | Extension that implements a public `burn(...)` function for LSP8 to burn a specific `tokenId`.                                                    |                                                                                                                                                                                                               |
| [`ILSP8Mintable.sol`]                                 | 10   | Interface for a public `mint(...)` function for a LSP8 non-fungible token.                                                                        |                                                                                                                                                                                                               |
| [`LSP8Constants.sol`]                                 | 6    | Contains the standard ERC725Y metadata keys, LSP1 type IDs defined in the LSP8 standard, as well as its ERC165 interface ID.                      |                                                                                                                                                                                                               |
| **LSP14Ownable2Step**                                 |      |                                                                                                                                                   |                                                                                                                                                                                                               |
| [`LSP14Ownable2Step.sol`]                             | 81   | Core implementation of the LSP14 standard.                                                                                                        | `@erc725/smart-contracts/`: [`OwnableUnset.sol`]                                                                                                                                                              |
| [`ILSP14Ownable2Step.sol`]                            | 10   | Interface that describes the standard functions and events defined in the LSP14 Ownable 2 Step standard.                                          |                                                                                                                                                                                                               |
| [`LSP14Constants.sol`]                                | 5    | Contains the LSP1 type IDs defined in the LSP14 standard, as well as its ERC165 interface ID.                                                     |                                                                                                                                                                                                               |
| [`LSP14Errors.sol`]                                   | 3    | Custom errors related to the internal logic of `LSP14Ownable2Step.sol`.                                                                           |                                                                                                                                                                                                               |
| **LSP17ContractExtension**                            |      |                                                                                                                                                   |                                                                                                                                                                                                               |
| [`LSP17Extendable.sol`]                               | 36   | Core implementation of the LSP17 standard. Extendable contract fallback logic.                                                                    | `@openzeppelin/contracts/`: \[[`ERC165.sol`], [`ERC165Checker.sol`]\]                                                                                                                                         |
| [`LSP17Extension.sol`]                                | 17   | Core implementation of the LSP17 standard. Extension logic.                                                                                       | `@openzeppelin/contracts/`: [`ERC165.sol`]                                                                                                                                                                    |
| [`LSP17Constants.sol`]                                | 4    | Contains the standard ERC725Y metadata keys & ERC165 interface ID defined in the LSP17 standard.                                                  |                                                                                                                                                                                                               |
| [`LSP17Errors.sol`]                                   | 2    | Custom errors related to the internal logic of `LSP17Extendable.sol`.                                                                             |                                                                                                                                                                                                               |
| [`LSP17Utils.sol`]                                    | 9    | Library of utility functions used to help handling LSP17 Contract Extensins                                                                       |                                                                                                                                                                                                               |
| **LSP20CallVerification**                             |      |                                                                                                                                                   |                                                                                                                                                                                                               |
| [`LSP20CallVerification.sol`]                         | 42   | Core implementation of the LSP20 Standard.                                                                                                        |                                                                                                                                                                                                               |
| [`ILSP20CallVerification.sol`]                        | 9    | Interface that describes the standard functions and events defined in the LSP20 standard.                                                         |                                                                                                                                                                                                               |
| [`LSP20Constants.sol`]                                | 6    | Contains the ERC165 interface ID and return values defined in the LSP20 standard.                                                                 |                                                                                                                                                                                                               |
| [`LSP20Errors.sol`]                                   | 3    | Custom errors related to the internal logic of `LSP20CallVerification.sol`.                                                                       |                                                                                                                                                                                                               |
| **Other Libraries & Constants**                       |      |                                                                                                                                                   |                                                                                                                                                                                                               |
| [`EIP191Signer.sol`]                                  | 9    | Library of functions to construct signed hash of data with intended validator.                                                                    |                                                                                                                                                                                                               |
| [`LSP2Utils.sol`] (only 4 functions in scope)         |      | Library of functions to construct ERC725Y Data Keys based on their key type defined by a LSP2 JSON Schema.                                        | `solidity-bytes-utils`: [`BytesLib.sol`]                                                                                                                                                                      |
| - [`generateArrayElementKeyAtIndex(bytes32,uint128)`] | 7    |                                                                                                                                                   |                                                                                                                                                                                                               |
| - [`generateMappingKey(bytes10,bytes20)`]             | 7    |                                                                                                                                                   |                                                                                                                                                                                                               |
| - [`generateMappingWithGroupingKey(bytes10,bytes20)`] | 7    |                                                                                                                                                   |                                                                                                                                                                                                               |
| - [`isCompactBytesArray(bytes)`]                      | 12   |                                                                                                                                                   |                                                                                                                                                                                                               |
| [`LSP5Utils.sol`]                                     | 103  | Library of functions to register and manage assets stored in an ERC725Y smart contract storage.                                                   | `solidity-bytes-utils`: [`BytesLib.sol`]                                                                                                                                                                      |
| [`LSP5Constants.sol`]                                 | 3    | Contains the standard ERC725Y metadata keys, defined in the LSP5 standard.                                                                        |                                                                                                                                                                                                               |
| [`LSP10Utils.sol`]                                    | 98   | Library of functions to register and manage vaults stored in an ERC725Y smart contract storage.                                                   | `solidity-bytes-utils`: [`BytesLib.sol`]                                                                                                                                                                      |
| [`LSP10Constants.sol`]                                | 3    | Contains the standard ERC725Y metadata keys, defined in the LSP10 standard.                                                                       |                                                                                                                                                                                                               |

## Out of scope

_List any files/contracts that are out of scope for this audit._

# Additional Context

_Describe any novel or unique curve logic or mathematical models implemented in the contracts_

_Sponsor, please confirm/edit the information below._

## Scoping Details

```
- If you have a public code repo, please share it here:  https://github.com/lukso-network/lsp-smart-contracts
- How many contracts are in scope?:   53
- Total SLoC for these contracts?:  3469
- How many external imports are there?: 3
- How many separate interfaces and struct definitions are there for the contracts within scope?:  14
- Does most of your code generally use composition or inheritance?:   Inheritance
- How many external calls?:   0
- What is the overall line coverage percentage provided by your tests?:  90
- Is there a need to understand a separate part of the codebase / get context in order to audit this part of the protocol?:   True
- Please describe required context:   Understanding of ERC725 + the LSP standards
- Does it use an oracle?:  No
- Does the token conform to the ERC20 standard?:  True
- Are there any novel or unique curve logic or mathematical models?: The ERC725Account is a blockchain account, that can do several stuff execution, setting data, validating signatures, receiving and reacting on universalReceiver calls, extend the account with extensions.  The owner can execute certain functions, as well as addresses allowed by the logic of the owner. (If the caller is not the owner, verification is forwarded to the owner)  The LSP6KeyManager is a smart contract that can own the ERC725Account and allow certain calls to the account linked (ERC725Account) based on the permissions of the caller which are stored in the ERC725Account. Also this contract allows relay execution.  LSP1UniversalReceiverDelegate is a contract design to be set as a UniversalReceiverDelegate of the account to react on certain universalReceiver calls, to register the asset of the tokens and vaults received. LSP7 and LSP8 are new token standards based on LSP4 that allow adding metadata to the tokens contracts themselves. Their interface is built in a unified way, using the same functions for transferring tokens and approving operators, including the same number of parameters (and their types) for these functions. They also include features via LSP1 to notify the sender and the recipient on transfer of receiving tokens.
- Does it use a timelock function?:
- Is it an NFT?: True
- Does it have an AMM?:
- Is it a fork of a popular project?: False
- Does it use rollups?:
- Is it multi-chain?:
- Does it use a side-chain?:
```

# Tests

_Provide every step required to build the project from a fresh git clone, as well as steps to run the tests with a gas report._

_Note: Many wardens run Slither as a first pass for testing. Please document any known errors with no workaround._

# Slither

Any known issues from Slither for each contract are listed under the [`slither/`](./slither/) folder in this repository. We encourage reporting any bugs around them and not just the errors on their own. Slither errors without some proven negative impact will be considered as known issues.

<!-- Global Links -->
<!-- prettier-ignore-start -->

[`LSP0ERC725AccountCore.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP0ERC725Account/LSP0ERC725AccountCore.sol
[`LSP0Utils.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP0ERC725Account/LSP0Utils.sol
[`LSP0ERC725AccountInitAbstract.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP0ERC725Account/LSP0ERC725AccountInitAbstract.sol
[`ILSP0ERC725Account.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP0ERC725Account/ILSP0ERC725Account.sol
[`LSP0ERC725Account.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP0ERC725Account/LSP0ERC725Account.sol
[`LSP0ERC725AccountInit.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP0ERC725Account/LSP0ERC725AccountInit.sol
[`LSP0Constants.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP0ERC725Account/LSP0Constants.sol

---

[`UniversalProfileInitAbstract.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/UniversalProfileInitAbstract.sol
[`UniversalProfile.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/UniversalProfile.sol
[`UniversalProfileInit.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/UniversalProfileInit.sol

---

[`LSP1UniversalReceiverDelegateUP.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP1UniversalReceiver/LSP1UniversalReceiverDelegateUP/LSP1UniversalReceiverDelegateUP.sol
[`LSP1Utils.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP1UniversalReceiver/LSP1Utils.sol
[`LSP1UniversalReceiverDelegateVault.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP1UniversalReceiver/LSP1UniversalReceiverDelegateVault/LSP1UniversalReceiverDelegateVault.sol
[`ILSP1UniversalReceiver.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP1UniversalReceiver/ILSP1UniversalReceiver.sol
[`LSP1Constants.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP1UniversalReceiver/LSP1Constants.sol
[`LSP1Errors.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP1UniversalReceiver/LSP1Errors.sol

---

[`LSP4DigitalAssetMetadataInitAbstract.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP4DigitalAssetMetadata/LSP4DigitalAssetMetadataInitAbstract.sol
[`LSP4DigitalAssetMetadata.sol`]: chttps://github.com/code-423n4/2023-06-lukso/tree/main/ontracts/LSP4DigitalAssetMetadata/LSP4DigitalAssetMetadata.sol
[`LSP4Compatibility.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP4DigitalAssetMetadata/LSP4Compatibility.sol
[`LSP4Constants.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP4DigitalAssetMetadata/LSP4Constants.sol
[`ILSP4Compatibility.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP4DigitalAssetMetadata/ILSP4Compatibility.sol
[`LSP4Errors.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP4DigitalAssetMetadata/LSP4Errors.sol

---

[`LSP6SetDataModule.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP6KeyManager/LSP6Modules/LSP6SetDataModule.sol
[`LSP6KeyManagerCore.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP6KeyManager/LSP6KeyManagerCore.sol
[`LSP6ExecuteModule.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP6KeyManager/LSP6Modules/LSP6ExecuteModule.sol
[`LSP6Utils.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP6KeyManager/LSP6Utils.sol
[`LSP6Constants.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP6KeyManager/LSP6Constants.sol
[`ILSP6KeyManager.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP6KeyManager/ILSP6KeyManager.sol
[`LSP6Errors.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP6KeyManager/LSP6Errors.sol
[`LSP6OwnershipModule.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP6KeyManager/LSP6Modules/LSP6OwnershipModule.sol
[`LSP6KeyManagerInitAbstract.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP6KeyManager/LSP6KeyManagerInitAbstract.sol
[`LSP6KeyManager.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP6KeyManager/LSP6KeyManager.sol
[`LSP6KeyManagerInit.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP6KeyManager/LSP6KeyManagerInit.sol

---

[`LSP7DigitalAssetCore.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP7DigitalAsset/LSP7DigitalAssetCore.sol
[`LSP7CompatibleERC20InitAbstract.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP7DigitalAsset/extensions/LSP7CompatibleERC20InitAbstract.sol
[`LSP7CompatibleERC20.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP7DigitalAsset/extensions/LSP7CompatibleERC20.sol
[`ILSP7DigitalAsset.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP7DigitalAsset/ILSP7DigitalAsset.sol
[`LSP7DigitalAssetInitAbstract.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP7DigitalAsset/LSP7DigitalAssetInitAbstract.sol
[`LSP7CappedSupply.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP7DigitalAsset/extensions/LSP7CappedSupply.sol
[`LSP7CappedSupplyInitAbstract.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP7DigitalAsset/extensions/LSP7CappedSupplyInitAbstract.sol
[`LSP7DigitalAsset.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP7DigitalAsset/LSP7DigitalAsset.sol
[`LSP7MintableInitAbstract.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP7DigitalAsset/presets/LSP7MintableInitAbstract.sol
[`LSP7CompatibleERC20MintableInitAbstract.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP7DigitalAsset/presets/LSP7CompatibleERC20MintableInitAbstract.sol
[`LSP7Mintable.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP7DigitalAsset/presets/LSP7Mintable.sol
[`LSP7CompatibleERC20Mintable.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP7DigitalAsset/presets/LSP7CompatibleERC20Mintable.sol
[`LSP7Errors.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP7DigitalAsset/LSP7Errors.sol
[`LSP7CompatibleERC20MintableInit.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP7DigitalAsset/presets/LSP7CompatibleERC20MintableInit.sol
[`LSP7MintableInit.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP7DigitalAsset/presets/LSP7MintableInit.sol
[`ILSP7CompatibleERC20.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP7DigitalAsset/extensions/ILSP7CompatibleERC20.sol
[`ILSP7Mintable.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP7DigitalAsset/presets/ILSP7Mintable.sol
[`LSP7Burnable.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP7DigitalAsset/extensions/LSP7Burnable.sol
[`LSP7BurnableInitAbstract.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP7DigitalAsset/extensions/LSP7BurnableInitAbstract.sol
[`LSP7Constants.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP7DigitalAsset/LSP7Constants.sol

---

[`LSP8IdentifiableDigitalAssetCore.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP8IdentifiableDigitalAsset/LSP8IdentifiableDigitalAssetCore.sol
[`LSP8CompatibleERC721InitAbstract.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP8IdentifiableDigitalAsset/extensions/LSP8CompatibleERC721InitAbstract.sol
[`LSP8CompatibleERC721.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP8IdentifiableDigitalAsset/extensions/LSP8CompatibleERC721.sol
[`ILSP8IdentifiableDigitalAsset.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP8IdentifiableDigitalAsset/ILSP8IdentifiableDigitalAsset.sol
[`LSP8EnumerableInitAbstract.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP8IdentifiableDigitalAsset/extensions/LSP8EnumerableInitAbstract.sol
[`LSP8Enumerable.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP8IdentifiableDigitalAsset/extensions/LSP8Enumerable.sol
[`LSP8CappedSupplyInitAbstract.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP8IdentifiableDigitalAsset/extensions/LSP8CappedSupplyInitAbstract.sol
[`LSP8CappedSupply.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP8IdentifiableDigitalAsset/extensions/LSP8CappedSupply.sol
[`LSP8IdentifiableDigitalAssetInitAbstract.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP8IdentifiableDigitalAsset/LSP8IdentifiableDigitalAssetInitAbstract.sol
[`LSP8MintableInitAbstract.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP8IdentifiableDigitalAsset/presets/LSP8MintableInitAbstract.sol
[`ILSP8CompatibleERC721.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP8IdentifiableDigitalAsset/extensions/ILSP8CompatibleERC721.sol
[`LSP8IdentifiableDigitalAsset.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP8IdentifiableDigitalAsset/LSP8IdentifiableDigitalAsset.sol
[`LSP8CompatibleERC721MintableInitAbstract.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP8IdentifiableDigitalAsset/presets/LSP8CompatibleERC721MintableInitAbstract.s
[`LSP8Mintable.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP8IdentifiableDigitalAsset/presets/LSP8Mintable.sol
[`LSP8CompatibleERC721Mintable.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP8IdentifiableDigitalAsset/presets/LSP8CompatibleERC721Mintable.sol
[`LSP8CompatibleERC721MintableInit.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP8IdentifiableDigitalAsset/presets/LSP8CompatibleERC721MintableInit.sol
[`LSP8Errors.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP8IdentifiableDigitalAsset/LSP8Errors.sol
[`LSP8MintableInit.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP8IdentifiableDigitalAsset/presets/LSP8MintableInit.sol
[`LSP8Burnable.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP8IdentifiableDigitalAsset/extensions/LSP8Burnable.sol
[`ILSP8Mintable.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP8IdentifiableDigitalAsset/presets/ILSP8Mintable.sol
[`LSP8Constants.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP8IdentifiableDigitalAsset/LSP8Constants.s

---

[`LSP14Ownable2Step.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP14Ownable2Step/LSP14Ownable2Step.sol
[`ILSP14Ownable2Step.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP14Ownable2Step/ILSP14Ownable2Step.sol
[`LSP14Constants.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP14Ownable2Step/LSP14Constants.sol
[`LSP14Errors.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP14Ownable2Step/LSP14Errors.sol

---

[`LSP17Extendable.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP17ContractExtension/LSP17Extendable.sol
[`LSP17Extension.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP17ContractExtension/LSP17Extension.sol
[`LSP17Constants.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP17ContractExtension/LSP17Constants.sol
[`LSP17Errors.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP17ContractExtension/LSP17Errors.sol
[`LSP17Utils.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP17ContractExtension/LSP17Utils.sol

---

[`LSP20CallVerification.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP20CallVerification/LSP20CallVerification.sol
[`ILSP20CallVerification.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP20CallVerification/ILSP20CallVerification.sol
[`LSP20Constants.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP20CallVerification/LSP20Constants.sol
[`LSP20Errors.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP20CallVerification/LSP20Errors.sol

---

[`EIP191Signer.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/Custom/EIP191Signer.sol
[`LSP2Utils.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP2ERC725YJSONSchema/LSP2Utils.sol
[`generateArrayElementKeyAtIndex(bytes32,uint128)`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP2ERC725YJSONSchema/LSP2Utils.sol#L48
[`generateMappingKey(bytes10,bytes20)`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP2ERC725YJSONSchema/LSP2Utils.sol#L108
[`generateMappingWithGroupingKey(bytes10,bytes20)`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP2ERC725YJSONSchema/LSP2Utils.sol#L165
[`isCompactBytesArray(bytes)`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP2ERC725YJSONSchema/LSP2Utils.sol#L288
[`LSP5Utils.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP5ReceivedAssets/LSP5Utils.sol
[`LSP5Constants.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP5ReceivedAssets/LSP5Constants.sol
[`LSP10Utils.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP10ReceivedVaults/LSP10Utils.sol
[`LSP10Constants.sol`]: https://github.com/code-423n4/2023-06-lukso/tree/main/contracts/LSP10ReceivedVaults/LSP10Constants.sol

<!-- Links to Specs -->

[ERC-725]: https://github.com/ERC725Alliance/ERC725/blob/develop/docs/ERC-725.md
[LSP-0-ERC725Account]: https://github.com/lukso-network/LIPs/blob/main/LSPs/LSP-0-ERC725Account.md
[LSP-1-UniversalReceiver]: https://github.com/lukso-network/LIPs/blob/main/LSPs/LSP-1-UniversalReceiver.md
[LSP-2-ERC725YJSONSchema]: https://github.com/lukso-network/LIPs/blob/main/LSPs/LSP-2-ERC725YJSONSchema.md
[LSP-3-UniversalProfile-Metadata]: https://github.com/lukso-network/LIPs/blob/main/LSPs/LSP-3-UniversalProfile-Metadata.md
[LSP-4-DigitalAsset-Metadata]: https://github.com/lukso-network/LIPs/blob/main/LSPs/LSP-4-DigitalAsset-Metadata.md
[LSP-6-KeyManager]: https://github.com/lukso-network/LIPs/blob/main/LSPs/LSP-6-KeyManager.md
[LSP-5-ReceivedAssets]: https://github.com/lukso-network/LIPs/blob/main/LSPs/LSP-5-ReceivedAssets.md
[LSP-7-DigitalAsset]: https://github.com/lukso-network/LIPs/blob/main/LSPs/LSP-7-DigitalAsset.md
[LSP-8-IdentifiableDigitalAsset]: https://github.com/lukso-network/LIPs/blob/main/LSPs/LSP-8-IdentifiableDigitalAsset.md
[LSP-10-ReceivedVaults]: https://github.com/lukso-network/LIPs/blob/main/LSPs/LSP-10-ReceivedVaults.md
[LSP-14-Ownable2Step]: https://github.com/lukso-network/LIPs/blob/main/LSPs/LSP-14-Ownable2Step.md
[LSP-17-ContractExtension]: https://github.com/lukso-network/LIPs/blob/main/LSPs/LSP-17-ContractExtension.md
[LSP-20-CallVerification]: https://github.com/lukso-network/LIPs/blob/main/LSPs/LSP-20-CallVerification.md

<!-- Links to Docs --->

[ERC725]: https://docs.lukso.tech/standards/lsp-background/erc725
[UniversalProfile]: https://docs.lukso.tech/standards/universal-profile/introduction
[LSP0ERC725Account]: https://docs.lukso.tech/standards/universal-profile/lsp0-erc725account
[LSP1UniversalReceiver]: https://docs.lukso.tech/standards/generic-standards/lsp1-universal-receiver
[LSP1UniversalReceiverDelegate]: https://docs.lukso.tech/standards/generic-standards/lsp1-universal-receiver-delegate
[LSP2ERC725YJSONSchema]: https://docs.lukso.tech/standards/generic-standards/lsp2-json-schema
[LSP4DigitalAsset]: https://docs.lukso.tech/standards/nft-2.0/LSP4-Digital-Asset-Metadata
[LSP6KeyManager]: https://docs.lukso.tech/standards/universal-profile/lsp5-received-assets
[LSP5ReceivedVaults]: https://docs.lukso.tech/standards/universal-profile/lsp6-key-manager
[LSP7DigitalAsset]: https://docs.lukso.tech/standards/nft-2.0/LSP7-Digital-Asset
[LSP8IdentifiableDigitalAsset]: https://docs.lukso.tech/standards/nft-2.0/LSP8-Identifiable-Digital-Asset
[LSP10ReceivedVaults]: https://docs.lukso.tech/standards/universal-profile/lsp10-received-vaults
[LSP14Ownable2Step]: https://docs.lukso.tech/standards/generic-standards/lsp14-ownable-2-step
[LSP17ContractExtension]: https://docs.lukso.tech/standards/generic-standards/lsp17-contract-extension
[LSP20CallVerification]: https://docs.lukso.tech/standards/generic-standards/lsp20-call-verification

<!-- Links to Libraries -->

[`ECDSA.sol`]: https://github.com/OpenZeppelin/openzeppelin-contracts/blob/v4.9.2/contracts/utils/cryptography/ECDSA.sol
[`ERC165Checker.sol`]: https://github.com/OpenZeppelin/openzeppelin-contracts/blob/v4.9.2/contracts/utils/introspection/ERC165Checker.sol
[`Address.sol`]: https://github.com/OpenZeppelin/openzeppelin-contracts/blob/v4.9.2/contracts/utils/Address.sol
[`ERC165.sol`]: https://github.com/OpenZeppelin/openzeppelin-contracts/blob/v4.9.2/contracts/utils/introspection/ERC165.sol
[`Initializable.sol`]: https://github.com/OpenZeppelin/openzeppelin-contracts-upgradeable/blob/v4.9.2/contracts/proxy/utils/Initializable.sol
[`EnumerableSet.sol`]: https://github.com/OpenZeppelin/openzeppelin-contracts/blob/v4.9.2/contracts/utils/structs/EnumerableSet.sol
[`ERC725.constants.sol`]: https://github.com/ERC725Alliance/ERC725/blob/v5.1.0/implementations/contracts/constants.sol
[`ERC725Y.sol`]: https://github.com/ERC725Alliance/ERC725/blob/v5.1.0/implementations/contracts/ERC725Y.sol
[`ERC725YCore.sol`]: https://github.com/ERC725Alliance/ERC725/blob/v5.1.0/implementations/contracts/ERC725YCore.sol
[`ERC725X.sol`]: https://github.com/ERC725Alliance/ERC725/blob/v5.1.0/implementations/contracts/ERC725X.sol
[`ERC725XCore.sol`]: https://github.com/ERC725Alliance/ERC725/blob/v5.1.0/implementations/contracts/ERC725XCore.sol
[`OwnableUnset.sol`]: https://github.com/ERC725Alliance/ERC725/blob/v5.1.0/implementations/contracts/custom/OwnableUnset.sol
[`BytesLib.sol`]: https://github.com/GNSPS/solidity-bytes-utils/blob/v0.8.0/contracts/BytesLib.sol

<!-- prettier-ignore-end -->
