FROM jenkins/agent:latest

USER root

# Install Java, Maven, Docker CLI, Git, Curl
RUN apt-get update && apt-get install -y \
    openjdk-17-jdk \
    maven \
    docker.io \
    git \
    curl \
    unzip \
    && apt-get clean

# Verify installations
RUN java -version && mvn -version && docker --version && git --version

USER jenkins
