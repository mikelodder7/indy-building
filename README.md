# Installing libindy

## Ubuntu
```bash
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 68DB5E88
sudo add-apt-repository "deb https://repo.sovrin.org/sdk/deb xenial stable”
sudo apt-get update
sudo apt-get install -y libindy
```

## Mac OS X
- Download [Libindy](https://s3.us-east-2.amazonaws.com/sovrin-build-artifacts/libindy/macosx/stable/1.6.8/libindy_1.6.8.zip)
- Unzip to the directory you want to save as the working library
- Add to your **PATH** environment variable the path to *macosx/lib*

## Windows
- Download [Libindy](https://repo.sovrin.org/windows/libindy/stable/1.6.8/libindy_1.6.8.zip)
- Unzip to the directory you want to save as working library
- Add to your **PATH** environment variable the path to *lib*


# Build from source

## Ubuntu
Install build tools
```bash
apt-get update
apt-get install -y pkg-config automake autoconf cmake libtool git libzmq5
```

**Build libsodium**


Only needed if libsodium build errors happen when compiling libindy
```bash
curl -sSLO https://github.com/jedisct1/libsodium/releases/download/1.0.14/libsodium-1.0.14.tar.gz
tar xf libsodium-1.0.14.tar.gz
cd libsodium-1.0.14
./autogen.sh
./configure --prefix=/usr/local
make && make install
```

**Build ZMQ**


Only needed if zmq build errors happen when compiling libindy
```bash
curl -sSLO https://github.com/zeromq/libzmq/releases/download/v4.2.5/zeromq-4.2.5.tar.gz
tar xf zeromq-4.2.5.tar.gz
cd zeromq-4.2.5
./autogen.sh
./configure --prefix=/usr/local --enable-static --with-libsodium=/usr/local
make && make install
```

**Install Rust**
```
curl https://sh.rustup.rs -sSf | sh -s -- -y
source ~/.cargo/env
```

**Build libindy**
```bash
git clone https://github.com/hyperledger/indy-sdk.git
cd indy-sdk/libindy
git checkout tags/v1.6.8
cargo build --release
```

**Install libindy**
```bash
sudp cp target/release/libindy.a /usr/local/lib/
sudp cp target/release/libindy.so /usr/local/lib/
```

## Mac OS X
Open a command line terminal
**Install Homebrew**
```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

**Install Build tools**
```bash
brew install git
brew install pkg-config
brew install automake
brew install autoconf
brew install cmake
brew install libtool
brew install zmq
brew install zeromq
```

**Build libsodium**


Only needed if libsodium build errors happen when compiling libindy
```bash
curl -sSLO https://github.com/jedisct1/libsodium/releases/download/1.0.14/libsodium-1.0.14.tar.gz
tar xf libsodium-1.0.14.tar.gz
cd libsodium-1.0.14
./autogen.sh
./configure --prefix=/usr/local
make && make install
```

**Build ZMQ if needed**


Only needed if zmq build errors happen when compiling libindy
```bash
curl -sSLO https://github.com/zeromq/libzmq/releases/download/v4.2.5/zeromq-4.2.5.tar.gz
tar xf zeromq-4.2.5.tar.gz
cd zeromq-4.2.5
./autogen.sh
./configure --prefix=/usr/local --enable-static --with-libsodium=/usr/local
make && make install
```

**Install Rust**
```bash
curl https://sh.rustup.rs -sSf | sh -s -- -y
source ~/.cargo/env
```

**Build libindy**
```bash
git clone https://github.com/hyperledger/indy-sdk.git
cd indy-sdk/libindy
git checkout tags/v1.6.8
cargo build —-release
```

**Install libindy**
```bash
sudo cp target/release/libindy.a /usr/local/lib/
sudo cp target/release/libindy.dylib /usr/local/lib/
```

## Windows
- Download and run [Git](https://git-scm.com/download/win)
- Download and run [Rust](https://static.rust-lang.org/rustup/dist/i686-pc-windows-gnu/rustup-init.exe)
- Download [Libindy](https://repo.sovrin.org/windows/libindy/stable/1.6.8/libindy_1.6.8.zip)
- Unzip to the directory you want to save as working library
- Add to your **PATH** environment variable the path to *lib*

**Build libindy**
```bash
git clone https://github.com/hyperledger/indy-sdk.git
cd indy-sdk/libindy
git checkout tags/v1.6.8
cargo build —-release
```

Add to your **PATH** environment variable the path to target/release/libindy.dll
