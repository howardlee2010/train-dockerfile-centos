FROM kolla/centos-source-sensu-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="sensu-server" build-date="20200121"






    


RUN yum -y install cyrus-sasl-devel gcc-c++ make ruby-devel \
    && yum clean all && rm -rf /var/cache/yum



# Sensu plugins are all using semantic versioning.
# Let's cap them to the known major version that works with the ruby shipped on
# rhel/centos (currently 2.0)


RUN sensu-install --plugins mailer:"~>3",slack:"~>3"





USER sensu