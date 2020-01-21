FROM kolla/centos-source-openstack-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="placement-base" build-date="20200121"








RUN usermod --append --home /var/lib/placement --groups kolla placement \
    && mkdir -p /var/lib/placement \
    && chown -R 42482:42482 /var/lib/placement




    

        

    
RUN yum -y install mariadb \
    && yum clean all && rm -rf /var/cache/yum

ADD placement-base-archive /placement-base-source
ADD plugins-archive /



RUN ln -s placement-base-source/* placement \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /placement \
    && mkdir -p /etc/placement/ \
    && cp -r /placement/etc/placement/* /etc/placement/ \
    && chown -R placement: /etc/placement/ \
    && cp /placement/tools/mysql-migrate-db.sh /opt/ \
    && chmod 755 /opt/mysql-migrate-db.sh



COPY extend_start.sh /usr/local/bin/kolla_extend_start

RUN touch /usr/local/bin/kolla_placement_extend_start \
    && chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/kolla_placement_extend_start

