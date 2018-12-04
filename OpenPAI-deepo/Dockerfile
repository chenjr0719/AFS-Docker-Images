FROM ufoym/deepo:all-py36

ENV HADOOP_VERSION=2.7.2
ENV DEBIAN_FRONTEND=noninteractive
# LABEL HADOOP_VERSION=2.7.2

RUN DEBIAN_FRONTEND=noninteractive && \
    apt-get -y update && \
    apt-get -y install --no-install-recommends curl \
        unzip \
        automake \
        openjdk-8-jdk \
        openssh-server \
        openssh-client \
        lsof \
        libcupti-dev && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

RUN wget -qO- http://archive.apache.org/dist/hadoop/common/hadoop-${HADOOP_VERSION}/hadoop-${HADOOP_VERSION}.tar.gz | \
    tar xz -C /usr/local && \
    mv /usr/local/hadoop-${HADOOP_VERSION} /usr/local/hadoop

ENV JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64 \
    HADOOP_INSTALL=/usr/local/hadoop \
    NVIDIA_VISIBLE_DEVICES=all

ENV HADOOP_PREFIX=${HADOOP_INSTALL} \
    HADOOP_BIN_DIR=${HADOOP_INSTALL}/bin \
    HADOOP_SBIN_DIR=${HADOOP_INSTALL}/sbin \
    HADOOP_HDFS_HOME=${HADOOP_INSTALL} \
    HADOOP_COMMON_LIB_NATIVE_DIR=${HADOOP_INSTALL}/lib/native \
    HADOOP_OPTS="-Djava.library.path=${HADOOP_INSTALL}/lib/native"

ENV PATH=/usr/local/nvidia/bin:/usr/local/cuda/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:${HADOOP_BIN_DIR}:${HADOOP_SBIN_DIR} \
    LD_LIBRARY_PATH=/usr/local/nvidia/lib:/usr/local/nvidia/lib64:/usr/local/cuda/lib64:/usr/local/cuda/targets/x86_64-linux/lib/stubs:${JAVA_HOME}/jre/lib/amd64/server

RUN mkdir /AFS
WORKDIR /AFS