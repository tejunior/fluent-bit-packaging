FROM flb-build-base-amazonlinux/2.arm64v8

ARG FLB_PREFIX
ARG FLB_VERSION
ARG FLB_SRC

ENV FLB_TARBALL http://github.com/fluent/fluent-bit/archive/$FLB_PREFIX$FLB_VERSION.zip
COPY sources/$FLB_SRC /

RUN cd /tmp && \
    if [ "x$FLB_SRC" = "x" ] ; then wget -O "/tmp/fluent-bit-${FLB_VERSION}.zip" ${FLB_TARBALL} && unzip "fluent-bit-$FLB_VERSION.zip" ; else tar zxfv "/$FLB_SRC" ; fi && \
    cd "fluent-bit-$FLB_VERSION/build/" && \
    cmake3 ../

CMD cd "/tmp/fluent-bit-${FLB_VERSION}/build/" && make && cp ./bin/fluent-bit /output/
