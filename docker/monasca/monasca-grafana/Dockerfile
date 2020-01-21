FROM kolla/centos-source-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="monasca-grafana" build-date="20200121"







RUN usermod --append --home /usr/share/grafana --groups kolla monasca \
    && mkdir -p /usr/share/grafana \
    && chown -R 42431:42431 /usr/share/grafana



    


RUN yum -y install golang git npm bzip2 gcc-c++ make ruby ruby-devel fontconfig rpm-build \
    && yum clean all && rm -rf /var/cache/yum

WORKDIR /usr/share/grafana

COPY grafana_sudoers /etc/sudoers.d/kolla_grafana_sudoers
COPY extend_start.sh /usr/local/bin/kolla_extend_start

ENV GO_PATH=/grafana
ENV monasca_grafana_build_path=${GO_PATH}/src/github.com/grafana/grafana
ARG monasca_grafana_version=grafana4_2
ARG monasca_grafana_url=https://github.com/monasca/grafana/archive/$monasca_grafana_version.tar.gz


# NOTE(mgoddard): Pinning rake because rake 13.0.0 depends on Ruby 2.2, and CentOS 7 only provides
# Ruby 2.0.
# NOTE(yoctozepto): Update npm to 6.x version to avoid issues with metadata parsing.
# NPM installs itself in /usr/local/bin (the default in Ubuntu) which is not in the PATH.
# This is forced for all distros to avoid conflicts with native packages.
RUN gem install rake:"~>12" fpm \
    && curl -sSL -o /tmp/monasca-grafana.tgz ${monasca_grafana_url} \
    && mkdir -p ${monasca_grafana_build_path} \
    && tar --strip 1 -xvf /tmp/monasca-grafana.tgz -C ${monasca_grafana_build_path} \
    && rm -f /tmp/monasca-grafana.tgz \
    && cd ${monasca_grafana_build_path} \
    && go run build.go setup \
    && npm config set prefix /usr/local -g \
    && npm install npm@6.x -g \
    && /usr/local/bin/npm install \
    && go run build.go build package \
    && mv ${monasca_grafana_build_path}/dist /grafana_pkgs \
    && rm -rf /grafana


  


RUN yum -y install /grafana_pkgs/grafana*.rpm \
    && yum clean all && rm -rf /var/cache/yum



RUN grafana-cli plugins install monasca-datasource \
    && chmod 750 /etc/sudoers.d \
    && chmod 440 /etc/sudoers.d/kolla_grafana_sudoers \
    && chmod 755 /usr/local/bin/kolla_extend_start




USER monasca