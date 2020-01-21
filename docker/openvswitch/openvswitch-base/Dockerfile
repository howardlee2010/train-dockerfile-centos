FROM kolla/centos-source-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="openvswitch-base" build-date="20200121"








    

    
    
    

RUN yum -y install openvswitch tcpdump python-netifaces python-openvswitch \
    && yum clean all && rm -rf /var/cache/yum



COPY extend_start.sh /usr/local/bin/kolla_extend_start

RUN mv /usr/sbin/tcpdump /usr/bin/tcpdump \
    && touch /usr/local/bin/kolla_openvswitch_extend_start \
    && chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/kolla_openvswitch_extend_start

