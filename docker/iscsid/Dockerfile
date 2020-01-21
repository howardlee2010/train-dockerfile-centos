FROM kolla/centos-source-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="iscsid" build-date="20200121"






    

    
    
    



RUN yum -y install iscsi-initiator-utils targetcli python-rtslib \
    && yum clean all && rm -rf /var/cache/yum

COPY extend_start.sh /usr/local/bin/kolla_extend_start
RUN chmod 755 /usr/local/bin/kolla_extend_start \
    && rm /etc/iscsi/initiatorname.iscsi


