Roteiro de Configuração e Automação de Infraestrutura
1. Provisionamento do Cluster EKS com Terraform
Objetivo: Provisionar um cluster EKS chamado softdesign na região us-west-2.

Passos:
Configuração do Terraform:

Arquivo main.tf: Define o cluster EKS, grupos de nós, e roles IAM necessários.
Arquivo variables.tf: Define as variáveis utilizadas no main.tf.
Arquivo outputs.tf: Define as saídas do Terraform, como o ARN do cluster.
Comandos Executados:

bash
Copiar código
terraform init
terraform apply
Descrição dos Arquivos:

main.tf: Configuração principal para criar o cluster EKS e a configuração dos nós.
variables.tf: Definição de variáveis como a região e o nome do cluster.
outputs.tf: Exibição das saídas necessárias, como o endpoint do cluster.
Entregável: Scripts Terraform ou um roteiro detalhado com os arquivos usados.

2. Conversão do docker-compose para Manifestos K8S
Objetivo: Converter o arquivo docker-compose.yml para arquivos de manifesto Kubernetes.

Passos:
Criação dos Arquivos de Configuração:

ConfigMap: Para armazenar variáveis de ambiente.
PersistentVolumeClaim: Para garantir a persistência dos dados do MongoDB.
Deployments: Definem as aplicações app e mongo.
Services: Exposição das aplicações app e mongo.
Arquivos Criados:

configmap.yaml: Define a configuração do MongoDB.
mongo-pvc.yaml: Define o PVC para o MongoDB.
app-deployment.yaml e mongo-deployment.yaml: Configuração dos deployments.
app-service.yaml e mongo-service.yaml: Configuração dos serviços para expor os deployments.
Entregável: Arquivos YAML convertidos.

3. Criação do Dockerfile
Objetivo: Criar um Dockerfile para construir a imagem da aplicação.

Passos:
Criação do Dockerfile:

Base: Utilização de uma imagem base adequada (e.g., OpenJDK).
COPY: Adição do JAR da aplicação.
ENTRYPOINT: Configuração do comando para iniciar a aplicação.
Arquivo Criado:

Dockerfile: Define como a imagem Docker deve ser construída.
Entregável: Arquivo Dockerfile.

4. Criação do Pipeline Jenkins
Objetivo: Criar um pipeline Jenkins para automatizar o build e o deploy.

Passos:
Criação do Jenkinsfile:

Stage de Build: Constrói a imagem Docker.
Stage de Deploy: Aplica os arquivos YAML ao cluster Kubernetes.
Arquivo Criado:

Jenkinsfile: Define as etapas de build e deploy no Jenkins.
Entregável: Arquivo Jenkinsfile ou acesso ao serviço Jenkins configurado.

5. Instalação do Ingress Controller com HTTPS
Objetivo: Instalar o Ingress Controller e configurar HTTPS para o domínio.

Passos:
Instalação do Ingress Controller:

Comando de Instalação:
bash
Copiar código
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/cloud/deploy.yaml
Configuração do Ingress com HTTPS:

Arquivo de Configuração: Configuração do recurso Ingress para o domínio e TLS.
Arquivo Criado:

ingress.yaml: Define o recurso de Ingress com HTTPS.
