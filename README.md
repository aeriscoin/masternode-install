# AERISCOIN
Shell script to install a [Aeriscoin Masternode](https://aeriscoin.com) on a Linux server running Ubuntu 14.04 or 16.04. Use it on your own risk.  
This script will instal version 0.15.1
***

## VPS installation:
```
wget -N https://raw.githubusercontent.com/aeriscoin/masternode-install/master/aeriscoin_install.sh
bash aeriscoin_install.sh
```
***

## Desktop wallet setup

After the MN is up and running, you need to configure the desktop wallet accordingly. Here are the steps for Windows Wallet
1. Open the Aeriscoin Coin Desktop Wallet.
2. Go to RECEIVE and create a New Address: **MN1**
3. Send **5000** **ARS** to **MN1**.
4. Wait for 20 confirmations.
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
12. Open **Debug Console** and type:
```
startmasternode "alias" "0" "MN1"
```
***

## Usage:
```
aeriscoin-cli mnsync status
aeriscoin-cli getinfo
aeriscoin-cli masternode status
```
Also, if you want to check/start/stop **Aeriscoin** , run one of the following commands as **root**:

```
systemctl status Aeriscoin #To check the service is running.
systemctl start Aeriscoin #To start Aeriscoin service.
systemctl stop Aeriscoin #To stop Aeriscoin service.
systemctl is-enabled Aeriscoin #To check whetether Aeriscoin service is enabled on boot or not.
```
***
## Old Aeriscoin delete:
In order to delete your Aeriscoin Masternode,  please run the following commands:
```
systemctl stop Aeriscoin
systemctl disable Aeriscoin
rm -r /root/.aeriscoin*
rm -r /usr/local/bin/aeriscoin*
rm -r /etc/systemd/system/Aeriscoin.service
```
***
