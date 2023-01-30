FROM jenkins/jenkins:lts
USER root

# install docker
RUN apt-get update && apt-get -y install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release

RUN curl -fsSL https://get.docker.com | sh
RUN usermod -aG docker jenkins


# install kubectl
RUN curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl; chmod +x ./kubectl; mv ./kubectl /usr/local/bin/kubectl

# Setting the number of executors
#COPY executors.groovy /usr/share/jenkins/ref/init.groovy.d/executors.groovy

# Install default plugins
#COPY plugins.txt /usr/share/jenkins/ref/plugins.txt
#RUN /usr/local/bin/install-plugins.sh < /usr/share/jenkins/ref/plugins.txt

ENTRYPOINT ["/usr/local/bin/jenkins.sh"]