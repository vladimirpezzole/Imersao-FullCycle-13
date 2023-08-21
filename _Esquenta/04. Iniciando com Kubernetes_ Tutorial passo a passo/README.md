 #  ✨ **Esquenta**  👇 

[**👆 Voltar**](https://github.com/vladimirpezzole/Imersao-FullCycle-13)
*************
### **04. Iniciando com Kubernetes: Tutorial passo a passo**

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
