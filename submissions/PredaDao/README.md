# Preda Decentralized Autonomous Organization (DAO) Contract

This project implements a Decentralized Autonomous Organization (DAO) smart contract on the Preda platform. Preda is a blockchain language that enables the creation and execution of smart contracts in a secure and decentralized environment.

## Contracts

### 1. DAOContract

The main DAO contract that orchestrates the interaction between other contracts.

#### Functions:

- `addController(address controller)`: Add a controller to the DAO. Only the owner can add controllers.

- `initializeContracts(address tokenAddress, address membershipAddress, address votingAddress)`: Initialize the DAO with Token, Membership, and Voting contracts.

- `createProposal(string description, uint256 amount)`: Create a proposal within the DAO.

- `vote(uint32 proposalId, bool support)`: Vote on a proposal.

- `executeProposal(uint32 proposalId)`: Execute a proposal.

- `getProposalDetails(uint32 proposalId)`: Retrieve details of a specific proposal.

### 2. Membership

A contract managing the membership of the DAO.

#### Functions:

- `addMember(address newMember)`: Add a new member to the DAO.

- `removeMember(address member)`: Remove a member from the DAO.

- `isMember(address account)`: Check if an address is a member.

### 3. Token

A basic token contract used within the DAO for voting power.

### 4. Voting

A contract handling the creation, voting, and execution of proposals.

#### Functions:

- `createProposal(string description, address proposer, uint256 amount)`: Create a proposal.

- `vote(uint32 proposalId, address voter, bool support)`: Vote on a proposal.

- `executeProposal(uint32 proposalId, address executor)`: Execute a proposal.

- `getProposalDetails(uint32 proposalId)`: Retrieve details of a specific proposal.

## Usage

1. Deploy the individual contracts on the Pragma platform.

2. Initialize the DAOContract with the addresses of Token, Membership, and Voting contracts.

3. Interact with the DAOContract functions to manage controllers, create proposals, and execute actions based on voting.

## ScriptArgs Configuration

The `scriptArgs.json` file specifies the dependencies and relationships between different contracts. Make sure to configure it according to the structure of your project.

## Contributors

- Sambit Sargam Ekalabya
