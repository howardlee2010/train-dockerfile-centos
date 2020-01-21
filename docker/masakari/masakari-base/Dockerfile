FROM kolla/centos-source-openstack-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="masakari-base" build-date="20200121"








RUN usermod --append --home /var/lib/masakari --groups kolla masakari \
    && mkdir -p /var/lib/masakari \
    && chown -R 42485:42485 /var/lib/masakari




    

        
        
        
        

RUN yum -y install httpd mod_ssl mod_wsgi python2-ldappool \
    && yum clean all && rm -rf /var/cache/yum
RUN mkdir -p /var/www/cgi-bin/masakari \
    && sed -i -r 's,^(Listen 80),#\1,' /etc/httpd/conf/httpd.conf \
    && sed -i -r 's,^(Listen 443),#\1,' /etc/httpd/conf.d/ssl.conf

    

ADD masakari-base-archive /masakari-base-source



RUN ln -s masakari-base-source/* masakari \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /masakari \
    && mkdir -p /etc/masakari /var/www/cgi-bin/masakari \
    && chown -R masakari: /etc/masakari /var/www/cgi-bin/masakari



COPY extend_start.sh /usr/local/bin/kolla_extend_start

RUN touch /usr/local/bin/kolla_masakari_extend_start \
    && chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/kolla_masakari_extend_start \
    && chmod 755 /var/www/cgi-bin/masakari

