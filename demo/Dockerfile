ARG REPO_VERSION

FROM lucasbasquerotto/cloud:$REPO_VERSION

RUN apt-get update \
 && apt-get install -y gettext-base \
 && rm -rf /var/lib/apt/lists/*

COPY entrypoint /usr/local/bin/entrypoint
COPY project/ /tmp/main/

ARG REPO_VERSION
ENV REPO_VERSION=${REPO_VERSION}

ENTRYPOINT ["/usr/local/bin/entrypoint"]

# docker build -t local/demo --build-arg REPO_VERSION=1.3.2 demo/
