FROM kolla/centos-source-manila-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="manila-api" build-date="20200121"







    
        
        
        
        
RUN yum -y install httpd mod_ssl mod_wsgi \
    && yum clean all && rm -rf /var/cache/yum
RUN sed -i -r 's,^(Listen 80),#\1,' /etc/httpd/conf/httpd.conf \
    && sed -i -r 's,^(Listen 443),#\1,' /etc/httpd/conf.d/ssl.conf

    

RUN mkdir -p /var/www/cgi-bin/manila \
    && cp -a /var/lib/kolla/venv/bin/manila-wsgi /var/www/cgi-bin/manila/manila-wsgi



COPY extend_start.sh /usr/local/bin/kolla_manila_extend_start
RUN chmod 755 /usr/local/bin/kolla_manila_extend_start \
    && chown -R manila: /var/www/cgi-bin/manila \
    && chmod 755 /var/www/cgi-bin/manila/manila-wsgi




USER manila