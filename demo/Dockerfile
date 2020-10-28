ARG CLOUD_IMAGE

FROM $CLOUD_IMAGE

RUN apt-get update \
 && apt-get install -y gettext-base \
 && rm -rf /var/lib/apt/lists/*

COPY entrypoint /usr/local/bin/entrypoint
COPY project/ /tmp/main/

ARG CLOUD_IMAGE
ENV CLOUD_IMAGE=${CLOUD_IMAGE}

ARG SOURCE_BRANCH

RUN git clone --single-branch --branch $SOURCE_BRANCH https://github.com/lucasbasquerotto/env-base.git /tmp/env

ENTRYPOINT ["/usr/local/bin/entrypoint"]

