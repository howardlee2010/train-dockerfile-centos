FROM kolla/centos-source-ironic-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="ironic-pxe" build-date="20200121"






    
    
    
    

    
        
    

    

RUN yum -y install httpd ipxe-bootimgs mod_ssl tftp-server mod_wsgi syslinux-tftpboot \
    && yum clean all && rm -rf /var/cache/yum
RUN sed -i -r 's,^(Listen 80),#\1,' /etc/httpd/conf/httpd.conf \
    && sed -i -r 's,^(Listen 443),#\1,' /etc/httpd/conf.d/ssl.conf


COPY tftp-map-file /map-file
COPY extend_start.sh /usr/local/bin/kolla_ironic_extend_start
RUN chmod 755 /usr/local/bin/kolla_ironic_extend_start


