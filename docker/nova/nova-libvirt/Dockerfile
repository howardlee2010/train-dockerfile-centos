FROM kolla/centos-source-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="nova-libvirt" build-date="20200121"








RUN usermod --append --home /var/lib/nova --groups kolla nova \
    && usermod --append --groups qemu nova \
    && mkdir -p /var/lib/nova \
    && chown -R 42436:42436 /var/lib/nova




    
    
        
    



RUN yum -y install ceph-common cyrus-sasl-scram libguestfs libvirt-client libvirt-daemon libvirt-daemon-config-nwfilter libvirt-daemon-driver-lxc libvirt-daemon-driver-nwfilter openvswitch trousers qemu-kvm-ev \
    && yum clean all && rm -rf /var/cache/yum



COPY extend_start.sh /usr/local/bin/kolla_extend_start
RUN chmod 755 /usr/local/bin/kolla_extend_start


