Collecting workspace information# StratumDAO

A full-layered governance DAO smart contract built on Stacks with multi-factor voting, delegation, and reward mechanisms.

## Overview

StratumDAO is a Clarity smart contract that implements a comprehensive decentralized autonomous organization (DAO) with:

- **Proposal Management**: Create, vote on, and execute governance proposals
- **Voting Delegation**: Delegate voting power to other participants
- **Reward System**: Earn tokens based on participation and voting activity
- **Multi-factor Scoring**: BTC holdings and participation metrics influence voting power
- **Execution Control**: Configurable delays and quorum thresholds for proposal execution

## Project Structure

```
StratumDAO/
├── contracts/
│   └── StratumDAO.clar          # Main Clarity smart contract
├── tests/
│   └── StratumDAO.test.ts       # Vitest unit tests
├── settings/
│   ├── Devnet.toml              # Devnet configuration with test accounts
│   ├── Testnet.toml             # Testnet settings
│   └── Mainnet.toml             # Mainnet settings
├── Clarinet.toml                # Project configuration
├── package.json                 # Dependencies and scripts
├── tsconfig.json                # TypeScript configuration
└── vitest.config.js             # Vitest configuration
```

## Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) (v16 or higher)
- [Clarinet](https://github.com/hirosystems/clarinet) CLI
- [Docker](https://www.docker.com/) (for Devnet)

### Installation

```sh
npm install
```

### Development

**Check contract syntax:**

```sh
clarinet check
```

**Run tests:**

```sh
npm run test
```

**Run tests with coverage and cost analysis:**

```sh
npm run test:report
```

**Watch mode (auto-rerun tests on file changes):**

```sh
npm run test:watch
```

## Key Features

### Data Structures

- **Proposals**: Store governance proposals with voting counts and execution status
- **Participation**: Track voter participation scores
- **BTC Holdings**: Record Bitcoin holdings for multi-chain governance weighting
- **Delegations**: Enable voting power delegation between participants
- **Voter Rewards**: Manage reward distribution for active participants

### Core Functions

| Function | Description |
|----------|-------------|
| `create-proposal` | Create a new governance proposal |
| `delegate-voting` | Delegate voting rights to another principal |
| `cancel-proposal` | Cancel an active proposal (creator only) |
| `execute-proposal` | Execute a proposal if quorum and voting conditions are met |
| `claim-rewards` | Claim accumulated voting rewards |
| `set-max-voting-power` | Set maximum voting power limit |
| `set-execution-delay` | Configure blocks to wait before execution |
| `set-btc-holding` | Record BTC holdings for a voter |

## Configuration

### Devnet Accounts

The Devnet.toml provides pre-configured test wallets:

- **deployer**: Contract deployer account
- **wallet_1 through wallet_8**: Test accounts with 100M STX each
- **faucet**: Faucet account for testing

### Contract Parameters

- **quorum-threshold**: Minimum votes (1000) required for proposal execution
- **reward-per-vote**: Token reward per vote cast (10 tokens)
- **participation-multiplier**: Weight factor for participation (50x)
- **reputation-multiplier**: Weight factor for reputation (30x)

## Testing

Tests are written using [Vitest](https://vitest.dev/) and the [Clarinet SDK](https://docs.hiro.so/stacks/clarinet-js-sdk):

```typescript
// Example test
describe("example tests", () => {
  it("ensures simnet is well initialised", () => {
    expect(simnet.blockHeight).toBeDefined();
  });
});
```
