FROM kolla/centos-source-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="kubernetes-entrypoint" build-date="20200121"




RUN curl -Lo /usr/local/bin/kubernetes-entrypoint https://github.com/stackanetes/kubernetes-entrypoint/releases/download/v0.3.0/kubernetes-entrypoint \
    && chmod 755 /usr/local/bin/kubernetes-entrypoint




CMD /usr/local/bin/kubernetes-entrypoint