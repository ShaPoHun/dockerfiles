# Download extral binaries needed by 'kubeasz'
#
# @author:  gjmzj
# @repo:    https://github.com/kubeasz/dockerfiles/kubeasz-ext-bin
# @ref:     https://github.com/easzlab/kubeasz

FROM alpine:3.9

ENV ETCD_VER=v3.4.3 \
    CNI_VER=v0.8.6 \
    HELM_VER=v3.2.1 \
    DOCKER_COMPOSE_VER=1.23.2 \
    CALICOCTL_VER=v3.8.8 \
    EXT_BIN_VER=0.5.2

COPY cfssl_1.4.1_linux_arm64.tar.gz .

RUN mkdir -p /extra && \
    \
    wget https://github.com/etcd-io/etcd/releases/download/$ETCD_VER/etcd-$ETCD_VER-linux-arm64.tar.gz && \
    tar zxf etcd-$ETCD_VER-linux-arm64.tar.gz && \
    cd etcd-$ETCD_VER-linux-arm64 && \
    mv etcd etcdctl /extra && \
    cd / && rm -rf etcd-$ETCD_VER-linux-arm64* && \
    \
    tar zxvf cfssl_1.4.1_linux_arm64.tar.gz  --strip-components 1  -C /extra && \
    \
    wget https://github.com/containernetworking/plugins/releases/download/$CNI_VER/cni-plugins-linux-arm64-$CNI_VER.tgz && \
    mkdir /cni && tar zxf cni-plugins-linux-arm64-$CNI_VER.tgz -C /cni && \
    cd /cni && mv bridge flannel host-local loopback portmap tuning /extra && \
    cd / && rm -rf cni* && \
    \
    wget https://get.helm.sh/helm-$HELM_VER-linux-arm64.tar.gz && \
    tar zxf helm-$HELM_VER-linux-arm64.tar.gz && \
    mv linux-arm64/helm /extra && \
    rm -rf linux-arm64 helm-$HELM_VER-linux-arm64.tar.gz && \
    \
    wget https://github.com/projectcalico/calicoctl/releases/download/$CALICOCTL_VER/calicoctl-linux-arm64 && \
    mv calicoctl-linux-arm64 /extra/calicoctl

CMD [ "sleep", "360000000" ]
