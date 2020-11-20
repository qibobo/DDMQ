FROM centos:7

## Ports
EXPOSE 8080

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

RUN mkdir -p \
 /root/logs/rocketmqlogs \
 /root/store \
 /root/chronos-storage/rocksdb \
 /root/chronos-storage/seektimestamp \
 /root/chronos-storage/rocksdb_backup \
 /root/chronos-storage/rocksdb_restore

# copy
COPY . ${HOME_DIR}/console


# cmd
CMD bash -C '/root/chronos/control.sh start';'bash'
