FROM flb-build-base-opensuse/leap

ARG FLB_PREFIX
ARG FLB_VERSION

ENV FLB_TARBALL http://github.com/fluent/fluent-bit/archive/$FLB_PREFIX$FLB_VERSION.zip

RUN cd /tmp && \
    wget -O "/tmp/fluent-bit-${FLB_VERSION}.zip" ${FLB_TARBALL} && unzip "fluent-bit-$FLB_VERSION.zip" && \
    cd "/tmp/fluent-bit-${FLB_VERSION}/build" && \
    export CFLAGS="$CFLAGS -std=gnu99" && \
    cmake ../

CMD cd "/tmp/fluent-bit-${FLB_VERSION}/build/" && make && cp ./bin/fluent-bit /output/
