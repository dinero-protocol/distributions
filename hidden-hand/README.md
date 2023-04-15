# Hidden Hand

Reward Distributor (Mainnet): [`0x0b139682d5c9df3e735063f46fb98c689540cf3a`](https://etherscan.io/address/0x0b139682d5c9df3e735063f46fb98c689540cf3a)
Reward Distributor (Optimism): [`0x0b139682D5C9Df3e735063f46Fb98c689540Cf3A`](https://optimistic.etherscan.io/address/0x0b139682D5C9Df3e735063f46Fb98c689540Cf3A)

> #### Important note:
>
> _Distribution data contains ALL rewards, including those that have already been claimed_.
>
> In order to calculate the _current_ rewards (amount of rewards that have not yet been claimed), you must subtract the claimed rewards from the total rewards.
>
> You may query the [RewardDistributor](https://etherscan.io/address/0x0b139682d5c9df3e735063f46fb98c689540cf3a) for previous claims using the `claimed` method and passing in `rewardTokenAddress` and `walletAddress` as parameters, eg:
>
> ```ts
> const amount = await contract.claimed(
>   '0xRewardToken', // Reward token
>   '0x0000000000000000000000000000000000000000' // Wallet address
> )
> ```
>
> You would then subtract this amount from the total contained in `./latest/0xRewardToken.json`

### Token mappings

Note: ETH rewards are represented by the [BribeVault](https://etherscan.io/address/0x9DDb2da7Dd76612e0df237B89AF2CF4413733212).

- ETH: `0x9DDb2da7Dd76612e0df237B89AF2CF4413733212`

### Directory structure

```
.
└── aura                                # Protocol slug
    ├── 1                               # Chain ID (1 = Mainnet)
    │   ├── latest                      # Aggregated distribution data
    │   │   └── 0xRewardToken.json      # Rewards for token address
    │   └── 1674691200                  # Distribution at proposal deadline (UTC)
    │       └── 0xRewardToken.json
    └── 10                              # Chain ID (10 = Optimism)
        ├── latest
        │   └── 0xRewardToken.json
        └── 1674691200
            └── 0xRewardToken.json
```
