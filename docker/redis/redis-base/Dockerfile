FROM kolla/centos-source-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="redis-base" build-date="20200121"







RUN usermod --append --home /run/redis --groups kolla redis \
    && mkdir -p /run/redis \
    && chown -R 42460:42460 /run/redis


COPY extend_start.sh /usr/local/bin/kolla_extend_start
RUN chmod 755 /usr/local/bin/kolla_extend_start

