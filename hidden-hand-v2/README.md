# Hidden Hand

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

### Important note:

_Distribution data contains ALL rewards, including those that have already been claimed_.

In order to calculate the _current_ rewards (amount of rewards that have not yet been claimed), you must subtract the claimed rewards from the total rewards.

You may query the [RewardDistributor](https://etherscan.io/address/0xa9b08B4CeEC1EF29EdEC7F9C94583270337D6416) for previous claims using the `claimed` method and passing in the `rewardIdentifier` (keccak256 hash of `PROTOCOL` + `rewardTokenAddress`) and `walletAddress` as parameters, eg:

```ts
const amount = await contract.claimed(
   '0x0000000000000000000000000000000000000000', // Reward Identifier
   '0x0000000000000000000000000000000000000000' // Wallet address
)
```

You would then subtract this amount from the total contained in `./latest/market/network/0xRewardToken.json`

### Reward Distributor Deployments

| Network         | ChainId | Reward Distributor Address  |
|-----------------|---| -----------------------------------------|
| Mainnet         | 1| [`0xa9b08B4CeEC1EF29EdEC7F9C94583270337D6416`](https://etherscan.io/address/0xa9b08B4CeEC1EF29EdEC7F9C94583270337D6416)
| Optimism        | 10| [`0x7354BB6842E421773E7b78f8875A1B85991677c0`](https://optimistic.etherscan.io/address/0x7354BB6842E421773E7b78f8875A1B85991677c0)
| Arbitrum        | 42161 | [`0x0A390DE04B7717B078CF5c8A7Eb891130d4a843b`](https://arbiscan.io/address/0x0A390DE04B7717B078CF5c8A7Eb891130d4a843b)
| BSC             | 56| [`0x9a66b0F857D15de7ACc9F524F60b9e3503d7C105`](https://bscscan.com/address/0x9a66b0F857D15de7ACc9F524F60b9e3503d7C105)
| Fantom          | 250| [`0x833a79e66d2cE0d5F5fdF8d213c9c02192cdF999`](https://ftmscan.com/address/0x833a79e66d2cE0d5F5fdF8d213c9c02192cdF999)
