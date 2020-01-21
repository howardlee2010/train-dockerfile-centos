FROM kolla/centos-source-prometheus-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="prometheus-mtail" build-date="20200121"






ARG prometheus_mtail_version=v3.0.0-rc24
ARG prometheus_mtail_url=https://github.com/google/mtail/releases/download/${prometheus_mtail_version}/mtail_${prometheus_mtail_version}_linux_amd64



RUN curl -sSL -o /opt/mtail ${prometheus_mtail_url} \
    && chmod +x /opt/mtail





# NOTE(dszumski): We run as root so that mtail can scrape root owned logs
# such as /var/log/secure which are mounted into the container as read only
# for auditing purposes. Longer term we should use a more secure mechanism
# for tailing these logs.
USER root