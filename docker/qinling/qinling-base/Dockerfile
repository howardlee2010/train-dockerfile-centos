FROM kolla/centos-source-openstack-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="qinling-base" build-date="20200121"








RUN usermod --append --home /var/lib/qinling --groups kolla qinling \
    && mkdir -p /var/lib/qinling \
    && chown -R 42484:42484 /var/lib/qinling




    

        
        
        
        

RUN yum -y install httpd mod_ssl mod_wsgi python2-ldappool \
    && yum clean all && rm -rf /var/cache/yum
RUN mkdir -p /var/www/cgi-bin/qinling \
    && sed -i -r 's,^(Listen 80),#\1,' /etc/httpd/conf/httpd.conf \
    && sed -i -r 's,^(Listen 443),#\1,' /etc/httpd/conf.d/ssl.conf

    

ADD qinling-base-archive /qinling-base-source



RUN ln -s qinling-base-source/* qinling \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /qinling \
    && mkdir -p /etc/qinling /var/www/cgi-bin/qinling \
    && cp -r /qinling/etc/policy.json.sample /etc/qinling/policy.json \
    && cp /qinling/qinling/api/wsgi.py /var/www/cgi-bin/qinling \
    && chown -R qinling: /etc/qinling /var/www/cgi-bin/qinling



COPY extend_start.sh /usr/local/bin/kolla_extend_start

RUN touch /usr/local/bin/kolla_qinling_extend_start \
    && chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/kolla_qinling_extend_start \
    && chmod 755 /var/www/cgi-bin/qinling

