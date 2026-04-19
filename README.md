# MonstaFactory

Token factory ecosystem on **Monad Mainnet** (Chain ID 143).

Create, launch, and trade tokens with a fair bonding curve, automatic liquidity graduation, and built-in staking farms.

## Deployed Contracts (v10)

| Contract | Address |
|---|---|
| **TokenFactory** | [`0xd2AC0B4c32e2F2d81Dd27BA0Eaec71561d755983`](https://monadexplorer.com/address/0xd2AC0B4c32e2F2d81Dd27BA0Eaec71561d755983) |
| **FarmFactory** | [`0xE76b2273903850a27b22Ac8782d5041479846166`](https://monadexplorer.com/address/0xE76b2273903850a27b22Ac8782d5041479846166) |
| **BondingCurveToken** (impl) | [`0x7Af43F9e39681094B836eb03EFd187989f4C7da0`](https://monadexplorer.com/address/0x7Af43F9e39681094B836eb03EFd187989f4C7da0) |
| **FactoryRewardContract** (impl) | [`0x4AdCaDF4689E792b8A5B9Df0B1A9977cb8891CCa`](https://monadexplorer.com/address/0x4AdCaDF4689E792b8A5B9Df0B1A9977cb8891CCa) |
| **PerpetualFarm** (impl) | [`0x23F7A3b889b12fF8212eba7fbA73d4ef4C8a7327`](https://monadexplorer.com/address/0x23F7A3b889b12fF8212eba7fbA73d4ef4C8a7327) |

> Network: Monad Mainnet | RPC: `https://rpc.monad.xyz` | Chain ID: `143`

## Architecture

```
User creates token via TokenFactory
        |
        v
BondingCurveToken deployed (clone)
  - Fair bonding curve (buy/sell)
  - ForMonad Tax: 3% fixed (sells to WMON, rewards stakers)
        |
        v  (when bonding target reached)
Graduation
  - Liquidity added to Uniswap V3 (60/40 split)
  - PerpetualFarm auto-created via FarmFactory
  - FactoryRewardContract deployed for staking rewards
        |
        v
Free trading on Uniswap V3 + Staking on PerpetualFarm
```

## Key Mechanics

- **Bonding Curve**: Tokens start on a fair bonding curve. No presales, no rugs.
- **ForMonad Tax**: 3% tax on all trades (post-graduation). Batch-sells token for WMON and distributes to stakers.
- **Graduation Fee**: 5% of collected MON sent to factory as WMON at graduation.
- **Auto-Farm**: A staking farm is automatically created when a token graduates.
- **External Bonus**: Farm owners can deposit external token bonuses (whitelisted tokens or graduated MonstaFactory tokens).

## ABIs

Pure ABI JSON files for each contract are in the [`abi/`](./abi/) directory:

- [`BondingCurveToken.json`](./abi/BondingCurveToken.json) — ERC20 token with bonding curve
- [`TokenFactory.json`](./abi/TokenFactory.json) — Factory for creating tokens
- [`PerpetualFarm.json`](./abi/PerpetualFarm.json) — Staking farm for token rewards

## Documentation

- [Whitepaper (PDF)](./docs/MonstaFactory_Whitepaper.pdf)
- [Roadmap (PDF)](./docs/MonstaFactory_Roadmap.pdf)

## Key Addresses (Monad)

| Resource | Address |
|---|---|
| WMON | `0x3bd359C1119dA7Da1D913D1C4D2B7c461115433A` |
| Uniswap V3 Factory | `0x204faca1764b154221e35c0d20abb3c525710498` |
| NonfungiblePositionManager | `0x7197e214c0b767cfb76fb734ab638e2c192f4e53` |
| UniversalRouter | `0x0d97dc33264bfc1c226207428a79b26757fb9dc3` |

## Links

- Website: [monstafactory.xyz](https://monstafactory.xyz)
- Telegram: [t.me/monstafactory](https://t.me/monstafactory)
- Twitter/X: [x.com/Monstafactory](https://x.com/Monstafactory)

## License

All rights reserved. Contract ABIs and documentation are provided for integration purposes only.
