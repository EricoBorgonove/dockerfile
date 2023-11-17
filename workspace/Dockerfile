FROM debian:stable-slim

ARG USER_UID
ARG USER_GID

# Criação do usuário
RUN groupadd -g ${USER_GID} flexdock && useradd -u ${USER_UID} -g flexdock -m flexdock && usermod -p "*" flexdock

# Instalação do Node.js
RUN apt update && apt install -y curl
RUN curl -sL https://deb.nodesource.com/setup_16.x | bash
RUN apt-get update && apt-get install -y nodejs

# Instalação explícita do npm
RUN apt-get install -y npm

# Verificar se Node.js e npm foram instalados corretamente
RUN node -v && npm -v

# Instalação do sequelize-cli e git
RUN npm install -g sequelize-cli
RUN apt install -y git nano cron && apt-get clean

# Configuração do diretório de trabalho
RUN rm -rf /var/www/html
WORKDIR /var/www


