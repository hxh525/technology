[https://dev.mysql.com/](https://dev.mysql.com/)

### ubuntu online install mysql

#### ubuntu 卸载 mysql

```
#首先删除mysql相关服务
sudo apt-get -y remove mysql*
sudo apt-get -y autoremove

#删除mysql 相关目录
sudo rm -R /var/lib/mysql/
sudo rm -R /etc/mysql/

#查看，还剩什么就卸载什么
#dpkg -l | grep mysql
dpkg -l | grep mysql | grep ii
#清理残留的数据 (rc 状态的包即卸载了包却保留了配置文件)
#dpkg -l | grep ^rc | awk '{print $2}' | sudo xargs dpkg -P
```

#### ubuntu 安装 mysql

```
#使用apt-key实用程序直接将GPG密钥下载到APT密钥环
sudo apt-key adv --keyserver pgp.mit.edu --recv-keys 5072E1F5

#添加源到sources.list.d
sudo mkdir -p /etc/apt/sources.list.d
sudo touch /etc/apt/sources.list.d/mysql.list
sudo echo 'deb http://repo.mysql.com/apt/ubuntu/ trusty mysql-5.7' | sudo tee /etc/apt/sources.list.d/mysql.list > /dev/null

#更新列表
sudo apt-get update
sudo apt-get -y install libmysqlclient20

#自动交互时候的命令debconf-set-selections 修改mypassword
sudo debconf-set-selections <<< "mysql-server mysql-server\/root-pass password mypassword"
sudo debconf-set-selections <<< "mysql-server mysql-server/re-root-pass password mypassword"

#"-y"当安装包的时候会询问y/n,这个参数是所有询问默认y
#DEBIAN_FRONTEND 变量说明是非交互性
#sudo DEBIAN_FRONTEND=noninteractive apt-get -y install mysql-server
sudo apt-get -y install mysql-server

#修改端口开发,最大连接数参数
sudo sed -ie 's/127.0.0.1/0.0.0.0/' /etc/mysql/mysql.conf.d/mysqld.cnf
echo 'max_connections=30000' | sudo tee -a  /etc/mysql/mysql.conf.d/mysqld.cnf

#修改mysql root 密码
mysqladmin -uroot -pmypassword password 12345678

#修改mysql root 外部访问
mysql -h localhost -uroot -p12345678 << EOF
use mysql;
update user set host = '%' where user = 'root';
flush privileges; 
select user, host from user;
EOF

#启动 mysql
sudo service mysql stop
sudo service mysql start
sudo service mysql status
```

#### ubuntu 安装 mysql

```
sudo wget http://dev.mysql.com/get/mysql-apt-config_0.8.0-1_all.deb
sudo dpkg -i mysql-apt-config_0.8.1-1_all.deb

sudo apt-get update

#自动交互时候的命令debconf-set-selections 修改mypassword
sudo debconf-set-selections <<< "mysql-server mysql-server/root-pass password mypassword"
sudo debconf-set-selections <<< "mysql-server mysql-server/re-root-pass password mypassword"
sudo apt-get -y install mysql-server
```

#### mysql 操作命令

```
sudo service mysql status
sudo service mysql start
sudo service mysql stop
```

#### 修改参数

```
echo 'max_connections=30000' | sudo tee -a  /etc/mysql/mysql.conf.d/mysqld.cnf
echo 'bind-address = 0.0.0.0' | sudo tee -a  /etc/mysql/mysql.conf.d/mysqld.cnf
```

### Mysql 安装包制作

```
#必须安装依赖/usr/etc/my.cnf
sudo apt-get install libaio-dev  

#下载mysql
wget https://dev.mysql.com/get/Downloads/MySQL-5.7/mysql-5.7.23-linux-glibc2.12-x86_64.tar.gz

#解压mysql
sudo tar zxvf mysql-5.7.23-linux-glibc2.12-x86_64.tar.gz
mv mysql-5.7.23-linux-glibc2.12-x86_64 mysql-5-7-23

#初始化db
sudo ./mysql-5-7-23/bin/mysqld --initialize --basedir=mysql-5-7-23 --datadir=./mysql-5-7-23/data

#修改data所有者权限
sudo chown -R ubuntu:ubuntu ./mysql-5-7-23/data

#根据用户启动mysql
sudo ./mysql-5-7-23/bin/mysqld_safe --user=ubuntu &

#登录mysql
sudo ./mysql-5-7-23/bin/mysql -uroot -p # 初始化db时日志打印临时root密码

#登录mysql后 修改密码 设置root远程可登陆
mysql>  alter user user() identified by "123456";
mysql>  use mysql;
mysql>  update user set host='%' where user='root' and host='localhost'; 

tar zxvf mysql-5-7-23.tar.gz mysql-5-7-23
```

#### mysql 安装包

```
#scp -r  ubuntu@52.81.1.169:/home/ubuntu/mysql/mysql-5-7-23.tar.gz ./ #拷贝mysql 解压版
sudo tar zxvf mysql-5-7-23.tar.gz
sudo chmod -R 774 ./mysql-5-7-23
sudo ./mysql-5-7-23/bin/mysql -uroot -p
sudo ./mysql-5-7-23/bin/mysqld_safe --user=ubuntu & #当前路径为mysql根路径
```

#### mysql 信息

    版本: 5.7.23
    源版本下载地址: 
    wget https://dev.mysql.com/get/Downloads/MySQL-5.7/mysql-5.7.23-linux-glibc2.12-x86_64.tar.gz

    绿色解压安装包: 

    启动方式: sudo ./bin/mysqld_safe --user=ubuntu & #当前路径为mysql根路径
    停止方式: sudo kill -9 `ps aux | grep mysql-5-7-23 | grep -v 'color=auto' | awk '{print $2}'`

    配置文件: /etc/my.cnf #默认无此配置文件,如需修改端口和其他配置信息,需要生成此配置文件
    默认端口: 3306
    初始化用户: root
    Root用户密码: 123456

#### /etc/my.cnf 

```
[client]
port=3306
socket=/tmp/mysql.sock
[mysqld]
init-connect='SET NAMES utf8'
basedir=/home/ubuntu/mysql/mysql
datadir=/home/ubuntu/mysql/mysql/data
socket=/tmp/mysql.sock
max_connections=20000
character-set-server=utf8
default-storage-engine=INNODB
```

#### Mysql 配置文件清理

```
sudo rm -rf mysql/mysql/data/*

sudo rm -rf /tmp/mysql*
sudo rm -rf /usr/local/mysql*
sudo rm -rf /var/lib/mysql
sudo rm -rf /etc/my.cnf*
sudo rm -rf /etc/mysql/my.cnf*
sudo rm -rf /usr/etc/my.cnf*
```













