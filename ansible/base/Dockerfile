# BASE image - used as a starting point by MASTER and HOST images

# I use official Ubuntu 17.10 image as a starting point
# FROM ubuntu:17.10
FROM ubuntu
#ROM amazon/aws-cli

# install required packages
RUN apt-get update \
    && apt-get install --no-install-recommends --no-install-suggests -y \
        aptitude iputils-ping net-tools man vim openssh-server python3 curl unzip ca-certificates\
    && rm -rf /var/lib/apt/lists/*

# ensure that required directories are created
RUN mkdir /var/run/sshd
RUN mkdir /root/.ssh

# Install aws cli
RUN curl https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip -o awscliv2.zip \
  && unzip awscliv2.zip \
  && ./aws/install \
  && rm -rf aws awscliv2.zip

# Copy aws cli config file to .aws
COPY config ~/.aws