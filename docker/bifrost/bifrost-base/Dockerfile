FROM kolla/centos-source-openstack-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="bifrost-base" build-date="20200121"








RUN usermod --append --home /var/lib/bifrost --groups kolla bifrost \
    && mkdir -p /var/lib/bifrost \
    && chown -R 42404:42404 /var/lib/bifrost




ENV VENV /var/lib/kolla/venv



ADD bifrost-base-archive /bifrost-base-source
COPY build_arg.yml /tmp/build_arg.yml
RUN ln -s bifrost-base-source/* bifrost \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt /bifrost

WORKDIR /bifrost



RUN rm -f /etc/yum.repos.d/rabbitmq_rabbitmq-server.repo \
    && yum clean all &&  rm -rf /var/yum/cache



ENV ANSIBLE_GATHER_TIMEOUT=30



RUN echo " " && \

    bash -c './scripts/env-setup.sh && source ./env-vars && \
    ansible-playbook -vvvv -i /bifrost/playbooks/inventory/target /bifrost/playbooks/install.yaml \
    -e @/tmp/build_arg.yml && \

    yum clean all && rm -rf /var/yum/cache'




COPY bifrost_sudoers /etc/sudoers.d/kolla_bifrost_sudoers

RUN chmod 750 /etc/sudoers.d \
    && chmod 440 /etc/sudoers.d/kolla_bifrost_sudoers \
    && chown -R bifrost:bifrost /bifrost

