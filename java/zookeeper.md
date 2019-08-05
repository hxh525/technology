#### zookeeper && kafka

[zookeeper下载](https://archive.apache.org/dist/zookeeper/current/)

[kafka下载](http://kafka.apache.org/downloads)

```
tar -zxvf zookeeper-3.4.14.tar.gz

sudo chmod -R 777 /home/ubuntu/zookeeper-3.4.14
sudo chmod -R 777 /home/ubuntu/kafka_2.11-2.3.0

cp /home/ubuntu/zookeeper-3.4.14/conf/zoo_sample.cfg  /home/ubuntu/zookeeper-3.4.14/conf/zoo.cfg

vi /home/ubuntu/zookeeper-3.4.14/conf/zoo.cfg
#dataDir=/app/zookeeper/data
#server.0=0.0.0.0:2888:3888
#server.1=106.52.105.162:2888:3888
#server.2=106.52.106.172:2888:3888

mkdir -p /app/zookeeper/data
echo 0 > /app/zookeeper/data/myid

vi /etc/profile
#export PATH=/home/ubuntu/zookeeper-3.4.14/bin:$PATH

source /etc/profile

zkServer.sh start
zkServer.sh status
zkServer.sh stop

tail -f /app/zookeeper/data/zookeeper.out
```

```
tar -zxvf kafka_2.11-2.3.0.tgz

sudo chmod -R 777 /home/ubuntu/kafka_2.11-2.3.0

vi /home/ubuntu/kafka_2.11-2.3.0/config/server.properties
#broker.id=0
#advertised.listeners=PLAINTEXT://106.52.102.223:9092
#log.dirs=/app/kafka/kafka-logs
#zookeeper.connect=172.16.0.15:2181,172.16.0.44:2181,172.16.0.9:2181

mkdir /app/kafka/kafka-logs

/home/ubuntu/kafka_2.11-2.3.0/bin/kafka-server-start.sh /home/ubuntu/kafka_2.11-2.3.0/config/server.properties 1>/dev/null 2>&1 &
```



