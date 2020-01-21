FROM kolla/centos-source-openstack-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="ceilometer-base" build-date="20200121"








RUN usermod --append --home /var/lib/ceilometer --groups kolla ceilometer \
    && mkdir -p /var/lib/ceilometer \
    && chown -R 42405:42405 /var/lib/ceilometer








ADD ceilometer-base-archive /ceilometer-base-source
ADD plugins-archive /
# NOTE(egonzalez): Remove ceilometer from constraint or will fail.
RUN ln -s ceilometer-base-source/* ceilometer \
    && sed -i 's|^ceilometer===.*$||g' requirements/upper-constraints.txt \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /ceilometer[gnocchi,mongo,mysql] \
    && mkdir -p /etc/ceilometer \
    && cp -r /ceilometer/etc/ceilometer/* /etc/ceilometer/ \
    && chown -R ceilometer: /etc/ceilometer \
    && sed -i 's|^exec_dirs.*|exec_dirs=/var/lib/kolla/venv/bin,/sbin,/usr/sbin,/bin,/usr/bin,/usr/local/bin,/usr/local/sbin|g' /etc/ceilometer/rootwrap.conf \
    && if [ "$(ls /plugins)" ]; then \
        pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /plugins/*; \
    fi



COPY ceilometer_sudoers /etc/sudoers.d/kolla_ceilometer_sudoers
COPY extend_start.sh /usr/local/bin/kolla_extend_start

RUN chmod 750 /etc/sudoers.d \
    && chmod 440 /etc/sudoers.d/kolla_ceilometer_sudoers \
    && touch /usr/local/bin/kolla_ceilometer_extend_start \
    && chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/kolla_ceilometer_extend_start

