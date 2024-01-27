# Decentralized Lending Platform

## Overview

This project is a simplified implementation of a decentralized lending platform built on the Preda blockchain. The platform consists of various smart contracts, each serving a specific purpose in the lending ecosystem.

## Contracts

### Token (Token.prd)

- Manages the native token used within the platform.
- Implements basic functionalities such as minting, transferring, and querying balances.

### Lending Pool (LendingPool.prd)

- Handles the lending pool where users can deposit their assets.
- Facilitates lending activities by allowing users to borrow against their deposited assets.

### Borrowing (Borrowing.prd)

- Governs the borrowing mechanism, enabling users to borrow assets from the lending pool.
- Implements features like collateral requirements, interest rates, and loan repayment.

### Governance (Governance.prd)

- Manages the governance system of the decentralized lending platform.
- Allows token holders to participate in decision-making processes and vote on proposals.

### DAO (DAO.prd)

- The Decentralized Autonomous Organization (DAO) that coordinates various aspects of the platform.
- Integrates Token, Lending Pool, Borrowing, and Governance contracts.

## Usage

- **Token Transactions**: Use the Token contract to mint, transfer, and manage the native token.
- **Lending and Borrowing**: Interact with the Lending Pool and Borrowing contracts to deposit assets, borrow funds, and repay loans.
- **Governance Participation**: Token holders can participate in the governance process through the Governance contract.
- **DAO Operations**: Coordinate various functionalities by interacting with the DAO contract.

## Contributors

- Sambit Sargam Ekalabya

## Acknowledgments

- Acknowledge any external libraries, tutorials, or resources you used.
