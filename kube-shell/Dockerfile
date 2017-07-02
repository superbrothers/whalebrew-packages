FROM python:3-alpine

LABEL io.whalebrew.name kube-shell
LABEL io.whalebrew.config.volumes '["~/.kube:/.kube","~/.minikube:/.minikube"]'

ENV KUBECTL_VERSION v1.6.6
ENV KUBE_SHELL_VERSION 0.0.17

RUN set -x && \
    apk --update add --no-cache --virtual deps curl && \
    curl -sLO https://storage.googleapis.com/kubernetes-release/release/${KUBECTL_VERSION}/bin/linux/amd64/kubectl && \
    chmod +x ./kubectl && \
    mv ./kubectl /usr/local/bin/kubectl && \
    apk del deps

RUN set -x && \
    pip install --no-cache-dir \
        kube-shell==$KUBE_SHELL_VERSION

ENTRYPOINT ["kube-shell"]
