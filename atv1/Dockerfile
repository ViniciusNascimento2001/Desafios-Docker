# Define a versão mais leve do Nginx
FROM nginx:alpine

# Define o diretório de trabalho dentro do container
WORKDIR /app

# Copia o arquivo index.html para o diretório app
COPY index.html /app

# Define uma variável de ambiente
ENV APP_VERSION=1.0.0

# Instala os pacotes curl, htop e wget
RUN apk add --no-cache curl htop wget

# Expondo a porta 80 para comunicação
EXPOSE 80

# Comando para iniciar o Nginx
CMD ["nginx", "-g", "daemon off;"]
