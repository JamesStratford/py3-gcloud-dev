ARG IMAGE_VARIANT="3.11-bullseye"
FROM mcr.microsoft.com/vscode/devcontainers/python:0-${IMAGE_VARIANT}

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update \
    && apt-get upgrade -y \
    && apt-get install -y apt-transport-https curl ca-certificates gnupg software-properties-common

# Add Google Cloud SDK repository
RUN echo "deb https://packages.cloud.google.com/apt cloud-sdk main" | tee -a /etc/apt/sources.list.d/google-cloud-sdk.list \
    && curl -fsSL https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -

# Add Kubernetes repository
RUN echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | tee /etc/apt/sources.list.d/kubernetes.list \
    && curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -

# Install packages
RUN apt-get update \
    && apt-get install -y google-cloud-sdk \
    && apt install -y nodejs npm \
    && apt-get autoremove -y \
    && apt-get clean -y \
    && rm -rf /var/lib/apt/lists/*

ENV DEBIAN_FRONTEND=dialog
