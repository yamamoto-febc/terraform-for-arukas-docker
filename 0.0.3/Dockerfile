FROM alpine:3.4
MAINTAINER Kazumichi Yamamoto <yamamoto.febc@gmail.com>

ENV GLIBC_VERSION "2.23-r1"
ENV TERRAFORM_VERSION "0.7.0"
ENV ARUKAS_VERSION "0.0.3"

RUN set -x && apk add --no-cache --virtual curl unzip ca-certificates bash && \
    curl -LO https://github.com/andyshinn/alpine-pkg-glibc/releases/download/${GLIBC_VERSION}/glibc-${GLIBC_VERSION}.apk && \
    apk add --allow-untrusted glibc-${GLIBC_VERSION}.apk && \
    curl -L https://releases.hashicorp.com/terraform/${TERRAFORM_VERSION}/terraform_${TERRAFORM_VERSION}_linux_amd64.zip > /usr/local/bin/terraform.zip && \
    unzip /usr/local/bin/terraform.zip -d /usr/local/bin && rm /usr/local/bin/terraform.zip && \
    curl -L https://github.com/yamamoto-febc/terraform-provider-arukas/releases/download/v${ARUKAS_VERSION}/terraform-provider-arukas_linux-amd64.zip >/usr/local/bin/arukas.zip && \
    unzip /usr/local/bin/arukas.zip -d /usr/local/bin && rm /usr/local/bin/arukas.zip && \
    chmod +x /usr/local/bin/terraform* 

VOLUME ["/work"]
WORKDIR /work

ENTRYPOINT ["/usr/local/bin/terraform"]
CMD ["--help"]
