# Subinode-Setup-Guide
**Windows:**

=> Go to Debug Console then type

```subinode genkey```

=> Then type

```getnewaddress Your_MN_Label legacy```

For example:

```getnewaddress SN1 legacy```

=> Now send exactly 10000 SUBI to the address and then type

```subinode outputs```

You will get txid and output index.

=> Now go to C:\Users\\%username%\Appdata\Roaming\Subi and open subinode.conf

In the file, add a line that matches the following syntax.

```LABEL IP:5335 SUBINODEKEY TXID INDEX```

For example:

```SN1 xx.xx.xx.xx:5335 xxx xxxxxx 0```

=> Now save and restart your wallet.


**VPS**

Minimum Requirements:

1. 512MB RAM

2. Ubuntu 18.04 x64

You'll get VPS with above configuration for only 3.5$ in <a href="https://www.vultr.com/?ref=7318863">vultr.com</a>

=> Now after buying VPS, open putty and login. Then install the following dependencies:

```sudo apt-get update```

```sudo apt-get install libboost-all-dev libzmq3-dev build-essential libtool autotools-dev automake pkg-config python3 libboost-system-dev libboost-filesystem-dev libboost-chrono-dev libboost-test-dev libboost-thread-dev software-properties-common libminiupnpc-dev libqt5gui5 libqt5core5a libqt5dbus5 qttools5-dev qttools5-dev-tools libprotobuf-dev protobuf-compiler libqrencode-dev```

```sudo apt-get install libssl-dev libevent-dev bsdmainutils libboost-all-dev```

```sudo add-apt-repository ppa:bitcoin/bitcoin```

```sudo apt-get install libdb4.8-dev libdb4.8++-dev```

```sudo apt-get install unzip```

=> Now download the Linux binaries:

```wget https://github.com/alamin0x1/Subinode-Setup-Guide/releases/download/1.0.0.2/bin.zip```

[I've uploaded that binaries to my github repository to make it easier]

=> Now extract the zip:

```unzip bin.zip```

=> Now you need to add permissions:

```chmod u+x subi-cli```

```chmod u+x subid```

```chmod u+x subi-tx```

=> Now start your daemon:

```./subid```

The daemon will require config file.

=> After that you'll need to restart your VPS:

```sudo reboot```

=> Then after few minutes again login to your VPS using putty or similar software.

=> Then go to config folder:

```cd ~/.subi```

=> Now open config file:

```vi subi.conf```

=> Next, enter the following configuration. Be sure to update the following fields below:

```
rpcuser=username
rpcpassword=password
rpcallowip=127.0.0.1
port=5335
rpcport=5336
listen=1
server=1
daemon=1
logtimestamps=1
maxconnections=64
txindex=1
subinode=1
externalip=subinode-ip-address:5335
subinodeprivkey=subinode-key
```

=> Now press Esc and type

```:wq!```

and press enter. It will save the file and exit.

=> Now go to root directory:

```cd```

=> Start the daemon and let it sync:

```./subid```

=> You can check the info using:

```./subi-cli getinfo```

=> Now when it is fully synced, go to your Windows wallet and start the Masternode from Subinodes tab.

If you are not sure about this, after opening Subines tab, right click on Masternode name and then click on "Start alias". Your nodes should show PRE_ENABLED in status and after a few minutes change to ENABLED.

=> Now in VPS type:

```./subi-cli subinode start```

If everything is okay, you will see "Successfully started subinode".

=> Then to see Masternode status type:

```./subi-cli subinode status```

Hurray! You've setup your Subinode!
