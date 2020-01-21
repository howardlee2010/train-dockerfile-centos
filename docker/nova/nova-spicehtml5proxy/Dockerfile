FROM kolla/centos-source-nova-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="nova-spicehtml5proxy" build-date="20200121"






    

        

    


RUN yum -y install numpy spice-html5 \
    && yum clean all && rm -rf /var/cache/yum




USER nova