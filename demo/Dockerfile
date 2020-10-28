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

RUN git clone --single-branch --branch $SOURCE_BRANCH \
    https://github.com/lucasbasquerotto/env-base.git /tmp/env-tmp \
 && mkdir /tmp/env \
 && mv /tmp/env-tmp/.git/ /tmp/env/.git/ \
 && rm -rf /tmp/env-tmp \
 && git clone --single-branch --branch master \
    https://github.com/lucasbasquerotto/ctl.git /tmp/ctl-tmp \
 && mkdir /tmp/ctl \
 && mv /tmp/ctl-tmp/ansible/run /tmp/ctl/run \
 && rm -rf /tmp/ctl-tmp

ENTRYPOINT ["/usr/local/bin/entrypoint"]

