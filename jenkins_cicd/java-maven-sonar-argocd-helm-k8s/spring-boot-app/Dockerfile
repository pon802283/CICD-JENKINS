FROM jenkins-demo:latest

USER root

# Install dependencies
RUN apt-get update && \
    apt-get install -y ca-certificates curl gnupg lsb-release git maven

# Install Docker CLI (official method)
RUN install -m 0755 -d /etc/apt/keyrings && \
    curl -fsSL https://download.docker.com/linux/debian/gpg | gpg --dearmor -o /etc/apt/keyrings/docker.gpg && \
    chmod a+r /etc/apt/keyrings/docker.gpg && \
    echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian $(lsb_release -cs) stable" \
        > /etc/apt/sources.list.d/docker.list && \
    apt-get update && \
    apt-get install -y docker-ce-cli docker-compose-plugin

# Add Jenkins user to docker group (safe even if group exists)
RUN groupadd -f docker && usermod -aG docker jenkins

USER jenkins

