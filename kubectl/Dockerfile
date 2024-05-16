FROM alpine
MAINTAINER jason <ji@live.cn>

ENV KUBE_LATEST_VERSION="v1.30.0"

RUN apk add --update ca-certificates \
 && apk add -t deps \
 && apk add --update curl \
 && apk add gettext \
 && export ARCH="$(uname -m)" && if [[ ${ARCH} == "x86_64" ]]; then export ARCH="amd64"; elif [[ ${ARCH} == "aarch64" ]]; then export ARCH="arm64"; fi && curl -L https://dl.k8s.io/release/${KUBE_LATEST_VERSION}/bin/linux/${ARCH}/kubectl -o /usr/local/bin/kubectl \
 && chmod +x /usr/local/bin/kubectl \
 && apk del --purge deps \
 && rm /var/cache/apk/*

WORKDIR /root