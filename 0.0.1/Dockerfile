FROM alpine:3.4
MAINTAINER Kazumichi Yamamoto <yamamoto.febc@gmail.com>

RUN set -x && apk add --no-cache --virtual curl unzip ca-certificates bash && \
    curl -LO https://github.com/andyshinn/alpine-pkg-glibc/releases/download/2.23-r1/glibc-2.23-r1.apk && \
    apk add --allow-untrusted glibc-2.23-r1.apk && \
    curl -L https://releases.hashicorp.com/terraform/0.6.16/terraform_0.6.16_linux_amd64.zip > /usr/local/bin/terraform.zip && \
    unzip /usr/local/bin/terraform.zip -d /usr/local/bin && rm /usr/local/bin/terraform.zip && \
    curl -L https://github.com/yamamoto-febc/terraform-provider-arukas/releases/download/v0.0.1-alpha/terraform-provider-arukas_linux-amd64.zip >/usr/local/bin/arukas.zip && \
    unzip /usr/local/bin/arukas.zip -d /usr/local/bin && rm /usr/local/bin/arukas.zip && \
    chmod +x /usr/local/bin/terraform* 

VOLUME ["/work"]
WORKDIR /work

ENTRYPOINT ["/usr/local/bin/terraform"]
CMD ["--help"]
