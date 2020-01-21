FROM kolla/centos-source-cyborg-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="cyborg-api" build-date="20200121"





    
        
    



RUN yum -y install mod_ssl mod_wsgi \
    && yum clean all && rm -rf /var/cache/yum


RUN sed -i -r 's,^(Listen 80),#\1,' /etc/httpd/conf/httpd.conf \
    && sed -i -r 's,^(Listen 443),#\1,' /etc/httpd/conf.d/ssl.conf



COPY extend_start.sh /usr/local/bin/kolla_cyborg_extend_start
RUN chmod 755 /usr/local/bin/kolla_cyborg_extend_start


