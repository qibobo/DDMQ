FROM centos:7

## Ports
EXPOSE 9613
EXPOSE 9713
EXPOSE 8080
EXPOSE 2181

# Env
ENV HOME_DIR /root
ENV HOME /root

WORKDIR ${HOME_DIR}

RUN yum install -y java-1.8.0-openjdk java-1.8.0-openjdk-devel unzip gettext nmap-ncat openssl wget telnet\
  && yum clean all -y

RUN curl https://mirrors.cnnic.cn/apache/tomcat/tomcat-9/v9.0.39/bin/apache-tomcat-9.0.39.zip -o tomcat.zip \
  && unzip tomcat.zip \ 
  && mv apache-tomcat-9.0.39 tomcat \
  && rm tomcat.zip \ 
  && chmod +x tomcat/bin/*.sh

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

# copy
COPY console ${HOME_DIR}/console
COPY consumer ${HOME_DIR}/consumer
COPY producer ${HOME_DIR}/producer
COPY chronos ${HOME_DIR}/chronos
COPY broker ${HOME_DIR}/broker
COPY namesvr ${HOME_DIR}/namesvr
COPY start.sh ${HOME_DIR}/start.sh

# cmd
CMD bash -C '/root/start.sh';'bash'
