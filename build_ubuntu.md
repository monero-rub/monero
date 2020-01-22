## UBUNTU BUILD NOTES
Some notes on how to build RUB in Ubuntu.

### Dependencies
```
sudo apt install build-essential cmake pkg-config libssl-dev libzmq3-dev libunbound-dev libsodium-dev libunwind8-dev liblzma-dev libreadline6-dev libldns-dev libexpat1-dev doxygen graphviz libpgm-dev qttools5-dev-tools libhidapi-dev libusb-dev libprotobuf-dev protobuf-compiler
```

Install boost
```
wget https://dl.bintray.com/boostorg/release/1.65.1/source/boost_1_65_1.tar.bz2
tar -xjf boost_1_65_1.tar.bz2
cd boost_1_65_1/
./bootstrap.sh
sudo ./b2 install
```

### To Build
```
git clone https://github.com/monero-rub/monero.git
cd monero
git submodule update --init --force external/miniupnp
git submodule update --init --force external/unbound
git submodule update --init --force external/trezor-common
git submodule update --init --force external/rapidjson
mkdir build && cd build
cmake ..
make
```

### Usage

**monerorubd** The node server for linking other nodes to synchronize block data 

Produce help message
```
./monerorubd --help
```

e.g Run as daemon 
```
./monerorubd --add-exclusive-node=193.112.64.213:18080 --detach
```

**monerorub-wallet-cli** The command line wallet

Produce help message
```
./monerorub-wallet-cli --help
```

e.g Generate new wallet
```
./monerorub-wallet-cli --generate-new-wallet=your_wallet_name
```

