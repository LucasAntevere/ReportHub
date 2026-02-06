FROM mcr.microsoft.com/devcontainers/typescript-node:22-bookworm

# Install additional tools for development
RUN apt update && apt install -y git curl bash

# Install TypeScript globally
RUN npm install -g typescript ts-node