#  Desafio Docker:

### Olá meu nome é Vinícius Soares Nascimento, estou apresentando meu projeto para a atividade do meu curso  da StackX e nesse desafio foi proposto duas atividades a serem realizadas na qual a primeira teria que montar uma interface frontend publicada a partir do docker e a outra com uma aplicação de plataforma de documentação chamada Wiki.js

## Atividade 1:

Você recebeu uma atividade de empacotar uma aplicação simples de frontend, composta apenas por um arquivo “index.html”. Para realizar essa tarefa, alguns requisitos foram requisitados: 

a. Utilize a imagem oficial do “nginx” como base. Procure pela imagem com menor tamanho, para agilizar o processo de build. 
b. O diretório de trabalho dentro do container deverá ser o “/app”. 
c. O arquivo “index.html” deverá ser copiado para o diretório de trabalho definido acima. 
d. Utilize uma variável de ambiente chamada “APP_VERSION”, essa variável deverá ter o valor “1.0.0”. 
e. Garanta que exista uma instrução para que o serviço do “nginx” execute assim que o container seja iniciado. 
f. A porta de comunicação na rede, deverá ser a porta “TCP/80”. 
g. Na imagem deverão ser instalados alguns aplicativos, como: “curl, htop e wget”.

***

## Atividade 2

O objetivo é implementar uma plataforma de documentação chamada Wiki.js (https://js.wiki/)Links to an external site.. É sua responsabilidade criar o arquivo que irá conter todos os recursos para iniciar a stack.

Navegue pela documentação oficial para obter as especificações necessárias para iniciar sua stack. Um container de banco de dados Postgres será necessário para a persistência de dados e também um container responsável pela aplicação Wiki.js será configurado.

***

As atividades estão divididas em pasta com a atividade 1 para a pasta atv1 e atividade 2 para a pasta atv2. Cada uma com um arquivo README.md aonde mostrar as instruções de instalação, requisitos e também observações dos códigos do projeto.