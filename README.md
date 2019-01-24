# BlacerCoin
Shell script to install a [BlacerCoin Masternode](http://blacercoin.com/) on a Linux server running Ubuntu 14.04, 16.04 or 18.04. Use it on your own risk.

***
## Installation wallet (latest version):
```
git clone https://github.com/blcrproject/blcr-install/
cd blcr-install
bash blcr-install.sh
```
***
## Update wallet to latest version:
```
cd ~/blcr-install/
git pull
bash blcr-update.sh
```
***

## Desktop wallet setup

After the MN is up and running, you need to configure the desktop wallet accordingly. Here are the steps for Windows Wallet
1. Open the BlacerCoin Coin Desktop Wallet.
2. Go to RECEIVE and create a New Address: **MN1**
3. Send **1000** **BlacerCoin** to **MN1**.
4. Wait for 15 confirmations.
5. Go to **Tools -> "Debug console - Console"**
6. Type the following command: **masternode outputs**
7. Go to  ** Tools -> "Open Masternode Configuration File"
8. Add the following entry:
```
Alias Address Privkey TxHash Output_index
```
* Alias: **MN1**
* Address: **VPS_IP:PORT**
* Privkey: **Masternode Private Key**
* TxHash: **First value from Step 6**
* Output index:  **Second value from Step 6**
9. Save and close the file.
10. Go to **Masternode Tab**. If you tab is not shown, please enable it from: **Settings - Options - Wallet - Show Masternodes Tab**
11. Click **Update status** to see your node. If it is not shown, close the wallet and start it again. Make sure the wallet is unlocked.
12. Open **Debug Console** in local wallet and type:
```
startmasternode "alias" "0" "MN1"
```
13. Open the **Linux VPS console** and type:
```
blacercoin-cli startmasternode local false
```
If successful, you will be answered:
Masternode successfully started
***

## Usage:
```
blacercoin-cli getinfo
blacercoin-cli mnsync status
blacercoin-cli masternode status
```
Also, if you want to check/start/stop **BlacerCoin** , run one of the following commands as **root**:

**Ubuntu 16.04 or 18.04**:
```
systemctl status BlacerCoin #To check the service is running.
systemctl start BlacerCoin #To start BlacerCoin service.
systemctl stop BlacerCoin #To stop BlacerCoin service.
systemctl is-enabled BlacerCoin #To check whetether BlacerCoin service is enabled on boot or not.
```
**Ubuntu 14.04**:  
```
/etc/init.d/BlacerCoin start #To start BlacerCoin service
/etc/init.d/BlacerCoin stop #To stop BlacerCoin service
/etc/init.d/BlacerCoin restart #To restart BlacerCoin service
```
***
