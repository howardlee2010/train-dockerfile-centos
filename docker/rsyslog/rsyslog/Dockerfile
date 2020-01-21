FROM kolla/centos-source-rsyslog-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="rsyslog" build-date="20200121"






    


RUN yum -y install rsyslog-elasticsearch rsyslog-gnutls rsyslog-mmjsonparse rsyslog-mmnormalize \
    && yum clean all && rm -rf /var/cache/yum


