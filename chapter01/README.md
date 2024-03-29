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

## 2、下载Python安装包
``` shell
 wget https://www.python.org/ftp/python/3.8.16/Python-3.8.16.tar.xz
 ```

## 3、解压
``` shell
tar -xvJf  Python-3.8.16.tar.xz
```

## 4、创建编译安装目录
``` shell
sudo mkdir -p /usr/local/python3
```

## 5、编译安装
``` shell
cd Python-3.8.16
./configure --prefix=/usr/local/python3 --enable-optimizations --with-ssl
#指定安装的路径,不指定的话,安装过程中可能软件所需要的文件复制到其他不同目录,删除软件很不方便,复制软件也不方便.
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
