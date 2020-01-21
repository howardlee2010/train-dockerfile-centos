FROM kolla/centos-source-storm:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="monasca-thresh" build-date="20200121"

USER root








RUN usermod --append --home /var/lib/monasca --groups kolla monasca \
    && mkdir -p /var/lib/monasca \
    && chown -R 42431:42431 /var/lib/monasca





    

ENV JAVA_HOME /usr/lib/jvm/jre-1.8.0-openjdk/



RUN yum -y install maven \
    && yum clean all && rm -rf /var/cache/yum

ADD monasca-thresh-archive /monasca-thresh-source
ADD additions/monasca-common* /monasca-common-source





# FIXME(dszumski): Remove this when the following bug is fixed:
# https://bugs.launchpad.net/ubuntu/+source/ca-certificates-java/+bug/1770553


RUN cd /monasca-common-source/java \
    && mvn clean install -DskipTests \
    && cd /monasca-thresh-source/monasca-thresh-*/thresh \
    && mvn clean package -DskipTests




# Overwrite the script inherited from Storm
COPY extend_start.sh /usr/local/bin/kolla_extend_start
RUN touch /usr/local/bin/kolla_monasca_extend_start \
    && chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/kolla_monasca_extend_start




USER monasca