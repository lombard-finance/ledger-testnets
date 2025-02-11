# Ledger networks

## Cosmovisor

Add chain upgrades
```bash
wget "https://raw.githubusercontent.com/lombard-finance/ledger-testnets/master/$NETWORK/cosmovisor/upgrades.csv" -O upgrades.csv
cosmovisor add-batch-upgrade --upgrade-file upgrades.csv
```