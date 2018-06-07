# Travis CI project with GHDL
[![Build Status](https://travis-ci.org/emanuelen5/GHDL-Travis-Hello-World.svg?branch=travis-ci-integration)](https://travis-ci.org/emanuelen5/GHDL-Travis-Hello-World)

Following this [tutorial](https://theintobooks.wordpress.com/2018/01/23/building-ghdl-from-source-for-ubuntu-16-04-mcode-version/) for setting up GHDL with mcode on Travis (homefully the simplest way to get working with Travis).

* ADA compiler [download links](https://www.adacore.com/download/more) for [32b-linux](http://mirrors.cdn.adacore.com/art/564b3e9dc8e196b040fbe248) and [64b-linux](http://mirrors.cdn.adacore.com/art/591c6d80c7a447af2deed1d7).

## Steps I have taken
```bash
cd ~/Downloads
wget http://mirrors.cdn.adacore.com/art/591c6d80c7a447af2deed1d7 # filename: 'gnat-gpl-2017-x86_64-linux-bin.tar.gz'
tar -vxzf gnat-gpl-2017-x86_64-linux-bin.tar.gz
cd gnat-gpl-2017-x86_64-linux-bin

sudo ./doinstall
# Install of ADA is now complete!

export PATH="/usr/gnat/bin:$PATH"

# Clone GHDL and build
git clone https://github.com/ghdl/ghdl.git

sudo apt-get install zlib1g-dev

cd ghdl
./configure --prefix=/usr/local/ghdl_mcode
make

# '/usr/gnat/bin' needs to be on the path when installing
sudo PATH=$PATH make install

export "PATH=/usr/local/ghdl_mcode/bin/:$PATH"
# --- GHDL is now installed and on the path! ---

pip install vunit_hdl
python vunit_main.py
```
