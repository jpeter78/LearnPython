Linux 安装Python3.7

1、安装依赖环境

sudo apt-get install zlib1g-dev libbz2-dev libssl-dev libncurses5-dev libsqlite3-dev libreadline-dev tk-dev libgdbm-dev libdb-dev libpcap-dev xz-utils libexpat1-dev liblzma-dev libffi-dev libc6-dev

2、下载Python安装包

 wget https://www.python.org/ftp/python/3.7.6/Python-3.7.6.tar.xz

3、解压

tar -xvJf  Python-3.7.6.tar.xz

4、创建编译安装目录

sudo mkdir -p /usr/local/python3

5、编译安装
cd Python-3.7.6
./configure --prefix=/usr/local/python3 --enable-optimizations --with-ssl
#第一个指定安装的路径,不指定的话,安装过程中可能软件所需要的文件复制到其他不同目录,删除软件很不方便,复制软件也不方便.
#第二个可以提高python10%-20%代码运行速度.
#第三个是为了安装pip需要用到ssl,后面报错会有提到.
make
sudo make install
