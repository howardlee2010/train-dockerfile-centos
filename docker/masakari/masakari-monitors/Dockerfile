FROM kolla/centos-source-masakari-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="masakari-monitors" build-date="20200121"








RUN usermod --append --home /var/lib/masakari --groups kolla masakari \
    && mkdir -p /var/lib/masakari \
    && chown -R 42485:42485 /var/lib/masakari




    

        

    

RUN yum -y install libvirt-devel pacemaker-cli tcpdump \
    && yum clean all && rm -rf /var/cache/yum

ADD masakari-monitors-archive /masakari-monitors-source



RUN ln -s masakari-monitors-source/* masakari-monitors \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /masakari-monitors \
    && mkdir -p /etc/masakari-monitors \
    && chown -R masakari: /etc/masakari-monitors

COPY masakari_monitors_sudoers /etc/sudoers.d/kolla_masakari_monitors_sudoers

RUN chmod 750 /etc/sudoers.d \
    && chmod 640 /etc/sudoers.d/kolla_masakari_monitors_sudoers






USER masakari