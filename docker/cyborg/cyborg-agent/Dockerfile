FROM kolla/centos-source-cyborg-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="cyborg-agent" build-date="20200121"












RUN yum -y install pciutils \
    && yum clean all && rm -rf /var/cache/yum

RUN pip --no-cache-dir install --upgrade -c /requirements/upper-constraints.txt cursive 



ENV opae_libs_rpm_url=https://github.com/OPAE/opae-sdk/releases/download/1.1.0-2/opae-libs-1.1.0-2.x86_64.rpm
ENV opae_libs_rpm_sha1sum=3a10f80d64be46bb8d99ba88548646d0e368a06e

ENV opae_devel_rpm_url=https://github.com/OPAE/opae-sdk/releases/download/1.1.0-2/opae-devel-1.1.0-2.x86_64.rpm
ENV opae_devel_rpm_sha1sum=461356b987b41843f60123d66195620bf1e4e28e

RUN curl -sSL -o /tmp/opae-libs.rpm ${opae_libs_rpm_url} \
    && echo "${opae_libs_rpm_sha1sum} /tmp/opae-libs.rpm" | sha1sum -c \
    && curl -sSL -o /tmp/opae-devel.rpm ${opae_devel_rpm_url} \
    && echo "${opae_devel_rpm_sha1sum} /tmp/opae-devel.rpm" | sha1sum -c \
    && yum -y install /tmp/opae-libs.rpm /tmp/opae-devel.rpm \
    && rm -f /tmp/opae-libs.rpm /tmp/opae-devel.rpm

# NOTE(Bai Yongjun) Required packages are only supported Ubuntu16.04
# Please check the details:https://github.com/OPAE/opae-sdk/releases/tag/1.1.0-2


