<h1 align="center">Gitopia Testnet Installation Guide

## Gitopia Official Telegram: https://t.me/Gitopia

![image](https://user-images.githubusercontent.com/101462877/201489822-1d35a702-8d38-4a63-933b-6112b226817f.png)


## System requirements:
NODE TYPE | CPU     | RAM      | SSD     |
| ------------- | ------------- | ------------- | -------- |
| Testnet | 4          | 8         | 200*  |

## Important links for Gitopia:
- [Website](https://gitopia.com/)
- [Explorer](https://gitopia.explorers.guru/)
- [Twitter](https://twitter.com/gitopiaDAO)
- [Discord](https://discord.gg/EcwjHedFnp)

# 1.) Scripted installation with StateSync.

```
wget -O gitopiaIDN.sh https://raw.githubusercontent.com/0x000123/Gitopia-IBC/main/gitopiaIDN.sh && chmod +x gitopiaIDN.sh && ./gitopiaIDN.sh
```


  # Install Manual
  
Anda juga dapat melakukan ==> [Instalasi Manual](https://github.com/bent0000/Gitopia-IBC/blob/main/manual.md) 


# 2) Continue. 

## To check the sync status:

```
gitopiad status 2>&1 | jq .SyncInfo
``` 

![image](https://user-images.githubusercontent.com/101462877/201514358-41303e3f-6c51-4f12-b3e3-49bcecb3770c.png)

If the sync status is false as in the photo above, you can continue, if it is still true, wait and continue after false

## Create a wallet.
```
gitopiad keys add <WALLETNAME>
``` 
If you want to use an existing wallet:

```
gitopiad keys add <WALLETNAME> --recover
``` 


## To get testnet tokens, we import the words of the wallet we set up just above, to Keplr.

![image](https://user-images.githubusercontent.com/101462877/201490749-0d060bfa-bca3-4b09-8569-c00f499c8a48.png)

![image](https://user-images.githubusercontent.com/101462877/201490756-32b6b1f1-fdd8-4af1-b3f0-9f18f5a0ad3b.png)

![image](https://user-images.githubusercontent.com/101462877/201490769-99978610-5dba-4758-b4d1-abac5f18a215.png)

![image](https://user-images.githubusercontent.com/101462877/201490784-e00537d8-8c50-4951-9d76-fe78adca8032.png)

## After importing the wallet to Keplr, go to [Gitopia platform](https://gitopia.com/home) and get testnet tokens.

![image](https://user-images.githubusercontent.com/101462877/201490673-40e73d7d-0705-47c3-8ce6-391ad1326fdd.png)


![image](https://user-images.githubusercontent.com/101462877/201490821-bec0a6d7-9e97-4d22-b51d-092874799e52.png)


## Check that tokens have arrived in our wallet from [Explorer](https://gitopia.explorers.guru/)

![image](https://user-images.githubusercontent.com/101462877/201490841-58a9340a-8bb9-43c0-b086-dec720951575.png)


## Create validator.


```
gitopiad tx staking create-validator \
  --amount 1000000utlore \
  --from <WALLETNAME> \
  --commission-max-change-rate "0.01" \
  --commission-max-rate "0.2" \
  --commission-rate "0.07" \
  --min-self-delegation "1" \
  --pubkey  $(gitopiad tendermint show-validator) \
  --moniker $NODENAME \
  --chain-id gitopia-janus-testnet-2 \
  --website="http://twitter.com/Kyozer_er" \
  --details="Testing the Gitopia"
```


# Useful commands:

Checking logs

```
journalctl -fu gitopiad -o cat
```


Stopping the service

```
sudo systemctl stop gitopiad
```

Restarting the service

```
sudo systemctl restart gitopiad
```

Delegating tokens

```
gitopiad tx staking delegate gitopiavaloper1tdp45gtcfujsskg75k7tlxxxxxxx 10000000utlore --chain-id=gitopia-janus-testnet-2  --from <WALLETNAME>
```

Editing validator

```
gitopiad tx staking edit-validator \
  --moniker=$NODENAME \
  --identity="<YOUR KEYBASE ID>" \
  --website="<WEBSITE LINK>" \
  --details="DETAILS" \
  --chain-id=gitopia-janus-testnet-2  \
  --from=<WALLETNAME>
``` 


# Deleting node:

```
sudo systemctl stop gitopiad
sudo systemctl disable gitopiad
sudo rm /etc/systemd/system/gitopia* -rf
sudo rm $(which gitopiad) -rf
sudo rm $HOME/.gitopia* -rf
sudo rm $HOME/gitopia -rf
sed -i '/GITOPIA_/d' ~/.bash_profile
``` 



<p style="font-size:14px" align="right">
<a href="https://t.me/DCIDcom" target="_blank">Join Telegram Diskusi<img src="https://user-images.githubusercontent.com/50621007/183283867-56b4d69f-bc6e-4939-b00a-72aa019d1aea.png" width="30"/></a>
</p>
<p style="font-size:14px" align="lefth">
<a href="https://t.me/DCID_com" target="_blank">Join Telegram Airdrop<img src="https://user-images.githubusercontent.com/50621007/183283867-56b4d69f-bc6e-4939-b00a-72aa019d1aea.png" width="30"/></a>
</p>
