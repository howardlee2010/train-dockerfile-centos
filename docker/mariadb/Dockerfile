FROM kolla/centos-source-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="mariadb" build-date="20200121"








RUN usermod --append --home /var/lib/mysql --groups kolla mysql \
    && mkdir -p /var/lib/mysql \
    && chown -R 42434:42434 /var/lib/mysql



    



RUN yum -y install expect galera hostname mariadb mariadb-backup mariadb-server-galera mariadb-server-utils pv rsync tar \
    && yum clean all && rm -rf /var/cache/yum

COPY mariadb_sudoers /etc/sudoers.d/kolla_mariadb_sudoers
COPY extend_start.sh /usr/local/bin/kolla_extend_start
COPY security_reset.expect /usr/local/bin/kolla_security_reset
RUN chmod 755 /usr/local/bin/kolla_extend_start \
    && chmod 755 /usr/local/bin/kolla_security_reset \
    && chmod 750 /etc/sudoers.d \
    && chmod 440 /etc/sudoers.d/kolla_mariadb_sudoers \
    && rm -rf /var/lib/mysql/*



COPY backup.sh /usr/local/bin/kolla_mariadb_backup.sh
RUN chmod 755 /usr/local/bin/kolla_mariadb_backup.sh



# NOTE(mgoddard): Override the dumb-init arguments to avoid passing
# --single-child. This does not play well with mysqld_safe, which ignores
# SIGTERM, meaning Docker needs to forcibly kill the container to stop it.
# Without --single-child, the TERM signal is sent to all subprocesses,
# including mysqld.

ENTRYPOINT ["dumb-init", "--"]
CMD ["kolla_start"]






USER mysql