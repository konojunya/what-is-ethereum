# what-is-ethereum
Ethereumとは何かを勉強するリポジトリ

## プライベートネットの初期化

```
geth --datadir . init myGenesis.json
```

## プライベートネットの起動

```
geth --networkid 15 --datadir . console 2>> error.log
```

## Genesis ブロックの確認

```
> eth.getBlock(0)
```

## アカウントの作成

送金できるように2つ作っておく

```
> personal.newAccount("junpass")
> personal.newAccount("shotapass")
```

##　アカウントの確認

```
> eth.accounts
```

## コインベースアカウントの確認・変更

```
> eth.coinbase
> miner.setEtherbase(eth.accounts[1]) // 1の人に変更
```

## マイニング開始

```
> miner.start()
```

## マイニング状態かどうか確認

```
> eth.mining
```

## マイニング停止

```
> miner.stop()
```

## コインベースアカウントの残高確認

```
> eth.getBalance(eth.accounts[0])
```

## 単位をetherに合わせる

```
> web3.fromWei(eth.getBalance(eth.accounts[1]), "ether")
```

## 送金をするためにロックを解除

```
> personal.unlockAccount(eth.accounts[0])
```

## 送金

```
> eth.sendTransaction({from: eth.accounts[0], to: eth.accounts[1], value: web3.toWei(35, "ether")})
```

## ロックする

```
> personal.lockAccount(eth.accounts[0])
```

## トランザクションを確認

```
> eth.getTransaction("0x61e615848e324741b272935838b4363d5d824d02e26117478de84b87457dfdc0")
```

## トランザクションをブロックに取り込む

```
> miner.start()
```