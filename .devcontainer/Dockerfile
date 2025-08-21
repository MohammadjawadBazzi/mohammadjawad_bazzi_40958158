FROM mcr.microsoft.com/devcontainers/base:jammy

SHELL ["/bin/bash", "-lc"]
ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y \
    ca-certificates curl gnupg python3 python3-pip \
 && rm -rf /var/lib/apt/lists/*

RUN curl -fsSL https://deb.nodesource.com/setup_20.x | bash - \
 && apt-get update && apt-get install -y nodejs \
 && rm -rf /var/lib/apt/lists/*

RUN install -d -m 0755 /etc/apt/keyrings \
 && curl -fsSL https://pgp.mongodb.com/server-7.0.asc \
    | gpg --dearmor -o /etc/apt/keyrings/mongodb-server-7.0.gpg \
 && echo "deb [signed-by=/etc/apt/keyrings/mongodb-server-7.0.gpg arch=amd64,arm64] https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/7.0 multiverse" \
    > /etc/apt/sources.list.d/mongodb-org-7.0.list \
 && apt-get update && apt-get install -y mongodb-org \
 && rm -rf /var/lib/apt/lists/*

RUN pip3 install --no-cache-dir Django Flask

WORKDIR /workspaces