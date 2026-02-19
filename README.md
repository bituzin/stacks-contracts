# Stacks Smart Contracts Collection

This repository contains a set of useful smart contracts for the Stacks blockchain network, written in Clarity 4. These contracts demonstrate practical use cases and functionalities that can be leveraged in decentralized applications (dApps) on Stacks.

## Overview


Each `.clar` file in this repository represents a different smart contract, covering a variety of features such as:
- Token standards (SIP-009, SIP-010)
- NFT management
- Liquidity pools
- Multisending
- Oracles
- Staking
- Voting
- Timelocks
- Vaults and more

## New and Updated Contracts (suffix -05)

The following contracts (ending with `-05.clar`) have been recently added or updated for the MineStxweeper app:

- **achievement-nft-05.clar** – NFT achievements for players
- **board-generator-05.clar** – Board generation logic for the game
- **daily-challenge-05.clar** – Daily challenge management
- **economy-05.clar** – In-game economy and rewards
- **game-core-05.clar** – Core game logic and state
- **gm-05.clar** – Good-morning (GM) interaction contract
- **leaderboard-05.clar** – Leaderboard tracking and ranking
- **player-profile-05.clar** – Player profile and stats
- **tournament-05.clar** – Tournament management
- **wager-05.clar** – Wagering and betting logic
- **win-checker-05.clar** – Win condition verification

These contracts are tailored for the MineStxweeper dApp and provide modular, up-to-date logic for game features, player engagement, and rewards.

## Recent Improvements

- **Event Logging:** All contracts now emit detailed events (`print`) for every state-changing operation, making it easy to track actions on-chain and integrate with off-chain indexers.
- **Code Consistency:** Event names and code style have been unified across all contracts for easier maintenance and readability.
- **Input Validation:** Most public functions include input validation and error handling for better security.
- **Ready for Testing:** Contracts are structured to be easily testable with tools like Clarinet. You can add unit tests for each contract to ensure reliability.

## How to Test

1. Install [Clarinet](https://docs.hiro.so/clarinet/get-started/installation) or another Stacks smart contract testing tool.
2. Write test cases for each contract in the `tests/` directory (see Clarinet documentation for examples).
3. Run `clarinet test` to execute all tests and verify contract logic.

Example test (TypeScript, Clarinet):
```typescript
import { Clarinet, Tx, Chain, Account } from "clarinet-sdk";

Clarinet.test({
	name: "Mint badge should succeed for owner",
	async fn(chain: Chain, accounts: Map<string, Account>) {
		let owner = accounts.get("deployer")!;
		let recipient = accounts.get("wallet_1")!;
		let block = chain.mineBlock([
			Tx.contractCall("badges-002", "mint-badge", [
				recipient.address, "u100", '"BadgeName"', '"Desc"', '"img"'
			], owner.address)
		]);
		block.receipts[0].result.expectOk();
	}
});
```

## License
MIT
