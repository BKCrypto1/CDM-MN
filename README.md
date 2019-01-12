# Condominium Masternode Setup
Shell script to install a [CDM Masternode](https://www.cdmcoin.org//) on a Linux server running Ubuntu 16.04. 

*Use it on your own risk.

***
## CDM Masternode Requirement

| Masternode            | Amount Required |
| --- | --- |
| | 250,000 CDM |


***
## VPS
Sign up for either (referral link) [Digital Ocean](https://m.do.co/c/93c45618280e) or [Vultr](https://vultr.com) and set up a bare bones VPS. The $5/month option is sufficient for our needs. If you use the DO link above, you will get $100, 60-day credit.
- 1GB / 1CPU
- 25GB SSD
- 1TB Transfer

The install script will take care of the swap file for you.
***
## Installation:
1. Login as root
2. Run the following commands

```
wget -N https://github.com/BKCrypto1/CDM-MN/blob/master/cdminstall.sh
chmod +x cdminstall.sh
./cdminstall.sh
```
Upon completion, you will be provided with a bunch of masternode information. Save this information for the next step.
***

## Desktop wallet setup

After the MN is up and running, you need to configure the desktop wallet accordingly.
1. Open the Condominium (CDM) Desktop Wallet.
2. Go to RECEIVE and create a New Address: MN1
3. Send the required CDM to MN1. (250K)
4. Wait for at least 15 confirmations.
5. Go to Tools -> "Debug console"
6. Type the following command: 
```
masternode outputs
```
7. Go to Tools -> "Open Masternode Configuration File"
8. Add the following entry:
```
Alias IP:port MN_PrivateKey MN_Output_txid MN_Output_index
```

* Alias: MN1
* IP:port: VPS_IP:PORT
* MN_PrivateKey: Masternode Private Key
* MN_Output_txid: First value from Step 6
* MN_Output_index:  Second value from Step 6
9. Save and close the file.
10. Go to Tools -> "Open Wallet Configuration File"
11. Add the following entry:
```
externalip=IP:port
```
12. Save and close the file.
13. Close and Restart Wallet.
13. Go to Masternode Tab. If this tab is not shown, please enable it from: Settings - Options - Wallet - Show Masternodes Tab
14. Click Update status to see your node. If it is not shown, close the wallet and start it again. Make sure the wallet is unlocked.
15. Open Debug Console and type: (you can also click the start missing button)
```
masternode start-missing
```

***

## VPS Usage:
```
condominium-cli getinfo
condominium-cli mnsync status
condominium-cli masternode status
```
Also, if you want to check/start/stop Condominium Node , run one of the following commands as **root**:

**Ubuntu 16.04**:
```
systemctl status condominium #To check the service is running.
systemctl start condominium #To start Condominium service.
systemctl stop condominium #To stop Condominium service.
systemctl is-enabled condominium #To check whetether Condominium service is enabled on boot or not.
```

If you need any assistance, feel free to stop by the [Condominium Discord](https://discord.gg/MKgDRah) or [Condominium Telegram](http://t.me/cdmcoin). 
I go by the name of BK in both Channels.
