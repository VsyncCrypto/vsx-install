# Vsync
Shell script to install a [Vsync Masternode](https://www.vsync.pw/) on a Linux server running Ubuntu 14.04, 16.04 or 18.04. Use it on your own risk.

***
## Installation wallet (latest version):
```
git clone https://github.com/VsyncCrypto/vsx-install/
cd vsx-install
bash vsx-install.sh
```
***

## Update wallet to latest version:
```
cd ~/vsx-install/
git pull
bash vsx-update.sh
```
OR
```
git clone https://github.com/VsyncCrypto/vsx-install/
cd vsx-install
bash vsx-update.sh
```
***

## Delete old blockchain files, to download new ones:
```
cd ~/vsx-install/
git pull
bash vsx-upblock.sh
```
***

## Desktop wallet setup

After the MN is up and running, you need to configure the desktop wallet accordingly. Here are the steps for Windows Wallet
1. Open the Vsync Coin Desktop Wallet.
2. Go to RECEIVE and create a New Address: **MN1**
3. Send **100 000** **Vsync** to **MN1**.
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
12. Open **Debug Console** and type:
```
startmasternode "alias" "0" "MN1"
```
***

## Usage:
```
vsync-cli getinfo
vsync-cli mnsync status
vsync-cli masternode status
```
Also, if you want to check/start/stop **Vsync** , run one of the following commands as **root**:

**Ubuntu 16.04 or 18.04**:
```
systemctl status Vsync #To check the service is running.
systemctl start Vsync #To start Vsync service.
systemctl stop Vsync #To stop Vsync service.
systemctl is-enabled Vsync #To check whetether Vsync service is enabled on boot or not.
```
**Ubuntu 14.04**:  
```
/etc/init.d/Vsync start #To start Vsync service
/etc/init.d/Vsync stop #To stop Vsync service
/etc/init.d/Vsync restart #To restart Vsync service
```
***
