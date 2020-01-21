FROM kolla/centos-source-openstack-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="ironic-inspector" build-date="20200121"








RUN usermod --append --home /var/lib/ironic-inspector --groups kolla ironic-inspector \
    && mkdir -p /var/lib/ironic-inspector \
    && chown -R 42461:42461 /var/lib/ironic-inspector



    



ADD ironic-inspector-archive /ironic-inspector-source



RUN ln -s ironic-inspector-source/* ironic-inspector \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /ironic-inspector \
    && mkdir -p /etc/ironic-inspector \
    && cp /ironic-inspector/rootwrap.conf /etc/ironic-inspector/ \
    && cp -r /ironic-inspector/rootwrap.d/ /etc/ironic-inspector/ \
    && sed -i 's|^exec_dirs.*|exec_dirs=/var/lib/kolla/venv/bin,/sbin,/usr/sbin,/bin,/usr/bin,/usr/local/bin,/usr/local/sbin|g' /etc/ironic-inspector/rootwrap.conf

ADD ironic_inspector_sudoers /etc/sudoers.d/kolla_ironic_inspector_sudoers
RUN chmod 750 /etc/sudoers.d \
    && chmod 440 /etc/sudoers.d/kolla_ironic_inspector_sudoers



COPY extend_start.sh /usr/local/bin/kolla_extend_start

RUN chmod 755 /usr/local/bin/kolla_extend_start \
    && mkdir -p /var/lib/ironic-inspector/dhcp-hostsdir \
    && chown -R ironic-inspector: /etc/ironic-inspector /var/lib/ironic-inspector




USER ironic-inspector