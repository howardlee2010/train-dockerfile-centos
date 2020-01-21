FROM kolla/centos-source-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="kafka" build-date="20200121"







RUN usermod --append --home /opt/kafka --groups kolla kafka \
    && mkdir -p /opt/kafka \
    && chown -R 42423:42423 /opt/kafka



    


RUN yum -y install java-1.8.0-openjdk-headless \
    && yum clean all && rm -rf /var/cache/yum


ENV kafka_version=1.0.2
ENV kafka_scala_version=2.12
ENV kafka_url=https://archive.apache.org/dist/kafka/${kafka_version}/kafka_${kafka_scala_version}-${kafka_version}.tgz
ENV kafka_pkg_sha512sum=4cbcdaf8ccc4efe3d1b6275f3f2c32cf8f2f1a62104b5dd0bd9e2974160ab89d85a6e1791af8b948a413b99ed696b06ea9d4299b27ea63c3f7318dabf5761144



RUN curl -sSL -o /tmp/kafka.tgz ${kafka_url} \
    && echo "${kafka_pkg_sha512sum} /tmp/kafka.tgz" | sha512sum -c \
    && tar --strip 1 -xvf /tmp/kafka.tgz -C /opt/kafka \
    && rm -f /tmp/kafka.tgz


COPY extend_start.sh /usr/local/bin/kolla_extend_start
RUN chmod 755 /usr/local/bin/kolla_extend_start




USER kafka