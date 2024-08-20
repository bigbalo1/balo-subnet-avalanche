
---

# BigBallo Token and Vault Smart Contracts

This repository contains the Solidity code for the `BigBallo` ERC20 token and a `Vault` contract designed to work on the `bigballo` blockchain network, which is a custom Avalanche subnet.

## Overview

### BigBallo Token (ERC20)

The `BigBallo` token is a simple implementation of the ERC20 standard. It includes functionalities to mint and burn tokens, transfer tokens between accounts, and approve allowances for third-party spending.

#### Key Features

- **Name:** BigBallo
- **Symbol:** balo
- **Decimals:** 18

#### Contract Functions

- **`transfer(address recipient, uint amount)`:** Transfer `amount` of tokens to `recipient`.
- **`approve(address spender, uint amount)`:** Approve `spender` to spend `amount` of tokens on behalf of the caller.
- **`transferFrom(address sender, address recipient, uint amount)`:** Transfer `amount` of tokens from `sender` to `recipient` using the allowance mechanism.
- **`mint(uint amount)`:** Mint `amount` of new tokens to the caller's address, increasing the total supply.
- **`burn(uint amount)`:** Burn `amount` of tokens from the caller's address, reducing the total supply.

### Vault Contract

The `Vault` contract is designed to allow users to deposit and withdraw `BigBallo` tokens. The Vault mints shares corresponding to the amount of tokens deposited and burns shares when tokens are withdrawn.

#### Key Features

- **Deposit:** Users can deposit `BigBallo` tokens and receive shares in return.
- **Withdraw:** Users can burn their shares to withdraw the corresponding amount of `BigBallo` tokens.

#### Contract Functions

- **`deposit(uint _amount)`:** Deposit `_amount` of `BigBallo` tokens into the Vault. Shares are minted in proportion to the amount deposited.
- **`withdraw(uint _shares)`:** Withdraw an amount of `BigBallo` tokens corresponding to `_shares`. Shares are burned in the process.

### Mathematical Calculations

The vault uses the following formulas:

- **Deposit:** `shares = (_amount * totalSupply) / tokenBalance` (if the total supply is not zero).
- **Withdraw:** `amount = (_shares * tokenBalance) / totalSupply`.

These calculations ensure that the value of shares is proportionate to the tokens held in the Vault.

## Deployment

### Avalanche Subnet Details

The contracts are deployed on a custom Avalanche subnet named **bigballo** with the following details:

- **Network Name:** bigballo
- **Chain ID:** 30102020
- **Currency Symbol:** bal

### Deploying the Contracts

1. **Deploy the BigBallo Token:**
   Deploy the ERC20 contract with the name `BigBallo` and symbol `balo`.

2. **Deploy the Vault Contract:**
   Deploy the `Vault` contract by passing the address of the deployed `BigBallo` token contract to its constructor.

### Interacting with the Contracts

#### Using Remix or Hardhat

- **Deposit Tokens:** Call the `deposit()` function on the `Vault` contract, passing the amount of `BigBallo` tokens you wish to deposit.
- **Withdraw Tokens:** Call the `withdraw()` function on the `Vault` contract, passing the number of shares you wish to redeem for `BigBallo` tokens.

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

---
