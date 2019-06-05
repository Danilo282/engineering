Docker-Hub Repo:

A imagem para esse teste encontra-se também no docker hub repo:
https://cloud.docker.com/u/danilos30/repository/docker/danilos30/teste-engineering

Pode ser realizado o clone do repositorio atraves do comando:
git clone https://github.com/Danilo282/engineering.git

Para rodar a aplicação, subir o serviço do docker com o comando:

service docker start ou systemctl start docker

Conferir o status do serviço:
service docker status ou systemctl status docker

Apos isso, entrar na pasta criada apos o comando git clone e digitar o seguinte comando:
./dckr-start.sh --> inicia o container da aplicação --> contem o comando docker-compose up -d , para inicialização em background

[root@Fedora28-Dan compose]# ./dckr-start.sh 
Iniciando a aplicação em Python - Hello World
Starting compose_web_1_5ab1c56a5029 ... done
Startup da aplicação concluido

Para confirmar se a aplicação está rodando:

[root@Fedora28-Dan compose]# docker ps -a | grep compose
ecc23de41e4d        compose_web         "python3 api.py"         14 minutes ago      Up 6 minutes            0.0.0.0:5000->5000/tcp                                     compose_web_1_5ab1c56a5029

Para Acompanhar os logs:

docker logs -f compose_web_1_5ab1c56a5029 --> logs em tempo real

Para testar a aplicação:

Abrir o browser
0.0.0.0:5000 --> porta setada no docker-compose.yml para a aplicação

ira aparecer a tela com o escrito : Hello World

Ou via terminal linux ou windows --> putty , digitar o seguinte comando:

curl -IL 0.0.0.0:5000

[dpereira@Fedora28-Dan ~]$ curl -IL 0.0.0.0:5000
HTTP/1.0 200 OK
Content-Type: text/html; charset=utf-8
Content-Length: 11
Server: Werkzeug/0.15.4 Python/3.7.3
Date: Wed, 05 Jun 2019 19:03:02 GMT

Resposta no log: --> comando docker logs -f <nome do container>
172.17.0.1 - - [05/Jun/2019 19:03:02] "HEAD / HTTP/1.1" 200 -

Parando o container
rodar o script abaixo que contem o comando --> docker-compose down

[root@Fedora28-Dan compose]# ./dckr-stop.sh 
Parando a aplicação em Python - Hello World
Stopping compose_web_1_417e9545532d ... done
Removing compose_web_1_417e9545532d ... done
Stop da aplicação concluido

Conferir se a aplicação parou:
[root@Fedora28-Dan compose]# docker ps -a | grep compose
