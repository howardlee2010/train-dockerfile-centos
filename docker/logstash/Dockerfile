FROM kolla/centos-source-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="logstash" build-date="20200121"







RUN usermod --append --home /usr/share/logstash --groups kolla logstash \
    && chsh --shell /bin/bash logstash \
    && mkdir -p /usr/share/logstash \
    && chown -R 42478:42478 /usr/share/logstash



    

ENV JAVA_HOME /usr/lib/jvm/jre-1.8.0-openjdk/



RUN yum -y install java-1.8.0-openjdk-headless \
    && yum clean all && rm -rf /var/cache/yum
COPY extend_start.sh /usr/local/bin/kolla_extend_start

# FIXME(dszumski): Logstash was added to Kolla for Monasca. Monasca is
# currently tied to an old messaging version in Kafka (0.9) and doesn't
# work with Logstash 5.x or above. When Monasca is updated to use a more
# recent messaging version this patch should be reverted and the Monasca
# Logstash configuration files upgraded to use the new format.


ENV logstash_rpm_url=https://download.elastic.co/logstash/logstash/packages/centos/logstash-2.4.1.noarch.rpm
ENV logstash_rpm_sha1sum=68c5e78c3d941f06f77d638c0756b6aea715bec5
RUN curl -sSL -o /tmp/logstash.rpm ${logstash_rpm_url} \
    && echo "${logstash_rpm_sha1sum} /tmp/logstash.rpm" | sha1sum -c \
    && yum -y install /tmp/logstash.rpm \
    && rm -f /tmp/logstash.rpm



RUN chmod 755 /usr/local/bin/kolla_extend_start




USER logstash