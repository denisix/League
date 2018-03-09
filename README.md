# Fixed compilation issues
* error with leveldb caused by incorrect makefile.unix. Now you can successfully compile it.

# League Coin
All new coin. All new opportunities. 
* https://github.com/LGACoin/League
* https://league.express/

# How-to setup:
```
# You have to buy Ubuntu 14.04 VPS to setup MN

# Install requirements:
sudo apt-get install -y build-essential libtool autotools-dev pkg-config libssl-dev libboost-all-dev autoconf automake git libqt4-dev libminiupnpc-dev libgmp-dev openssl software-properties-common
git clone https://github.com/bitcoin-core/secp256k1
cd secp256k1
./autogen.sh
./configure
make
sudo make install

sudo add-apt-repository ppa:bitcoin/bitcoin
sudo apt-get update
sudo apt-get install -y libdb4.8-dev libdb4.8++-dev
        
# in case you have not a lot of RAM on your VPS do this:
sudo dd if=/dev/zero of=/var/swap.img bs=1024k count=1000
sudo mkswap /var/swap.img
sudo swapon /var/swap.img
sudo chmod 0600 /var/swap.img
sudo chown root:root /var/swap.img

# Install League wallet
git clone https://github.com/denisix/League
cd League/src
make -f makefile.unix
./Leagued

(then type Ctrl+C to stop it gracefully or: ./Leagued stop )

# make config
nano ~/.League/League.conf

# and paste the following (rpcuser & rpcpassword you can generate others):
rpcuser=yourusername
rpcpassword=yourpassword
rpcallowip=127.0.0.1
daemon=1
server=1
listen=1
#masternodeaddr=x.x.x.x:19371
#masternode=1
#masternodeprivkey=privatekey

# then start the wallet again and get new account address:
./Leagued
(wait a little bit)
./Leagued getaccountaddress "mn1"

(send exactly 3000 coins, you can buy them at presale stage at their website - https://league.express/ )

(then you will see them at your account "mn1")
./Leagued listaccounts

./Leagued masternode genkey

(replace "privatekey" with the value)
nano ~/.League/League.conf

masternodeaddr=x.x.x.x:19371
masternode=1
masternodeprivkey=privatekey
```
