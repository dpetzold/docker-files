FROM alpine AS build

RUN apk --no-cache add curl  

ENV ETCD_VER=v3.3.5
ENV DOWNLOAD_URL=https://storage.googleapis.com/etcd

RUN curl -L ${DOWNLOAD_URL}/${ETCD_VER}/etcd-${ETCD_VER}-linux-amd64.tar.gz -o /tmp/etcd-${ETCD_VER}-linux-amd64.tar.gz && \
    mkdir /tmp/etcd && \
    tar xzvf /tmp/etcd-${ETCD_VER}-linux-amd64.tar.gz -C /tmp/etcd --strip-components=1

FROM scratch
COPY --from=build /tmp/etcd/etcdctl /
ENV ETCDCTL_API=3
ENTRYPOINT ["/etcdctl"]
