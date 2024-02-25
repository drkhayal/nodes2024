## Sync node

### From snapshot (fast)

1. Binary yüklə
```bash
wget https://github.com/crossfichain/crossfi-node/releases/download/v0.3.0-prebuild3/crossfi-node_0.3.0-prebuild3_linux_amd64.tar.gz && tar -xf crossfi-node_0.3.0-prebuild3_linux_amd64.tar.gz
```

2. Configs yüklə
```bash
git clone https://github.com/crossfichain/testnet.git
```

3. Node başlat
```bash
./bin/crossfid start --home ./testnet
```
4. Test token aldığınız cüzdanı import edirik. My_validator - öz validator adımız
```bash
./bin/crossfid --home ./testnet keys add my_validator --recover
```
5.Validator qururuq. Moniker Və validatorname özümüzə uyğun dəyişirik. 
```bash
./bin/crossfid --home ./testnet tx staking create-validator \
  --amount=9900000000000000000mpx \
  --pubkey=$(./bin/crossfid --home ./testnet tendermint show-validator) \
  --moniker="moniker" \
  --chain-id="crossfi-evm-testnet-1" \
  --commission-rate="0.10" \
  --commission-max-rate="0.20" \
  --commission-max-change-rate="0.01" \
  --min-self-delegation="1000000" \
  --gas="auto" \
  --gas-prices="10000000000000mpx" \
  --gas-adjustment=1.5 \
  --from=validatorname
```

6. Tokenləri özümüzə delegate edirik. Valoperadresinizi və Validatorname özümüzə uyğun dəyişirik. 
```bash
./bin/crossfid --home ./testnet tx staking delegate valoperadresiniz 9900000000000000000000mpx --from validatorname --chain-id crossfi-evm-testnet-1 --gas-adjustment 1.5 --gas auto --gas-prices 10000000000000mpx -y
```

7. Burda öz adınızı və ya adresinizi axtarın. Siyahıda varsınızsa nodunuz alınıb. https://test.xfiscan.com/
