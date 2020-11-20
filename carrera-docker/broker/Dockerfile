FROM centos:7

## Ports
EXPOSE 10911
# Env
ENV HOME_DIR /root
ENV HOME /root

WORKDIR ${HOME_DIR}

RUN yum install -y java-1.8.0-openjdk java-1.8.0-openjdk-devel unzip gettext nmap-ncat openssl wget telnet\
  && yum clean all -y

RUN mkdir -p \
 /root/logs/rocketmqlogs \
 /root/store \
 /root/chronos-storage/rocksdb \
 /root/chronos-storage/seektimestamp \
 /root/chronos-storage/rocksdb_backup \
 /root/chronos-storage/rocksdb_restore

# copy

COPY . ${HOME_DIR}/broker


# cmd
CMD bash -C '/root/broker/control.sh start';'bash'
