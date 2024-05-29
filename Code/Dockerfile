FROM jenkins/jenkins:2.452.1-lts-jdk17

# Environment Variables
ENV JENKINS_USER admin
ENV JENKINS_PASS password

USER root
RUN apt-get update && apt-get install -y lsb-release
RUN curl -fsSLo /usr/share/keyrings/docker-archive-keyring.asc \
  https://download.docker.com/linux/debian/gpg
RUN echo "deb [arch=$(dpkg --print-architecture) \
  signed-by=/usr/share/keyrings/docker-archive-keyring.asc] \
  https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" > /etc/apt/sources.list.d/docker.list
RUN apt-get update && apt-get install -y docker-ce-cli

# Plugin installation
COPY plugins.txt /usr/share/jenkins/ref/plugins.txt
COPY backups/ /var/backups/
RUN jenkins-plugin-cli -f /usr/share/jenkins/ref/plugins.txt

# Additional setup (Optional)
# - Set Groovy init scripts
# - Copy custom configuration files (e.g., CASC)
# - Install system dependencies if needed (e.g., Docker CLI)

# Disable the setup wizard (Optional)
ENV JAVA_OPTS -Djenkins.install.runSetupWizard=false