FROM kolla/centos-source-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="rabbitmq" build-date="20200121"








RUN usermod --append --home /var/lib/rabbitmq --groups kolla rabbitmq \
    && mkdir -p /var/lib/rabbitmq \
    && chown -R 42439:42439 /var/lib/rabbitmq




# NOTE(mandre) Remove rabbitmq-server pinning once package dependencies are met
# https://bugs.launchpad.net/kolla/+bug/1814233
    



RUN yum -y install erlang-hipe hostname rabbitmq-server-3.7.10 \
    && yum clean all && rm -rf /var/cache/yum





RUN rm -rf /var/lib/rabbitmq/* \
    && mkdir -p /usr/lib/rabbitmq/plugins \
    && /usr/lib/rabbitmq/bin/rabbitmq-plugins enable --offline \
       rabbitmq_management


    

ENV PLUGINS_DIR /usr/lib/rabbitmq/plugins

         RUN curl -L -o ${PLUGINS_DIR}/accept-0.3.3.ez https://github.com/deadtrickster/prometheus_rabbitmq_exporter/releases/download/v3.7.2.4/accept-0.3.3.ez
    
         RUN curl -L -o ${PLUGINS_DIR}/prometheus-3.5.1.ez https://github.com/deadtrickster/prometheus_rabbitmq_exporter/releases/download/v3.7.2.4/prometheus-3.5.1.ez
    
         RUN curl -L -o ${PLUGINS_DIR}/prometheus_cowboy-0.1.4.ez https://github.com/deadtrickster/prometheus_rabbitmq_exporter/releases/download/v3.7.2.4/prometheus_cowboy-0.1.4.ez
    
         RUN curl -L -o ${PLUGINS_DIR}/prometheus_httpd-2.1.8.ez https://github.com/deadtrickster/prometheus_rabbitmq_exporter/releases/download/v3.7.2.4/prometheus_httpd-2.1.8.ez
    
         RUN curl -L -o ${PLUGINS_DIR}/prometheus_rabbitmq_exporter-3.7.2.4.ez https://github.com/deadtrickster/prometheus_rabbitmq_exporter/releases/download/v3.7.2.4/prometheus_rabbitmq_exporter-3.7.2.4.ez
    


COPY extend_start.sh /usr/local/bin/kolla_extend_start
COPY rabbitmq_get_gospel_node.py /usr/local/bin/rabbitmq_get_gospel_node
RUN chmod 755 /usr/local/bin/kolla_extend_start /usr/local/bin/rabbitmq_get_gospel_node




USER rabbitmq