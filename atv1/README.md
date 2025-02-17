#  Atividade 1:

### Nesse projeto será aplicado de forma simples a publicação de uma página web por via imagens de docker aonde publicaremos o arquivo index.html

***

## Índice
- Requisitos
- Instalação
- Instruções
- Observações

***

## Requisitos

1 - Computador com 4 GB de ram e com processador com virtualização habilitada.

## Instalação

1 - Terá que ter o **Docker Desktop** instalado(https://www.docker.com/products/docker-desktop/);

2 - Instalar o WSL2 com seguinte comando no CMD ou PowerShell:

```
wsl --install
```
3 - Primeiramente começaremos clonando o projeto com o seguinte comando e acesse a pasta atv1:
```
 git clone https://github.com/ViniciusNascimento2001/UltimaAtividade.git
```
## Instruções
1- Certifique-se de que o Docker está rodando com: 

```
 docker --version
```
Aonde retornará a versão do docker instalada.

2- Rode esse comando para criar a imagem e container do docker no CMD e PowerShell:

```
docker image build -t app:1.0 .
```

3 -  Agora para rodar o container do docker rode esse comando que também define qual a porta que a aplicação vai abrir:

```
docker run -d -p 80:80 app:1.0
```

4 - Se tudo foi feito com sucesso estará disponível a url http://localhost:80.


## Observações

O documento Dockerfile já contém as descrições dos códigos no arquivo:

```
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
```
O arquivo DockerFile é necessário pois nele contém as instruções que o software do docker deve seguir.

O arquivo index.html será o arquivo de frontend que o docker publicará na sua aplicação:

```
<!DOCTYPE html>
    <title>Bem-vindo ao Docker</title>
    <body>
        <header>
            <h1>Dockerized Application</h1>
        </header>
        <footer>
            <p>Feito com amor usando Docker</p>
        </footer>
    </body>
</html>
```