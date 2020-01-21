FROM kolla/centos-source-openstack-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="zun-base" build-date="20200121"








RUN usermod --append --home /var/lib/zun --groups kolla zun \
    && mkdir -p /var/lib/zun \
    && chown -R 42463:42463 /var/lib/zun




    

        
        
        
        

RUN yum -y install httpd mod_ssl numactl mod_wsgi python2-ldappool \
    && yum clean all && rm -rf /var/cache/yum
RUN mkdir -p /var/www/cgi-bin/zun \
    && sed -i -r 's,^(Listen 80),#\1,' /etc/httpd/conf/httpd.conf \
    && sed -i -r 's,^(Listen 443),#\1,' /etc/httpd/conf.d/ssl.conf

    

ADD zun-base-archive /zun-base-source



RUN ln -s zun-base-source/* zun \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /zun \
    && mkdir -p /etc/zun /var/www/cgi-bin/zun \
    && cp -r /zun/etc/zun/* /etc/zun/ \
    && cp /zun/zun/api/app.wsgi /var/www/cgi-bin/zun \
    && chown -R zun: /etc/zun /var/www/cgi-bin/zun \
    && sed -i 's|^exec_dirs.*|exec_dirs=/var/lib/kolla/venv/bin,/sbin,/usr/sbin,/bin,/usr/bin,/usr/local/bin,/usr/local/sbin|g' /etc/zun/rootwrap.conf



COPY zun_sudoers /etc/sudoers.d/kolla_zun_sudoers
COPY extend_start.sh /usr/local/bin/kolla_extend_start

RUN chmod 750 /etc/sudoers.d \
    && chmod 640 /etc/sudoers.d/kolla_zun_sudoers \
    && touch /usr/local/bin/kolla_zun_extend_start \
    && chmod 755 /var/www/cgi-bin/zun \
    && chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/kolla_zun_extend_start

