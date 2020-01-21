FROM kolla/centos-source-kuryr-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="kuryr-libnetwork" build-date="20200121"






    

        

    
RUN yum -y install bridge-utils openvswitch \
    && yum clean all && rm -rf /var/cache/yum

ADD kuryr-libnetwork-archive /kuryr-libnetwork-source



RUN ln -s kuryr-libnetwork-source/* kuryr-libnetwork \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /kuryr-libnetwork




