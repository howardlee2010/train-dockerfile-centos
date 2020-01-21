FROM kolla/centos-source-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="ceph-base" build-date="20200121"








RUN usermod --append --home /var/lib/ceph --groups kolla ceph \
    && mkdir -p /var/lib/ceph \
    && chown -R 64045:64045 /var/lib/ceph




   

    
        
    


RUN yum -y install btrfs-progs ceph ceph-mgr-dashboard ceph-radosgw e2fsprogs gdisk hdparm parted smartmontools xfsprogs ceph-fuse \
    && yum clean all && rm -rf /var/cache/yum

COPY extend_start.sh /usr/local/bin/kolla_extend_start
RUN chmod 755 /usr/local/bin/kolla_extend_start

