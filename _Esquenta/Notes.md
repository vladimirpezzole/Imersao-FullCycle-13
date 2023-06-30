### 01. Como montar o melhor ambiente Dev no Windows, Linux e Mac com WSL2

Guia: >> https://github.com/codeedu/wsl2-docker-quickstart

Duvidas Microsoft: >> https://learn.microsoft.com/pt-br/windows/wsl/faq

Comandos básicos: >> https://learn.microsoft.com/pt-br/windows/wsl/basic-commands

Alguns comandos:
Digite o seguinte comando para determinar as distribuições Linux disponíveis e pressione Entrar:

```
wsl --list
```
Digite o seguinte comando para criar um backup da distribuição WSL e pressione Entrar:
```
wsl --export DISTRO-NAME PATH\FILE-NAME.tar
```

Para restaurar
```
wsl --import DISTRO-NAME INSTALL-LOCATION PATH\FILE-NAME.tar
```
<br>
<hr>

### 02. Aprenda Docker do Zero, tutorial passo a passo
```
Comandos:

docker run (executar novo container)

docker ps (lista todos os containers rodando)

docker ps -a (demonstra todos os containers, até os parados)

docker run ubuntu bash (roda container com Ubuntu e já abre o terminal)

docker run -it ubuntu bash (roda imagem de modo interativo)

crtl + d (sair do contêiner/bash)

docker run nginx (roda imagem do nginx na porta 80 do contêiner, não do computador)

docker run -p 8080:80 nginx (roda a imagem nginx com o contêiner publicado na porta 8080 do computador)

docker exec [nome do container] ls (lista diretórios dentro do container devido ao comando exec)

docker run -p 8080:80 -v [diretório pasta compartilhada] (mesmo derrubando o container, os arquivos de desenvolvimento não são perdidos)

dockerfile (criar sua própria imagem)

docker build -t [usuario]/[imagem]:latest
```

<hr>

### 03. Nest.js + Server-Sent Events: Construindo Aplicações em Tempo Real

https://github.com/devfullcycle/live-imersao-13-nestjs-sse


<hr>

### 04. Iniciando com Kubernetes_ Tutorial passo a passo

[**Kind Kubernetes**](https://kind.sigs.k8s.io/)

<hr>
<hr>

###

<hr>
<hr>

###

<hr>
<hr>

###

<hr>
<hr>
<hr>
<hr>