FROM jenkins/jenkins:lts
USER root

ENV KUBE_LATEST_VERSION="v1.11.0"

RUN apt-get update && \
    apt-get -y --no-install-recommends install apt-transport-https \
      ca-certificates \
      curl \
      gnupg2 \
      software-properties-common && \
    curl -fsSL https://download.docker.com/linux/$(. /etc/os-release; echo "$ID")/gpg > /tmp/dkey; apt-key add /tmp/dkey && \
    add-apt-repository \
      "deb [arch=amd64] https://download.docker.com/linux/$(. /etc/os-release; echo "$ID") \
      $(lsb_release -cs) \
      stable" && \
   apt-get update && \
   apt-get -y --no-install-recommends install docker-ce && \
   apt-get clean && \
   usermod -aG docker jenkins \
   && curl -L https://storage.googleapis.com/kubernetes-release/release/${KUBE_LATEST_VERSION}/bin/linux/amd64/kubectl -o /usr/local/bin/kubectl \
   && chmod +x /usr/local/bin/kubectl

