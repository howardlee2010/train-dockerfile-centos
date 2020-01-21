FROM kolla/centos-source-monasca-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="monasca-api" build-date="20200121"







    
        
    
RUN yum -y install mariadb \
    && yum clean all && rm -rf /var/cache/yum

ADD monasca-api-archive /monasca-api-source



RUN ln -s monasca-api-source/* monasca-api \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt influxdb /monasca-api



COPY extend_start.sh /usr/local/bin/kolla_monasca_extend_start
RUN chmod 755 /usr/local/bin/kolla_monasca_extend_start



