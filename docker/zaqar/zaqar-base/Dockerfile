FROM kolla/centos-source-openstack-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="zaqar-base" build-date="20200121"








RUN usermod --append --home /var/lib/zaqar --groups kolla zaqar \
    && mkdir -p /var/lib/zaqar \
    && chown -R 42452:42452 /var/lib/zaqar




    
        
        
        
        

RUN yum -y install httpd mod_ssl mod_wsgi python2-ldappool \
    && yum clean all && rm -rf /var/cache/yum \
    && sed -i -r 's,^(Listen 80),#\1,' /etc/httpd/conf/httpd.conf \
    && sed -i -r 's,^(Listen 443),#\1,' /etc/httpd/conf.d/ssl.conf

    



ADD zaqar-base-archive /zaqar-base-source

RUN ln -s zaqar-base-source/* zaqar \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt pymongo /zaqar gevent \
    && mkdir -p /etc/zaqar /var/lib/zaqar /var/www/cgi-bin/zaqar \
    && cp -r /zaqar/etc/* /etc/zaqar/ \
    && cp /zaqar/zaqar/transport/wsgi/app.py /var/www/cgi-bin/zaqar \
    && chown -R zaqar: /etc/zaqar /var/lib/zaqar /var/www/cgi-bin/zaqar



COPY extend_start.sh /usr/local/bin/kolla_extend_start
RUN touch /usr/local/bin/kolla_zaqar_extend_start \
    && chmod 755 /var/www/cgi-bin/zaqar \
    && chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/kolla_zaqar_extend_start

