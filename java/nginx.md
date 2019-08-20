#### nginx 安装包制作

```
#下载nginx 解压包路径 '/usr/local/nginx-1.12.2/nginx-1.12.2.tar.gz'
wget http://nginx.org/download/nginx-1.12.2.tar.gz
sudo tar xvf nginx-1.12.2.tar.gz

#编译nginx 
cd nginx-1.12.2
sudo ./configure  --prefix=/usr/local/nginx-1.12.2  --sbin-path=/usr/local/nginx-1.12.2/sbin/nginx --conf-path=/usr/local/nginx-1.12.2/conf/nginx.conf --error-log-path=/usr/local/nginx-1.12.2/logs/error.log --pid-path=/usr/local/nginx-1.12.2/logs/nginx.pid

sudo make
sudo make install

#打包所有文件
cd ..
sudo rm -rf nginx-1.12.2.tar.gz
sudo tar zcvf nginx-1.12.2.tar.gz ./*


nginx 安装包

#sudo scp -r  ubuntu@52.81.1.169:/home/ubuntu/nginx/nginx-1.12.2.tar.gz ./ #拷贝nginx 解压版
sudo mkdir -p /usr/local/nginx-1.12.2
sudo rm -rf /usr/local/nginx-1.12.2/*
sudo tar -zxvf nginx-1.12.2.tar.gz -C /usr/local/nginx-1.12.2
sudo /usr/local/nginx-1.12.2/sbin/nginx
```

#### nginx 信息

下载地址: [http://nginx.org/download/nginx-1.12.2.tar.gz](http://nginx.org/download/nginx-1.12.2.tar.gz)

    启动方式: sudo /usr/local/nginx-1.12.2/sbin/nginx  #当前路径为mysql根路径
    停止方式: sudo kill -9 `ps aux | grep nginx-1.12.2 | grep -v 'color=auto' | awk '{print $2}'`
    配置文件: /usr/local/nginx-1.12.2/nginx-1.12.2/conf/nginx.conf #当前路径为mysql根路径
    默认访问端口: 8081



