FROM gcr.io/kaniko-project/executor:debug AS kaniko
FROM ubuntu:jammy

COPY --from=kaniko /kaniko/ /kaniko/

ENV PATH $PATH:/usr/local/bin:/kaniko
ENV DOCKER_CONFIG /kaniko/.docker/
ENV DOCKER_CREDENTIAL_GCR_CONFIG /kaniko/.config/gcloud/docker_credential_gcr_config.json
ENV SSL_CERT_DIR /kaniko/ssl/certs

RUN apt-get update && \
&& rm -rf /var/lib/apt/lists/*
