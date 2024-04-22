sudo apt update
bash <(wget -qO- https://github.com/fackNode/requirements/raw/main/go.sh)
export GOPATH=$HOME/go
export PATH=$PATH:/usr/local/go/bin:$GOPATH/bin
go version
#create wallet
mkdir $HOME/nimble && cd $HOME/nimble
git clone https://github.com/nimble-technology/wallet-public.git
cd wallet-public
make install
#master
nimble-networkd keys add master
#save seed
#sub
nimble-networkd keys add sub
#save seed
#install py
apt install software-properties-common -y 
add-apt-repository ppa:deadsnakes/ppa 
apt install python3.10 && apt install python3-venv
#check ver
python3 --version
#run miner
cd $HOME/nimble
git clone https://github.com/nimble-technology/nimble-miner-public.git
cd nimble-miner-public
make install
#add screen
screen -S nimble
source ./nimenv_localminers/bin/activate
make run addr=<wallet>
