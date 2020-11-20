FROM centos:7

## Ports

EXPOSE 2181

# Env
ENV HOME_DIR /root
ENV HOME /root

WORKDIR ${HOME_DIR}

RUN yum install -y java-1.8.0-openjdk java-1.8.0-openjdk-devel unzip gettext nmap-ncat openssl wget telnet\
  && yum clean all -y



RUN curl https://mirrors.cnnic.cn/apache/zookeeper/zookeeper-3.6.2/apache-zookeeper-3.6.2-bin.tar.gz -o zookeeper-3.6.2.tar.gz \
  && tar xzvf zookeeper-3.6.2.tar.gz \
  && rm zookeeper-3.6.2.tar.gz \ 
  && cp apache-zookeeper-3.6.2-bin/conf/zoo_sample.cfg apache-zookeeper-3.6.2-bin/conf/zoo.cfg \ 
  && echo "admin.serverPort=8888" >> apache-zookeeper-3.6.2-bin/conf/zoo.cfg

RUN mkdir -p \
 /root/logs/rocketmqlogs \
 /root/store \
 /root/chronos-storage/rocksdb \
 /root/chronos-storage/seektimestamp \
 /root/chronos-storage/rocksdb_backup \
 /root/chronos-storage/rocksdb_restore

# cmd
CMD bash -C '/root/apache-zookeeper-3.6.2-bin/bin/zkServer.sh start';'bash'

