FROM kolla/centos-source-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="kubetoolbox" build-date="20200121"









RUN yum -y install ceph-common ipmitool jq \
    && yum clean all && rm -rf /var/cache/yum


    
    # TODO(mandre) check for file integrity instead of downloading from an HTTPS source
    RUN curl -o /usr/bin/kubectl https://storage.googleapis.com/kubernetes-release/release/v1.11.0/bin/linux/amd64/kubectl \
        && chmod 755 /usr/bin/kubectl




