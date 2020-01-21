FROM kolla/centos-source-openstack-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="cyborg-base" build-date="20200121"








RUN usermod --append --home /var/lib/cyborg --groups kolla cyborg \
    && mkdir -p /var/lib/cyborg \
    && chown -R 42483:42483 /var/lib/cyborg




ADD cyborg-base-archive /cyborg-base-source



RUN ln -s cyborg-base-source/* cyborg \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /cyborg



COPY extend_start.sh /usr/local/bin/kolla_extend_start
COPY cyborg_sudoers /etc/sudoers.d/kolla_cyborg_sudoers

RUN chmod 750 /etc/sudoers.d \
    && touch /usr/local/bin/kolla_cyborg_extend_start \
    && chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/kolla_cyborg_extend_start


