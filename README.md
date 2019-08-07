#  /etc/hosts
#  change github hosts
127.0.0.1	localhost
127.0.1.1	ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

151.101.185.194 github.global.ssl.fastly.net
192.30.253.112 github.com

#  install vim8.1
sudo add-apt-repository ppa:jonathonf/vim
sudo apt update
sudo apt install vim

#  remove vim8.1
sudo apt remove vim
sudo add-apt-repository --remove ppa:jonathonf/vim

#  init vimrc and read READ.md
#  ~/.vim
cd ~/.vim
git clone https://github.com/robertian/vim-init.git

#  Ubuntu 16.04 and later
#  ~/.vim/bundles/
#  install youCompleteMe

#  if git submodule update, the network don't work, copy third_party
sudo apt install build-essential cmake python3-dev
git clone https://github.com/ycm-core/YouCompleteMe.git
cd ~/.vim/bundles/YouCompleteMe
git submodule update --init --recursive
#or
sudo cp -rf ~/.setup/linux_set/third_party ~/.vim/bundles/YouCompareMe
python3 install.py --clangd-completer


#  error: RPC failed; curl 18 transfer closed with outstanding read data remaining
#  fatal: The remote end hung up unexpectedly
#  fatal: early EOF
#  fatal: index-pack failed
git config --global http.postBuffer 724288000
