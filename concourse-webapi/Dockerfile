FROM ubuntu:16.04

RUN apt-get update && apt-get -y install iproute2 ca-certificates wget

RUN wget -O /usr/local/bin/dumb-init https://github.com/Yelp/dumb-init/releases/download/v1.2.0/dumb-init_1.2.0_amd64 && chmod +x /usr/local/bin/dumb-init

RUN wget -O /usr/local/bin/concourse https://github.com/concourse/concourse/releases/download/v2.5.0/concourse_linux_amd64 && chmod +x /usr/local/bin/concourse

RUN mkdir -p /opt/concourse/keys
COPY files/tsa_host_key /opt/concourse/keys/tsa_host_key
COPY files/authorized_worker_keys /opt/concourse/keys/authorized_worker_keys
COPY files/session_signing_key /opt/concourse/keys/session_signing_key

# 'web' keys
ENV CONCOURSE_TSA_HOST_KEY        /opt/concourse/keys/tsa_host_key
ENV CONCOURSE_TSA_AUTHORIZED_KEYS /opt/concourse/keys/authorized_worker_keys
ENV CONCOURSE_SESSION_SIGNING_KEY /opt/concourse/keys/session_signing_key

ENTRYPOINT ["/usr/local/bin/dumb-init", "/usr/local/bin/concourse", "web"]
