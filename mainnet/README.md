# Mainnet

| Validator | acc-num | Address                                    | Proxy                                      |
|-----------|---------|--------------------------------------------|--------------------------------------------|
| I         | 0       | lom14fzg2ex8xsl5ap7hq8skvt5ejpv35wvqx8dar7 | lom1lx0qcjy75xlsehxxpp6fhlps3nhpjtv7tnstfy |
| Faucet    | 1       | lom169dpm3dxss23ksm8q25zsyg07s0k55qafldgat | -                                          |
| Ap        | 2       | lom1d26fr26d3v924k30tl4pdl7fyxknwazq7a8yhm | lom18sggat4zrccrs99qsh802whvwe2k9euanykwln |
| L         | 3       | lom1rw9n93rt97upajx8ks82wl5f76a3map73lrl8x | lom18uy0lpcjnlf6gvsffyhxjyzcwuxy0v9vht3552 |
| C         | 4       | lom1klgwj8up9srlecah95pp0p0q2ar0gegc2rv8q3 | lom144wfrurnazcz3jk564a37m963tm5vjuj5kts8g |
| Am        | 5       | lom1r7kttcyhe8vymy4devyh7f2h3pmklj9e8d0arj | lom1xklayjln2cfj0xjex08stqp9rzyslvhzaenh0h |

```bash

# Initialize
ledgerd init lombard --chain-id ledger-mainnet-1 --default-denom ulom --home .
ledgerd config set client chain-id ledger-mainnet-1 --home .
ledgerd config set client keyring-backend test --home .

# Distribute initial balance of validators and faucet
ledgerd genesis add-genesis-account lom14fzg2ex8xsl5ap7hq8skvt5ejpv35wvqx8dar7 "2000000000ulom,1000000ustake" --home .
ledgerd genesis add-genesis-account lom169dpm3dxss23ksm8q25zsyg07s0k55qafldgat "17446744073709551615ulom,100000000ustake" --home .
ledgerd genesis add-genesis-account lom1d26fr26d3v924k30tl4pdl7fyxknwazq7a8yhm "2000000000ulom,1000000ustake" --home .
ledgerd genesis add-genesis-account lom1rw9n93rt97upajx8ks82wl5f76a3map73lrl8x "2000000000ulom,1000000ustake" --home .
ledgerd genesis add-genesis-account lom1klgwj8up9srlecah95pp0p0q2ar0gegc2rv8q3 "2000000000ulom,1000000ustake" --home .
ledgerd genesis add-genesis-account lom1r7kttcyhe8vymy4devyh7f2h3pmklj9e8d0arj "2000000000ulom,1ustake" --home .

# Distribute initial balance of proxies
ledgerd genesis add-genesis-account lom1lx0qcjy75xlsehxxpp6fhlps3nhpjtv7tnstfy "40000000000ulom" --home .
ledgerd genesis add-genesis-account lom18sggat4zrccrs99qsh802whvwe2k9euanykwln "40000000000ulom" --home .
ledgerd genesis add-genesis-account lom18uy0lpcjnlf6gvsffyhxjyzcwuxy0v9vht3552 "40000000000ulom" --home .
ledgerd genesis add-genesis-account lom1jhd8vszq6gut9uxwf4a462pv08x6t6jermrnrj "40000000000ulom" --home .
ledgerd genesis add-genesis-account lom1xklayjln2cfj0xjex08stqp9rzyslvhzaenh0h "40000000000ulom" --home .
```

Collect gentx
```bash
ledgerd genesis collect-gentxs --home .
```

Modify genesis

* `app_state.distribution.params.community_tax = "0.000000000000000000"`
* `app_state.gov.min_deposit.denom = "ulom"`
* `app_state.gov.min_deposit.amount = "200000000"`
* `app_stage.gov.max_deposit_period = "600s"` 1h
* `app_stage.gov.voting_period = "172800s"` 2d
* `app_stage.gov.expedited_voting_period = "86400s"` 1d
* `app_stage.gov.expedited_min_deposit.denom = "ulom"`
* `app_stage.gov.expedited_min_deposit.amount = "2000000000"`
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
* `app_stage.slashing.params.downtime_jail_duration = "60m0s"` 1h
* `app_stage.slashing.params.slash_fraction_downtime = "0.000100000000000000"`
* `app_stage.staking.params.unbonding_time = "1209600s"` 2w
* `app_stage.staking.params.max_validators = 4`
* `consensus.params.block.max_bytes = "2097152"`
* `consensus.params.block.max_gas = "20000000"`

Validate genesis:
```bash
ledgerd genesis validate --home .
```
