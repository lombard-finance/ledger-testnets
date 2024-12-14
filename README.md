# Testnets

```bash

# Initialize
ledgerd init lombard --chain-id ledger-testnet-1 --default-denom ustake --home gastald
ledgerd config set client chain-id ledger-testnet-1 --home gastald
ledgerd config set client keyring-backend test --home gastald

# Distribute initial balance of validators and faucet
ledgerd genesis add-genesis-account lom1fy4n7w5l60kx3vgcftmpxxth9s5tzqt4swqgvy "102000000ulom" --home gastald
ledgerd genesis add-genesis-account lom13dvuxs0ms2gfw60vs8knwq83ctngn3xpe7zche "17446744073709551615ulom" --home gastald
ledgerd genesis add-genesis-account lom1a4ynu6r0x7chs87729xc7klj3p0mxrc3pz2dmu "102000000ulom,1000ustake" --home gastald
ledgerd genesis add-genesis-account lom1w5yuz8mn39pkrva3vvpukl3qnm5e3tvpa6wh87 "102000000ulom,1000ustake" --home gastald
ledgerd genesis add-genesis-account lom15ddatgjaze3n733lye5ryl8yadst22ylm9503s "102000000ulom,1000ustake" --home gastald
# Grant significant amount of ustake to gov module
ledgerd genesis add-genesis-account lom10d07y265gmmuvt4z0w9aw880jnsr700jwkzx46 "21000000ustake" --home gastald --module-name gov

# Distribute initial balance of proxies
ledgerd genesis add-genesis-account lom163enmx0d9gyseuagczfnw9kf3hp7zlqzm3c793 "4000000ulom" --home gastald
ledgerd genesis add-genesis-account lom1k04ddjpvztzz00h73rcjljr487xzt5x28un0ne "4000000ulom" --home gastald
ledgerd genesis add-genesis-account lom17388ntu5wkhe3jxm8tfnvfmgw6ctr2n9lswnh7 "4000000ulom" --home gastald
ledgerd genesis add-genesis-account lom122k4y2jsdzllqrme6ggf75ph6kz07863gnx5va "4000000ulom" --home gastald
```

Collect gentx
```bash
ledgerd genesis collect-gentxs --home gastald
```

Modify genesis

* `app_state.distribution.params.community_tax = "0.000000000000000000"`
* `app_state.gov.min_deposit.denom = "ulom"`
* `app_state.gov.min_deposit.amount = "1000000"`
* `app_stage.gov.max_deposit_period = "600s"` 1h
* `app_stage.gov.voting_period = "14400s"` 4h
* `app_stage.gov.expedited_voting_period = "7200s"` 2h
* `app_stage.gov.expedited_min_deposit.denom = "ulom"`
* `app_stage.gov.expedited_min_deposit.amount = "500000000"`
* `app_stage.mint.minter.inflation = "0.000000000000000000"`
* `app_stage.mint.params.mint_denom = "ulom"`
* `app_stage.mint.params.inflation_rate_change = "0.000000000000000000"`
* `app_stage.mint.params.inflation_max = "0.000000000000000000"`
* `app_stage.mint.params.inflation_min = "0.000000000000000000"`
* `app_stage.notary.params.notary_threshold.numerator = "70"`
* `app_stage.notary.params.notary_bridge_deposit_period = "60"`
* `app_stage.notary.params.notary_unstake_period = "60"`
* `app_stage.notary.params.notary_unstake_execution_period = "30"`
* `app_stage.slashing.params.signed_blocks_window = "10000"`
* `app_stage.slashing.params.downtime_jail_duration = "60m0s"`
* `app_stage.slashing.params.slash_fraction_downtime = "0.000100000000000000"`
* `app_stage.staking.params.unbonding_time = "1209600s"` 2w
* `app_stage.staking.params.max_validators = 4`
* `consensus.params.block.max_bytes = "2097152"`
* `consensus.params.block.max_gas = "20000000"`

Validate genesis:
```bash
ledgerd genesis validate --home gastald
```
