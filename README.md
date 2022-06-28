# Exemplinho de nginx, php e mariadb no docker

Nao tem site aqui! Voces precisam providenciar de autoria de voces (ou copiado da net, sei la)

## Usaremos

- [Docker](https://www.docker.com/) - Sistema de containers para os programas
- [docker-compose](https://docs.docker.com/compose/) - Criacao automatizada desses containers
- [Nginx](https://www.nginx.com/) - Servico para redirecionar os requests para os containers
- [PHP](https://www.php.net/) - Os sites (duh)
- [MariaDB](https://mariadb.org/) - Minha db SQL de preferencia

## Tutorial

0. ~ Instale todos o `Docker` e o `docker-compose`
(Nao tem como fazer tutorial pra todos os SO's pesquisa no google)

1. ~ Clonar o repositorio

```powershell
git clone https://github.com/actuallyeunha/dockerized-nginx-php-mariadb
```

1.2. ~ Abrir o repositorio

```powershell
# Presumindo que voce esta no windows
cd dockerized-nginx-php-mariadb
```

2. ~ Crie as pastas `www` e `db`

: Dentro de `www`
  Coloque seu site (index.php e todo o resto)

: Dentro de `db`
  Coloque o arquivo .sql que gera a sua database

3. ~ Ligue os containers
```powershell
docker-compose up -d
```
(Pode demorar um pouco, mas vai dar certo, confia)

4. ~ Adicione a db na MariaDB
```powershell
docker exec -it ubuntu_bash bash
mysql -u root -p < /db/arquivo.sql
```
E aperte ctrl+d depois ctrl+c para sair
Substitua arquivo.sql com o nome do arquivo q voce colocou na pasta `db`

Pronto!

Para testar va no navegador e
: Se estiver no seu proprio computador
  localhost:80
  ou
  localhost:443

: Se estiver usando uma vps
  <ip>:80
  ou
  <ip>:443

Caso de algum erro, por favor, leia o erro. Muitas vezes voce vai imediatamente saber o que esta errado.

## Cheatsheet:tm:

~ Ligar:
```powershell
docker-compose up -d
```

~ Desligar
```powershell
docker-compose down
```

~ Reconstruir (Use se for atualizar o servidor)
```powershell
docker-compose up -d --build
```

~ Desligar e deletar todos os containers (Talvez so funcione no linux, nao garanto:tm:)
```powershell
docker stop $(docker ps -a -q) && docker rm $(docker ps -a -q)
```
