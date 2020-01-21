FROM kolla/centos-source-ceph-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="cephfs-fuse" build-date="20200121"






# Clear any customisation by Kolla to entrypoint & command
ENTRYPOINT ["/usr/bin/ceph-fuse"]
CMD []