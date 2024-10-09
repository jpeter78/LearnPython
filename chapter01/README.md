# Linux 安装Python3.8

## 1、安装依赖环境

### Ubuntu
``` shell
sudo apt-get install -y zlib1g-dev libbz2-dev libssl-dev libncurses5-dev libsqlite3-dev libreadline-dev tk-dev libgdbm-dev libdb-dev libpcap-dev xz-utils libexpat1-dev liblzma-dev libffi-dev libc6-dev
```

### centos
``` shell
yum -y groupinstall "Development tools"
yum -y install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel gdbm-devel db4-devel libpcap-devel xz-devel
yum install libffi-devel -y
```
centos的openssl的版本可能低了，需要额外安装openssl
下载openssl
```
cd /usr/src 
wget https://github.com/openssl/openssl/releases/download/OpenSSL_1_1_1q/openssl-1.1.1q.tar.gz
```
解压并安装
```
tar -xzvf openssl-1.1.1q.tar.gz
cd openssl-1.1.1q
# 编译
./config --prefix=/usr --openssldir=/etc/ssl --libdir=lib no-shared zlib-dynamic
# 安装
make && make install
```
校验
```
openssl version
```

## 2、下载Python安装包
``` shell
 wget https://www.python.org/ftp/python/3.11.9/Python-3.11.9.tar.xz
 ```

## 3、解压
``` shell
tar -xvJf  Python-3.11.9.tar.xz
```

## 4、创建编译安装目录
``` shell
sudo mkdir -p /usr/local/python3
```

## 5、编译安装
``` shell
cd Python-3.11.9
./configure --prefix=/usr/local/python3 --enable-optimizations
#指定安装的路径,不指定的话,安装过程中可能软件所需要的文件复制到其他不同目录,删除软件很不方便,复制软件也不方便.
# 默认是自带ssl进行编译的，如果是centos，手动安装openssl的话，需要加上参数指定openssl的安装目录
./configure --prefix=/usr/local/python3 --enable-optimizations --with-openssl=/usr
make && make install
```

## 6、创建软连接
``` shell
mv /usr/bin/python /usr/bin/python.bak 
#把原来的python移除
ln -s /usr/local/python3/bin/python3 /usr/local/bin/python
ln -s /usr/local/python3/bin/pip3 /usr/local/bin/pip
#把python3和pip3创建python和pip的软连接
```

## 7、验证
``` shell
python -V
pip -V
```
