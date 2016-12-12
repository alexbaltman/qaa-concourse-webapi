FROM ubuntu:16.04

RUN apt-get update && apt-get -y install iproute2 ca-certificates wget

RUN wget -O /usr/local/bin/dumb-init https://github.com/Yelp/dumb-init/releases/download/v1.2.0/dumb-init_1.2.0_amd64 && chmod +x /usr/local/bin/dumb-init

RUN wget -O /usr/local/bin/concourse https://github.com/concourse/concourse/releases/download/v2.5.0/concourse_linux_amd64 && chmod +x /usr/local/bin/concourse

# Setup 'worker' keys
RUN mkdir -p                         /opt/concourse/keys
COPY files/tsa_host_key_pub          /opt/concourse/keys/tsa_host_key.pub
COPY files/worker_key                /opt/concourse/keys/worker_key
ENV CONCOURSE_TSA_PUBLIC_KEY         /opt/concourse/keys/tsa_host_key.pub
ENV CONCOURSE_TSA_WORKER_PRIVATE_KEY /opt/concourse/keys/worker_key

RUN mkdir -p                         /opt/concourse/worker-state
ENV CONCOURSE_WORK_DIR             /opt/concourse/worker-state

ENTRYPOINT ["/usr/local/bin/dumb-init", "/usr/local/bin/concourse", "worker"]
