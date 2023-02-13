# Redacted v2

Reward Distributor (Mainnet): [`0xd7807E5752B368A6a64b76828Aaff0750522a76E`](https://etherscan.io/address/0xd7807E5752B368A6a64b76828Aaff0750522a76E)

> #### Important note:
>
> _Distribution data contains ALL rewards, including those that have already been claimed_.
>
> In order to calculate the _current_ rewards (amount of rewards that have not yet been claimed), you must subtract the claimed rewards from the total rewards.
>
> You may query the [RewardDistributor](https://etherscan.io/address/0xd7807E5752B368A6a64b76828Aaff0750522a76E) for previous claims using the `claimed` method and passing in `rewardTokenAddress` and `walletAddress` as parameters, eg:
>
> ```ts
> const amount = await contract.claimed(
>   '0xa52fd396891e7a74b641a2cb1a6999fcf56b077e', // ETH mapping
>   '0x0000000000000000000000000000000000000000' // Wallet address
> )
> ```
>
> You would then subtract this amount from the total contained in `./latest/eth.json`

### Token mappings

Note: ETH rewards are represented by the [Redacted Gnosis Multisig Address](https://etherscan.io/address/0xa52fd396891e7a74b641a2cb1a6999fcf56b077e).

- BTRFLY: `0xc55126051b22ebb829d00368f4b12bde432de5da`
- ETH: `0xa52fd396891e7a74b641a2cb1a6999fcf56b077e`

### Directory structure

```
.
└── protocol-v2           # Redacted v2
    ├── latest            # Aggregated distribution data for all epochs
    │   ├── btrfly.json   # BTRFLY distribution data
    │   └── eth.json      # ETH distribution data
    └── 1674691200        # Distribution at epoch timestamp (UTC)
        ├── btrfly.json
        └── eth.json
```
