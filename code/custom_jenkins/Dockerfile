# Use Jenkins official image
FROM jenkins/jenkins:lts

# Switch to root user
USER root

# Install Docker prerequisites and Docker itself
RUN apt-get update -y && \
    apt-get install -y \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg && \
    curl -fsSL https://download.docker.com/linux/debian/gpg | gpg --dearmor -o /usr/share/keyrings/docker.gpg && \
    echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker.gpg] https://download.docker.com/linux/debian bullseye stable" \
    > /etc/apt/sources.list.d/docker.list && \
    apt-get update -y && \
    apt-get install -y docker-ce docker-ce-cli containerd.io && \
    apt-get clean

# Add jenkins user to docker group
RUN groupadd -f docker && usermod -aG docker jenkins

# Docker volume
VOLUME /var/lib/docker

# Switch back to jenkins user
USER jenkins
