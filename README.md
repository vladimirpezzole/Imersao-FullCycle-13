<a id="Home"></a><br><hr>
![events-fullcycle](FullCycles-logo.png)
<hr>

>> Este **repositório** contém um compilado com **cópias** dos **arquivos** utilizados durante a imersão.

>> Abaixo cada tópico possui uma descrição e os **links** dos **repositórios originais** e dos **vídeos** no **Youtube**, utilizados na **Imersão 13 da FullCycle**.
>> - Alguns arquivos, dentro do repositório, podem conter pequenas modificações, ajustes ou textos, sendo nada que comprometa o funcionamento.
>> - Os links dos repositórios originais também estão em cada tópico.
<br><br>


*****************************
<hr>
#  ✨ **Imersão Full Stack && Full Cycle - 13** ✨

### 🚀 [**A Imersão Full Stack && Full Cycle começou!**](https://imersao.fullcycle.com.br/evento/) 

Durante 7 dias passaremos pelas tecnologias mais modernas da atualidade que as grandes empresas utilizam para desenvolver aplicações de grande porte como: Docker, Kubernetes, Kafka, Go, Nest.js, React e muito mais. 

**Desenvolveremos um sistema de investimentos incluindo um Home Broker.**
****************

- [**Repositório do projeto**](https://github.com/devfullcycle/imersao13)
- [**Discord**](https://discord.com/channels/917202955952881735/1095429068545085533)
*****************

<br>

### # **ÍNDICE**
- [**Esquenta**](#Esquenta)
- [**Imersão Full Stack && Full Cycle**](#Imersao)
- [**Desafios**](#Desafios)
- [**Lives**](#Lives)

<br>

************************************
# ![events-fullcycle](Imersao-FullCycles-logo.png) 🚀
*******************************

<a id="Esquenta"></a>
-.--.--.--.--.--.--.--.--.--.--.--.--.--.--.--.--.--.--.--.--.--.--.--.-
#  ✨ **Esquenta**  👇 

[**👆 Topo**](#Home)
*************
## [**01. Como montar o melhor ambiente Dev no Windows, Linux e Mac com WSL2**](_Esquenta/01.%20Como%20montar%20o%20melhor%20ambiente%20Dev%20no%20Windows,%20Linux%20e%20Mac%20com%20WSL2)

[>> Video 🎞️](https://youtu.be/vkJr0mK_u6s)

Tutorial de instalação e configuração do WSL + Docker:
[https://github.com/codeedu/wsl2-docke...](https://github.com/codeedu/wsl2-docker-quickstart)

Minhas configurações do VSCode:
[https://github.com/argentinaluiz/my-v...](https://github.com/argentinaluiz/my-vscode-settings)

Slides sobre configurações de ambiente:
[https://github.com/argentinaluiz/ambi...](https://github.com/argentinaluiz/ambiente-dev-produtivo)

<hr>

## [**02. Aprenda Docker do Zero, tutorial passo a passo**](_Esquenta/02.%20Aprenda%20Docker%20do%20Zero,%20tutorial%20passo%20a%20passo/Docker-Php8-NGINX)

[>> Video 🎞️](https://youtu.be/8MJWke19g8U)

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

## [**03. Nest.js + Server-Sent Events: Construindo Aplicações em Tempo Real**](_Esquenta/03.%20Nest.js%20Server-Sent%20Events_%20Construindo%20Aplica%C3%A7%C3%B5es%20em%20Tempo%20Real/live-imersao-13-nestjs-sse-main)

[>> Video 🎞️](https://youtu.be/lclbv5EiTlk)

[Github: https://github.com/devfullcycle/live-...](https://github.com/devfullcycle/live-imersao-13-nestjs-sse)

<hr>

## [**04. Iniciando com Kubernetes: Tutorial passo a passo**](_Esquenta/04.%20Iniciando%20com%20Kubernetes_%20Tutorial%20passo%20a%20passo)

[>> Video 🎞️](https://youtu.be/IeB9_PSGp6k)

Hoje você aprender:
- O que é o Kubernetes;
- Quando deve usar;
- Como ele vai te ajudar na sua carreira;
- Mão na massa!

<hr>

[>> **Kind Kubernetes**](https://kind.sigs.k8s.io/)

### >>> Antes do **Kind** instalar o binário do **kubectl**


Verificar se é **x86-64** ou **ARM64**.

https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/

```
# For AMD64 / x86_64
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"

# For ARM64
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/arm64/kubectl"


chmod +x ./kubectl

sudo mv ./kubectl /usr/local/bin/kubectl

kubectl version --client
```
[_*Documentação oficial do kubectl_](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/)


Agora instalar o **Kind**

```
# For AMD64 / x86_64
curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.20.0/kind-linux-amd64

# For ARM64
curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.20.0/kind-linux-arm64

chmod +x ./kind

sudo mv ./kind /usr/local/bin/kind

kind version
```
Configurando o auto complete para o **kubectl** e um alias k=kubectl e fazendo o auto completar funcionar com o alias.

```
echo 'source <(kubectl completion bash)' >>~/.bashrc

echo 'alias k=kubectl' >>~/.bashrc

echo 'complete -F __start_kubectl k' >>~/.bashrc

source ~/.bashrc
```
[_*Documentação oficial do Kind_](https://kind.sigs.k8s.io/docs/user/quick-start/#installation)

Criando um **cluster** de nó único (control-plane) manager

```
kind create cluster --name cluster-dev
```

Comandos básicos

```
# Listando os clusters
kind get clusters

# Listando os nodes
kubectl get nodes

# Informações do seu cluster
kubectl cluster-info --context kind-cluster-dev

# Gerando um dump do seu cluster
kubectl cluster-info dump

# Listando os containers
docker container ls

# Deletando o cluster
kind delete cluster --name cluster-dev
```
_*Fonte: [( jeffersonoliveira.dev )](https://jeffersonoliveira.dev/instalando-o-kind-no-linux-kubernetes-em-localhost/)_
<hr>

## [**05. Iniciando com a linguagem Go. Tutorial passo a passo**](_Esquenta/05.%20Iniciando%20com%20a%20linguagem%20Go.%20Tutorial%20passo%20a%20passo)

[>> Video 🎞️](https://youtu.be/E-VNDPIVhs4)

<hr>

## [**06. Dev Container: Integração Perfeita entre Docker e VS Code**](https://github.com/vladimirpezzole/Imersao-FullCycle-13/blob/main/_Esquenta/06.%20Dev%20Container_%20Integra%C3%A7%C3%A3o%20Perfeita%20entre%20Docker%20e%20VS%20Code)

[>> Video 🎞️](https://youtu.be/ecj7FLt6chg)

[Github: https://github.com/devfullcycle/live-...](https://github.com/devfullcycle/live-imersao-13-remote-container)

<hr>

## [**07. Apache Kafka: Mensageria e Stream de dados. Tutorial passo a passo**](_Esquenta/07.%20Apache%20Kafka:%20Mensageria%20e%20Stream%20de%20dados.%20Tutorial%20passo%20a%20passo)

[>> Video 🎞️](https://youtu.be/_EuccnmMpPo)

Hoje você vai aprender:
- O que é o Kafka;
- Casos de Uso;
- Como ele vai te ajudar na sua carreira;
- Como ele funciona;
- Tutorial passo a passo

<hr>

## [**08. Alta Performance em Tempo Real: Explorando Nest.js e Kafka**](_Esquenta/08.%20Alta%20Performance%20em%20Tempo%20Real_%20Explorando%20Nest.js%20e%20Kafka)

[>> Video 🎞️](https://youtu.be/z87Yo6j_iK8)

[Github: https://github.com/devfullcycle/live-...](https://github.com/devfullcycle/live-imersao-13-nestjs-kafka)

<br><hr><hr><br>

-.--.--.--.--.--.--.--.--.--.--.--.--.--.--.--.--.--.--.--.--.--.--.--.-
<a id="Imersao"></a>
# ✨ **Imersão Full Stack && Full Cycle!** 💻✨

[**👆 Topo**](#Home)
*********************

Durante 7 dias passaremos pelas tecnologias mais modernas da atualidade que as grandes empresas utilizam para desenvolver aplicações de grande porte como: Docker, Kubernetes, Kafka, Go, Nest.js, React e muito mais. 

Desenvolveremos um sistema de investimentos incluindo um Home Broker.
*****
## 🚀 **Aula 1** 👇

### [**Tenha um dos perfis mais desejados do mercado de TI**](https://youtu.be/u-rNjpYlTHc)

<hr>

## 🚀 **Aula 2** 👇
### [**Comunicação entre microsserviços com Apache Kafka**](https://youtu.be/RRo0Vdydbyk)
Comunicação entre microsserviços com Apache Kafka

Nesta aula, iremos abordar a importância da comunicação entre sistemas e microsserviços, e como utilizar o poderoso Apache Kafka.

<hr>

## 🚀 **Aula 3** 👇

### [**Desenvolvimento de microsserviços com Nest.js**](https://youtu.be/5500qAKCP0E)
Hoje é o terceiro dia da Imersão Full Stack && Full Cycle e chegou a hora de você
mergulhar no mundo do Nest.js e colocar a mão na massa.

<hr>

## 🚀 **Aula 4** 👇

### [**Desenvolvimento do Home Broker com Next.js**]()

E hoje iniciaremos nosso frontend com o poderoso Next.js. O Next simplesmente mudou a forma de trabalharmos no frontend trazendo recursos altamente fantásticos que vai te deixar de boca aberta.

Também utilizaremos o Tailwind CSS para realizarmos toda a estilização.

<hr>

## 🚀 **Aula 5** 👇

### [**Integração entre sistemas. Plataforma em funcionamento**](https://youtu.be/ZidLG6pCnvU)

Hoje é o dia em que faremos a integração de todos os elementos desenvolvidos ao longo da Imersão.

Veremos como todos esses componentes se encaixam e trabalham juntos para criar uma solução completa.

<hr>

## 🚀  **Aula 6** 👇

[>> Video 🎞️]()

<hr>

## 🚀  **Aula 7** 👇

[>> Video 🎞️]()

<hr><br>

-.--.--.--.--.--.--.--.--.--.--.--.--.--.--.--.--.--.--.--.--.--.--.--.-
<a id="Desafios"></a>
#  ✨ **Desafios** 🛠️

[**👆 Topo**](#Home)
**********************


### **Desafio - Docker e GO - FASE 01**
`Informações do desafio`.

Esse desafio é muito empolgante principalmente se você nunca trabalhou com a **linguagem Go**!
Você terá que **publicar** uma **imagem** no **docker hub**. 

Quando executarmos:
```
docker run < seu-user>/fullcycle
````
Temos que ter o seguinte resultado: 
```
Full Cycle Rocks!!
```
Se você perceber, essa imagem apenas realiza um print da mensagem como resultado final, logo, vale a pena dar uma conferida no próprio site da **Go Lang** para aprender como fazer um **"olá mundo"**.

Lembrando que a **Go Lang** possui imagens oficiais prontas, vale a pena consultar o Docker Hub.

A imagem de nosso **projeto Go** precisa ter menos de **2MB** =)

Suba o projeto em um repositório **Git remoto** e coloque o link da imagem que subiu no **Docker Hub**.

Compartilhe o link do repositório do Git remoto para corrigirmos seu projeto.

Divirta-se!
<hr>

### **Desafio Nest.js -- FASE 02**

Informações do desafio
Neste desafio, você deve criar uma **aplicação Nest.js** com **Docker** que rode na **porta 3000**.

Esta aplicação precisa expor 2 rotas de API Rest:

- Listar assets - POST /api/assets
- Criar assets - GET /api/assets
- Criar orders - POST /api/orders
- Listar orders - GET /api/orders

Um asset tem os seguintes dados:

- id (é informado pelo usuário)
- symbol (símbolo do ativo)

Uma order tem os seguintes dados:

- id automático do banco
- asset_id (relacionado com Asset)
- price
- status (open, pending, closed) (não pode deixar mandar o status no POST)

O **ORM** a ser usado é o **Prisma ORM** e o banco de dados precisa ser o **Mongo**, 
```
image: bitnami/mongodb:5.0.17
```


Crie o arquivo **api.http** para fazer as chamadas HTTP. Ao rodar o docker compose up já precisa subir logo de cara o projeto com o **Nest.js** rodando + o **MongoDB**.


*Bons estudos!*

<br><hr>


-.--.--.--.--.--.--.--.--.--.--.--.--.--.--.--.--.--.--.--.--.--.--.--.-
<a id="Lives"></a>
# ✨ **Lives** 🎬

[**👆 Topo**](#Home)
*********************


Nessa live, você vai entender tudo que um dev precisa saber para construir uma carreira sólida em uma Big Tech.

-  [🎞️ **Como construir uma carreira sólida em uma Big Tech**](https://youtu.be/OlNdJrshn3I)
-  [🎞️ **MongoDb: Hands on oficial pela equipe da Mongo**](https://youtu.be/8RJohgzziLI)
    - Caminhos de certificaçao MongoDB, seja DBA ou DEV Learning Paths com direito a um voucher de 50% para a prova de certificação: 
    [**https://learn.mongodb.com/pages/certi...**](https://learn.mongodb.com/pages/certification-learning-paths)
-  [🎞️ **Gitlab e entrega automatizada de aplicações: Hands on oficial da Gitlab**](https://youtu.be/Gyp20s690cY)
    - **A brief history of GitLab** **https://about.gitlab.com/company/history/**
    - **gl-demo-ultimate-hugoazevedo** **https://gitlab.com/gl-demo-ultimate-hugoazevedo**
-  [🎞️ **Observabilidade no mundo real no Grupo Boticário**](https://youtu.be/A3oAqq8eeek)
-  [🎞️ **Microservices na prática**](https://youtu.be/gtv9szE_P1U)


<hr>

