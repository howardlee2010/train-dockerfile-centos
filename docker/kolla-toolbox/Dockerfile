FROM kolla/centos-source-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="kolla-toolbox" build-date="20200121"











RUN usermod --append --home /var/lib/ansible --groups kolla ansible \
    && mkdir -p /var/lib/ansible \
    && chown -R 42401:42401 /var/lib/ansible




RUN usermod --append --home /var/lib/rabbitmq --groups kolla rabbitmq \
    && mkdir -p /var/lib/rabbitmq \
    && chown -R 42439:42439 /var/lib/rabbitmq


# NOTE(mandre) Remove rabbitmq-server pinning once package dependencies are met
# https://bugs.launchpad.net/kolla/+bug/1814233

    


RUN yum -y install crudini gcc gdisk git jq libffi-devel libxml2-devel libxslt-devel make mariadb mariadb-devel openssh-clients openssl-devel python-devel rabbitmq-server-3.7.10 \
    && yum clean all && rm -rf /var/cache/yum




    

RUN curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py \
    && python get-pip.py \
    && rm get-pip.py





RUN pip --no-cache-dir install --upgrade virtualenv \
    && virtualenv --system-site-packages /opt/ansible

ENV PATH /opt/ansible/bin:$PATH



RUN mkdir -p /requirements \
    && curl -sSL -o /requirements/upper-constraints.txt https://releases.openstack.org/constraints/upper/train \
    && pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt ansible==2.8.* cmd2 influxdb mysqlclient os-client-config pbr pymongo python-openstackclient pytz pyudev shade \
    && mkdir -p /etc/ansible /usr/share/ansible \
    && echo 'localhost ansible_connection=local ansible_python_interpreter=/opt/ansible/bin/python' > /etc/ansible/hosts \
    && sed -i 's|  "identity_api_version": "2.0",|  "identity_api_version": "3",|' /opt/ansible/lib/python2.7/site-packages/os_client_config/defaults.json

ENV ANSIBLE_LIBRARY /usr/share/ansible:$ANSIBLE_LIBRARY

COPY find_disks.py kolla_keystone_service.py kolla_keystone_user.py kolla_sanity.py /usr/share/ansible/
COPY ansible.cfg /var/lib/ansible/.ansible.cfg
RUN chmod 644 /usr/share/ansible/find_disks.py \
              /usr/share/ansible/kolla_keystone_service.py \
              /usr/share/ansible/kolla_keystone_user.py \
              /usr/share/ansible/kolla_sanity.py \
              /var/lib/ansible/.ansible.cfg

COPY ansible_sudoers /etc/sudoers.d/kolla_ansible_sudoers
RUN chmod 440 /etc/sudoers.d/kolla_ansible_sudoers




USER ansible