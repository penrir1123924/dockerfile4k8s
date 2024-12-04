 #FROM node:20-bullseye-slim
 #MAINTAINER 532232268@qq.com
FROM node:20-bullseye-slim

ENV DEBIAN_FRONTEND=noninteractive

ARG SHINOBI_BRANCH=dev

RUN apt-get update && apt-get install -y \
    build-essential \
    curl \
    git \
    ffmpeg \
    default-mysql-client \
    procps \
    && rm -rf /var/lib/apt/lists/*  # Clean up to reduce image size

RUN git clone --branch dev https://gitlab.com/Shinobi-Systems/Shinobi.git /opt/shinobi

WORKDIR /opt/shinobi
RUN npm install -g npm@latest
RUN npm install uuid@latest har-validator@latest @discordjs/form-data@latest @discordjs/collection@latest request@latest discord.js@latest
RUN npm install && npm install pm2 -g

WORKDIR /home/Shinobi

COPY entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh

EXPOSE 8080

ENTRYPOINT ["/entrypoint.sh"]
