<div align="center">
  <h1>TUTORIAL CREDIT COIN SIPALING TESTNET</h1>
</div>

<div align="center">
  <img src="https://bitcoinvn.com/attachments/8c8e7200-588d-11ea-9d3c-107e95d9307a-png.2668/" alt="CREDIT COIN Background" />
</div>


## 1. Upade Vps
```bash
sudo apt update; sudo apt upgrade 
```
## 2. Install Docker Dll
```bash
sudo apt-get update && sudo apt install jq git && sudo apt install apt-transport-https ca-certificates curl software-properties-common -y && curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add - && sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable" && sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin && sudo apt-get install docker-compose-plugin 

```

## 3. Download Image 
```bash
docker pull gluwa/creditcoin:2.222.2-testnet 
```

## 4. Jalankan Node  
```bash
docker run -d \
 --name creditcoin-validator \
 -p 30333:30333 \
 -v  creditcoin/creditcoin-node/data  \
 gluwa/creditcoin:2.222.2-testnet \
 --name "NAMA VALIDATOR KAMU" \
 --telemetry-url "wss://telemetry.creditcoin.network/submit/ 0" \
 --public-addr "/dns4/IPKAMU/tcp/30333" \
--chain test \
 --bootnodes "/dns4/testnet-bootnode.creditcoin.network/tcp/30333/p2p/12D3KooWG3eEuYxo37LvU1g6SSESu4i9TQ8FrZmJcjvdys7eA3cH" "/dns4/testnet-bootnode2.creditcoin.network/tcp/30333/p2p/12D3KooWLq7wCMQS3qVMCNJ2Zm6rYuYh74cM99i9Tm8PMdqJPDzb" "/dns4/testnet-bootnode3.creditcoin.network/tcp/30333/p2p/12D3KooWAKUrvmchoLomoouoN1sKfF9kq8dYtCVFvtPuvqp7wFBS" \
--validator \
--base-path /creditcoin-node/data \
--port 30333
```


## 5. Cek Log
Setelah cek log teman teman bisa close vpsnya lalu buka kembali vps nya maksud saya buka session baru lalu masukan command di langkah 6 
```bash
docker logs -f creditcoin-validator
```

## 6. Membuat Wallet
Setelah membuka session baru teman teman buat 2 wallet dengan cara copy command dibawah lalu paste di vps teman teman
jika sudah simpan kedua pharse tersebut lalu masukan pharse teman teman ke wallet polkadotjs
```bash
docker exec -it creditcoin-validator creditcoin-cli new
```

## 7. Mengirim Faucet 
Teman teman masuk kedalam link berikut untuk mengirim faucet dari wallet utama ke wallet yang sudah di generate
Teman teman bisa kirim 5k ke akun 1 dan 1kk ke akun 2 sisanya nanti teman teman bisa pakai buat nuyul lagi 
https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Frpc.testnet.creditcoin.network%2Fws#/accounts
```bash
docker exec -it creditcoin-validator creditcoin-cli new
```

## 8. Menjalankan Validator 
```bash
docker exec -it creditcoin-validator creditcoin-cli wizard -a 5000
```
  Nanti teman teman akan disuruh masukan Pharse jadi teman teman masukan pharse dengan keterangan berikut 
- Stash       : Wallet 1
- Controller  : Wallet 2
#### Jika muncul Seperti ini  berarti teman teman sudah benar 
```bash
💰 Stash account: 5HnEe2fg9vsGBCEsbMQFPxFvE324akZb3qjNqe96unAj7h7X
🎮 Controller account: 5HnEe2fg9vsGBCEsbMQFPxFvE324akZb3qjNqe96unAj7h7X
🪙 Amount to bond: 100.000000000000000000 CTC
🎁 Reward destination: Staked
📡 Node URL: ws://localhost:9944
💸 Commission: 0
🔐 Blocked: No
```

## 9. Mengecek Node 
Teman teman bisa mengecek node melalui https://telemetry.creditcoin.network/
Dengan cara mencari nama validator yang sudah kita buat jika ada berarti aman yah

## 10. Mengecek Validator
Untuk mengecek validator sudah aktif atau belum teman teman bisa masuk melalui link berikut 
https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Frpc.testnet.creditcoin.network%2Fws#/staking
