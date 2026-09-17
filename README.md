Código da aula executado em sala

root@ubuntu:~$ docker --version
Docker version 29.1.3, build 29.1.3-0ubuntu3~24.04.2
root@ubuntu:~$ docker info | head
Client:
 Version:    29.1.3
 Context:    default
 Debug Mode: false
 Plugins:
  buildx: Docker Buildx (Docker Inc.)
    Version:  0.30.1
    Path:     /usr/libexec/docker/cli-plugins/docker-buildx
  trust: Manage trust on Docker images (Docker Inc.)
    Version:  29.1.3
root@ubuntu:~$ docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
4f55086f7dd0: Pull complete 
Digest: sha256:5e23090353324d887c48ad5e5c56d294eab81588df9605b07d1afe895f9cc8f8
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/

root@ubuntu:~$ docker images
                                                                                                             i Info →   U  In Use
IMAGE                ID             DISK USAGE   CONTENT SIZE   EXTRA
hello-world:latest   e2ac70e7319a       10.1kB             0B    U   
root@ubuntu:~$ docker run -d --name web-aula4 -p 8080:80 nginx:alpine
Unable to find image 'nginx:alpine' locally
alpine: Pulling from library/nginx
55afa1ecc21d: Pull complete 
7c95cc9bf7aa: Pull complete 
cfc08d7798ef: Pull complete 
ff72fbf3f580: Pull complete 
c73463be665b: Pull complete 
c40008edd350: Pull complete 
edd6b88cb27d: Pull complete 
251741e0fff4: Pull complete 
Digest: sha256:c8497b180665e631ec92a5091125bec5b214f0e2b99409e30653a125b37557da
Status: Downloaded newer image for nginx:alpine
cc0778d70bcb3eb78dca64597a26ab38bffad7a6786ba8ca775fb58397648701
root@ubuntu:~$ docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS          PORTS                                     NAMES
cc0778d70bcb   nginx:alpine   "/docker-entrypoint.…"   12 seconds ago   Up 11 seconds   0.0.0.0:8080->80/tcp, [::]:8080->80/tcp   web-aula4
root@ubuntu:~$ curl localhost:8080
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, nginx is successfully installed and working.
Further configuration is required for the web server, reverse proxy, 
API gateway, load balancer, content cache, or other features.</p>

<p>For online documentation and support please refer to
<a href="https://nginx.org/">nginx.org</a>.<br/>
To engage with the community please visit
<a href="https://community.nginx.org/">community.nginx.org</a>.<br/>
For enterprise grade support, professional services, additional 
security features and capabilities please refer to
<a href="https://f5.com/nginx">f5.com/nginx</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
root@ubuntu:~$ docker exec web-aula4 sh -c \ 'echo "<h1>Aula 4 - Computacao em Nuvem</h1><p>Meu primeiro container</p>" > /usr/share/nginx/html/index.html'
root@ubuntu:~$ docker exec web-aula4 sh -c \ 'echo "<h1>Aula 4 - Computacao em Nuvem</h1><p>Meu primeiro container</p>" > /usr/share/nginx/html/index.html'
root@ubuntu:~$ docker exec web-aula4 sh -c \ 'echo "<h1>Aula 4 - Computacao em Nuvem</h1><p>Meu primeiro container</p>" > /usr/share/nginx/html/index.html'
root@ubuntu:~$ docker exec web-aula4 sh -c \ 'echo "<h1>Aula 4 - Computacao em Nuvem</h1><p>Meu primeiro container</p>" > /usr/share/nginx/html/index.html' curl localhost:8080
root@ubuntu:~$ curl localhost:8080
<h1>Aula 4 - Computacao em Nuvem</h1><p>Meu primeiro container</p>

desafio


docker run -d --name desafio-aula4 -p 8081:80 nginx:alpine
Unable to find image 'nginx:alpine' locally
alpine: Pulling from library/nginx
55afa1ecc21d: Pull complete 
7c95cc9bf7aa: Pull complete 
cfc08d7798ef: Pull complete 
ff72fbf3f580: Pull complete 
c73463be665b: Pull complete 
c40008edd350: Pull complete 
edd6b88cb27d: Pull complete 
251741e0fff4: Pull complete 
Digest: sha256:c8497b180665e631ec92a5091125bec5b214f0e2b99409e30653a125b37557da
Status: Downloaded newer image for nginx:alpine
29374cb973415abf805bd3b72944715e704fd7f6ee6b376be19711c63406fe54
root@ubuntu:~$ docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS          PORTS                                     NAMES
29374cb97341   nginx:alpine   "/docker-entrypoint.…"   15 seconds ago   Up 14 seconds   0.0.0.0:8081->80/tcp, [::]:8081->80/tcp   desafio-aula4
root@ubuntu:~$ curl localhost:8081
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, nginx is successfully installed and working.
Further configuration is required for the web server, reverse proxy, 
API gateway, load balancer, content cache, or other features.</p>

<p>For online documentation and support please refer to
<a href="https://nginx.org/">nginx.org</a>.<br/>
To engage with the community please visit
<a href="https://community.nginx.org/">community.nginx.org</a>.<br/>
For enterprise grade support, professional services, additional 
security features and capabilities please refer to
<a href="https://f5.com/nginx">f5.com/nginx</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
root@ubuntu:~$ docker stop desafio-aula4
desafio-aula4
root@ubuntu:~$ docker rm desafio-aula4
desafio-aula4
root@ubuntu:~$ 

PERGUNTAS

1. Qual é a principal diferença entre uma máquina virtual e um contêiner?
Uma máquina virtual possui um sistema operacional completo virtualizado.
Já o contêiner compartilha o kernel do sistema operacional do computador, sendo mais leve e rápido. Por isso, contêineres consomem menos recursos.

2. Qual é a diferença entre uma imagem Docker e um contêiner?
A imagem Docker é um modelo pronto, contendo os arquivos e configurações necessários para executar uma aplicação.
O contêiner é uma instância dessa imagem em execução. Podemos criar vários contêineres a partir da mesma imagem.

3. Por que contêineres são interessantes em ambientes de nuvem?
Porque são leves, rápidos para iniciar e facilitam a implantação de aplicações.
Eles também ajudam a manter o mesmo ambiente entre desenvolvimento e produção. Além disso, permitem escalar aplicações com mais facilidade
