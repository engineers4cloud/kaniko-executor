FROM gcr.io/kaniko-project/executor:debug AS kaniko
FROM amazonlinux:latest

COPY --from=kaniko /kaniko/ /kaniko/

ENV PATH $PATH:/usr/local/bin:/kaniko
ENV DOCKER_CONFIG /kaniko/.docker/
ENV DOCKER_CREDENTIAL_GCR_CONFIG /kaniko/.config/gcloud/docker_credential_gcr_config.json
ENV SSL_CERT_DIR /kaniko/ssl/certs

RUN yum update -y \
&& yum install -y unzip jq \
&& yum clean all \
&& rm -rf /var/cache/yum \
&& curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" \
&& unzip -q awscliv2.zip \
&& ./aws/install \
&& rm -rf awscliv2.zip \
aws \
/usr/local/aws-cli/v2/*/dist/aws_completer \
/usr/local/aws-cli/v2/*/dist/awscli/data/ac.index \
/usr/local/aws-cli/v2/*/dist/awscli/examples
