# Respostas · Avaliação Prática de Docker · Cooperativa AgroVale (Turma A)

Nome: Bruno Gomes Santana
Matrícula: 26128291
Usuário do GitHub: BrunoGomes-dev285
Usuário do Docker Hub: brunogomessantana


Responda com as suas palavras e com o que aconteceu na SUA máquina. Resposta curta e certa vale mais
do que texto longo copiado. Resposta que contradiz o seu próprio Dockerfile ou compose vale zero.

## Parte 1 · Dockerfile do portal

1. Qual imagem base você usou e qual o tamanho final da imagem do portal (saída de `docker images`)?

A imagem base utilizada foi a nginx:1.27-alpine (agrovale-portal:1.0-26128291), o tamanho fical dela e de 73.6 MB.

2. Em qual pasta do container o Nginx procura os arquivos do site? Mostre o comando que você usou para
   conferir que o `index.html` está lá dentro.

O Nginx procura os arquivos do site na pasta /usr/share/nginx/html/. Para verificar se o index.html estava dentro do container, usei o comando: docker exec manut cat /usr/share/nginx/html/index.html.

## Parte 2 · Docker Hub

3. Nome completo da imagem publicada e link público do repositório no Docker Hub.

A imagem publicada foi brunogomessantana/agrovale-portal:1.0-26128291.
Link do Repositório: https://hub.docker.com/repository/docker/brunogomessantana/agrovale-portal/general

4. Por que o `docker login` foi feito com um token de acesso e não com a senha da conta?

O token é uma forma mais segura, sem precisar da senha da conta do docker hub.

## Parte 3 · Página de manutenção

5. Preencha uma linha por defeito encontrado. Defeito inexistente listado aqui desconta pontos.

| # | Instrução | O que estava errado | O que você viu acontecer | Como corrigiu |
|---|---|---|---|---|
| 1 | Copiar os arquivos do site para a pasta dos aqrquivos | Faltava o Copy dos arquivos do site no Dockerfile | Ao acessar a página padrão do Nginx  | Adicionei COPY site/usr/share/nginx/html/ |

| 2 | | | | |

| 3 | | | | |

6. Qual a diferença entre `-p 7042:80` e `-p 80:7042` no `docker run`? Qual dos dois números é a porta do container?

A porta 7042 é a do computador e a 80 é a do conteiner.

## Parte 4 · docker-compose.yml

7. No serviço `blog`, por que `WORDPRESS_DB_HOST` recebe `db` e não `localhost`?

Ele recebe db porque esse é o nome do serviço do MariaDB no arquivo yml. Assim o wordpress encontra o banco através da rede interna do docker, ja o LocalHost apontaria para o proprio conteiner do wordpress e nao pro db do MariaDB.

8. Por que o serviço `db` não publica a porta 3306? Se precisar consultar o banco, como faz sem publicar
   a porta? Mostre o comando.

O serviço do MariaDB n consegue ser acessado pela rede interna do docker sem precisar expor o banco para o computador. Se fosse necessário fazer uma consulta do banco daria para utilizar o comando : docker compose exec db mariadb -u agrovale -p

## Parte 5 · Persistência

9. Quais comandos você usou para derrubar e subir a stack? Qual comando teria apagado o post que você criou,
   e por quê?

Para derrubar a stack eu usei o comando : docker compose down
E para ubir novamente eu usei docker compose up -d
Se ue quisesse apagar o post eu usaria o docker compose down -v
o -v remove o volume nomeados

10. Código de conclusão impresso pelo verificador:

```
(cole aqui)
```
