FROM alpine:3.5
MAINTAINER SpringerNature PE "platform-engineering@springer.com"

RUN apk update && \
    apk upgrade && \
    apk add --no-cache --update unzip curl openssl ca-certificates libc6-compat libxml2 xmlsec tzdata yaml readline && \
    ln -s /lib/ /lib64

ONBUILD ARG TZ=Europe/Amsterdam
ONBUILD ENV TZ $TZ
ONBUILD RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

ARG BOSH_VERSION="2.0.16"

RUN wget -nv https://s3.amazonaws.com/bosh-cli-artifacts/bosh-cli-${BOSH_VERSION}-linux-amd64 -O /usr/local/bin/bosh2 && chmod 755 /usr/local/bin/bosh2

# ENTRYPOINT ["bosh2"]
CMD ["bosh2"]
