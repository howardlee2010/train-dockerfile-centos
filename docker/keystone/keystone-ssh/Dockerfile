FROM kolla/centos-source-keystone-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="keystone-ssh" build-date="20200121"








RUN usermod --append --home /var/lib/keystone --groups kolla keystone \
    && chsh --shell /bin/bash keystone \
    && mkdir -p /var/lib/keystone \
    && chown -R 42425:42425 /var/lib/keystone



    

RUN yum -y install openssh-server rsync \
    && yum clean all && rm -rf /var/cache/yum

RUN sed -ri 's/session(\s+)required(\s+)pam_loginuid.so/session\1optional\2pam_loginuid.so/' /etc/pam.d/sshd

COPY extend_start.sh /usr/local/bin/kolla_extend_start
RUN chmod 755 /usr/local/bin/kolla_extend_start


