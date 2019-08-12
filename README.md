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

#  add SourceCodePro font 
#  set term param
sudo cp -rf ~/.setup/linux_set/SourceCodePro /usr/share/fonts/

# gtags
# 安装编译依赖的库
sudo apt build-dep global
sudo apt install libncurses5-dev libncursesw5-dev

# 从 GNU GLOBAL 官方下载最新的 tar.gz 包并解压到源码目录
wget https://ftp.gnu.org/pub/gnu/global/global-6.6.3.tar.gz

# untar
sudo tar -xvf global-6.6.3.tar.gz

# 在解压后的源码目录编译安装
./configure
make
sudo make install
# 只写 C/C++/Java 的话，那么到这里就够了，gtags 原生支持。如想要更多语言，那么 gtags 是支持使用 ctags/universal-ctags 或者 pygments 来作为分析前端支持 50+ 种语言。使用 ctags/universal-ctags 作为前端只能生成定义索引不能生成引用索引，因此我们要安装 pygments ，保证你的 $PATH 里面有 python，接着：
pip install pygments
