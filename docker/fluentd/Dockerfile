FROM kolla/centos-source-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="fluentd" build-date="20200121"

LABEL fluentd_version="0.14" fluentd_binary="td-agent"
    








    

    
        
    






RUN usermod --append --home /var/lib/td-agent --groups kolla td-agent \
    && usermod --append --groups mysql td-agent \
    && mkdir -p /var/lib/td-agent \
    && chown -R 42447:42447 /var/lib/td-agent

RUN yum -y install gcc-c++ make td-agent \
    && yum clean all && rm -rf /var/cache/yum

# Distro specific files and operations
# Fluentd on rpm-based non-x86_64 is installed from rpm


COPY fluentd_sudoers /etc/sudoers.d/kolla_fluentd_sudoers

RUN chmod 440 /etc/sudoers.d/kolla_fluentd_sudoers \
    && mkdir -p /etc/td-agent \
    && mkdir -p /var/run/td-agent \
    && chown -R td-agent: /etc/td-agent /var/run/td-agent

COPY extend_start.sh /usr/local/bin/kolla_extend_start
RUN chmod 755 /usr/local/bin/kolla_extend_start




    


# NOTE(hrw): one of plugins fetches 'string-scrub' which tries to use
# /usr/bin/mkdir directly while in Debian it is in /bin


RUN ulimit -n 65536 && td-agent-gem install fluent-plugin-elasticsearch fluent-plugin-grep fluent-plugin-grok-parser fluent-plugin-parser fluent-plugin-rewrite-tag-filter




# Build and install Fluentd output plugin for Monasca Log API
ARG monasca_output_plugin_tag=0.1.1
ARG monasca_output_plugin_url=https://github.com/monasca/fluentd-monasca/archive/$monasca_output_plugin_tag.tar.gz

RUN curl -sSL $monasca_output_plugin_url -o /tmp/fluentd-monasca.tar.gz \
    && tar -xvf /tmp/fluentd-monasca.tar.gz -C /tmp \
    && cd /tmp/fluentd-monasca-* \

    && td-agent-gem build fluentd-monasca-output.gemspec \

    && ulimit -n 65536 && td-agent-gem install fluentd-monasca-output-*.gem \
    && rm -rf /tmp/fluentd*






USER td-agent