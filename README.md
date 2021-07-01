###Executa teste do docker:


````docker container run hello-world --executa docker
docker container ls -- lista containers em execução
docker container ls -a -- lista containers que não estão mais em execução
docker ps -as -- lista containers que não estão mais em execução
Interação com container:
docker container run -it ubuntu /bin/bash  -- habilita o modo interativo com “i” de interação e “t” para ter acesso ao console /bin/bash inicializa o container usando o comando bash
docker container rm ID/NAME
docker container run --name meusegundocontainer hello-world
````

###Rodando containers com paginas:
````docker container run nginx -- executa o container de forma não interativa e continua
docker container run -d nginx  
docker container exec -it af89a0641238 /bin/bash -- acessa um container em modo de interação
docker container run -d -p 8080:80 nginx -- roda fazendo o parse de porta padrão
docker container run -d -p 8080:80 nginx
docker container rm ID -- remove um container em execução
docker container stop ID -- para um container em execução
docker image prune
docker system prune -af
````

###Criando imagens com docker:
````Dockerfile:
“FROM ubuntu
RUN apt-get update
RUN apt-get install curl --yes
“
OR “RUN apt-get update && apt-get install curl --yes”
docker image build -t ubuntu-curl . -- envia o contexto para o docker
docker image history ubuntu
````

###Docker registry:
````docker login --configura as credenciais do docker
docker image build -t gu1lh3rm/ubuntu-curl:v1 .
docker image ls
docker push gu1lh3rm/ubuntu-curl:v1
docker tag gu1lherm/ubuntu-curl:v1 guilherm/ubuntu-curl:latest
docker container run -d -p 8080:8080 gu1lherm/ubuntu-curl:v1
````

###Instação Kubernates
````
k3d para gerenciar instancias no kubernates
https://k3d.io/

Kubernates cli
https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/
````

###Gerenciamento de containers kubernates
````
k3d cluster create meuprimeirocluster -- cria cluster kubernates
kubectl get nodes -- lista clusters kubernates
k3d cluster list -- lista clusters kubernates
k3d cluster delete id -- deleta cluster 
k3d cluster create meucluster --servers 3 --agents 3 -- cria varios clusters
````

###Gerenciamento de clusters kubernates
````
kubectl api-resources
depois de criar o arquivo yaml execute
kubectl create -f .\meupod.yaml -- cria o pod
kubectl get pods -- lista os pods
kubectl describe pod meupod -- lista detalhes do pod
kubectl port-forward pod/meupod 8080:80 -- executa o pod e expoe a porta
kubectl get pods -l app=nginx -- lista um pod usando uma label

replicaset
kubectl apply -f meureplicaset.yaml
kubectl get replicaset
kubectl delete pod meupodreplicaset
kubectl delete replicaset meupodreplicaset
````
