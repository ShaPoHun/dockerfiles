# Download kubernetes binaries needed by 'kubeasz'
#
# @author:  gjmzj
# @repo:    https://github.com/kubeasz/dockerfiles/kubeasz-k8s-bin
# @ref:     https://github.com/easzlab/kubeasz

FROM alpine:3.9

ENV K8S_VER=v1.16.15

RUN wget https://dl.k8s.io/$K8S_VER/kubernetes-server-linux-arm64.tar.gz && \
    tar zxf kubernetes-server-linux-arm64.tar.gz && \
    mkdir -p /k8s && cd kubernetes/server/bin && \
    mv kube-apiserver kube-controller-manager kube-scheduler /k8s && \
    mv kubelet kube-proxy kubectl /k8s && \
    cd / && rm -rf kubernetes*

CMD [ "sleep", "360000000" ]
