FROM kolla/centos-source-ironic-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="ironic-conductor" build-date="20200121"






    
        
        
        
        
    



RUN pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt -r /ironic/driver-requirements.txt ironic-staging-drivers


RUN yum -y install dosfstools e2fsprogs fuse gdisk ipmitool parted psmisc qemu-img-ev shellinabox util-linux xfsprogs systemd \
    && yum clean all && rm -rf /var/cache/yum




USER ironic