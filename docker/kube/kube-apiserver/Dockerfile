FROM kolla/centos-source-kube-base:9.0.1
LABEL maintainer="Kolla Project (https://launchpad.net/kolla)" name="kube-apiserver" build-date="20200121"

ENV KUBERNETES_COMPONENT=kube-apiserver




RUN true \
    && curl -L ${KUBERNETES_DOWNLOAD_ROOT}/${KUBERNETES_COMPONENT} -o /usr/bin/${KUBERNETES_COMPONENT} \
    && chmod +x /usr/bin/${KUBERNETES_COMPONENT}


# Clear any customisation by Kolla to entrypoint & command
ENTRYPOINT []
CMD []


