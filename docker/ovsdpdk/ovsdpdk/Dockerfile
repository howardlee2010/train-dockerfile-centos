FROM kolla/centos-source-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="ovsdpdk" build-date="20200121"








#TODO(sean-k-mooney) create repo via open suse build system to package
# for centos/rhel distros.

RUN echo 'source not yet available for centos' \
    && /bin/false





COPY extend_start.sh /usr/local/bin/kolla_extend_start
RUN chmod 755 /usr/local/bin/kolla_extend_start


