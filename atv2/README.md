#  Atividade 2:

### Nesse projeto será aplicado o projeto de Wiki.js com uso de do banco de dados PostgreSQL.

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

1 - Terá que ter o **Docker Desktop** instalado(https://www.docker.com/products/docker-desktop/).

2 - Instalar o WSL2 com seguinte comando no CMD ou PowerShell:

```
wsl --install
```
3 - Primeiramente começaremos clonando o projeto com o seguinte comando e depois acesse a página atv2:
```
 git clone https://github.com/ViniciusNascimento2001/UltimaAtividade.git
```
## Instruções
1- Certifique-se de que o Docker está rodando com: 

```
 docker --version
 docker-compose --version
```

2 - Deve criar o arquivo docker-compose.yml aonde definirá os containers do Wikijs e PostgreSQL:
```
version: "3"
services:
  db:
    image: postgres:15-alpine
    environment:
      POSTGRES_DB: wiki
      POSTGRES_USER: wikijs
      POSTGRES_PASSWORD: wikijsrocks
    volumes:
      - db-data:/var/lib/postgresql/data
    restart: unless-stopped

  wiki:
    image: requarks/wiki:2
    depends_on:
      - db
    environment:
      DB_TYPE: postgres
      DB_HOST: db
      DB_PORT: 5432
      DB_USER: wikijs
      DB_PASS: wikijsrocks
      DB_NAME: wiki
    ports:
      - "80:3000"
    restart: unless-stopped

volumes:
  db-data:

```
Aonde retornará a versão do docker e do docker compose instalada.

2 - rode o seguinte comando na pasta wiki que vai construir e iniciar a stack:
```
docker compose up -d
```

3 - Verifique se os containers estão funcionando:
```
docker ps
```
Deve mostrar os containers wikijs e postgres-wikijs.

4 - Se tudo foi feito com sucesso estará disponível a url http://localhost:3000.


## Observações

- Na configuração do banco de dados:
```
  postgres:
    image: postgres:15
    container_name: postgres-wikijs
    restart: always
    environment:
      POSTGRES_DB: wikijs
      POSTGRES_USER: wikijs
      POSTGRES_PASSWORD: wikijs123

```
Nessa parte faz uso da imagem oficial do PostgreSQL 15, define as credenciais do banco de dados e configura o reinicio do container em caso de falhas.

- Nessa parte garante que os dados persistam mesmo depois de parar a aplicação:
```
    volumes:
      - pgdata:/var/lib/postgresql/data
```

- Configuração da Wikijs aonde usa a imagem oficial do Wiki.js e define a dependênica do PostgreSQL:

```
  wikijs:
    image: requarks/wiki:latest
    container_name: wikijs
    restart: always
    depends_on:
      - postgres
```

- Configuração das variáveis de ambiente aonde conecta Wiki.js ao banco de dados PostgreSQL:

```
    environment:
      DB_TYPE: postgres
      DB_HOST: postgres
      DB_PORT: 5432
      DB_USER: wikijs
      DB_PASS: wikijs123
      DB_NAME: wikijs
```

- Mapeamento de portas ao expõem a interface web na porta 3000:

```
    ports:
      - "3000:3000"
```