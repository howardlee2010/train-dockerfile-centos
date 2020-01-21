FROM kolla/centos-source-ceilometer-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="ceilometer-compute" build-date="20200121"






    
        
    

RUN yum -y install libvirt-python \
    && yum clean all && rm -rf /var/cache/yum

# NOTE(jeffrey4l): just for back compatibility


RUN true






# NOTE(huikang): non-root user does not work with libvirt.sock.
#                Need configuration in nova-libvirt container to allow
#                USER ceilometer to access libvirt.sock