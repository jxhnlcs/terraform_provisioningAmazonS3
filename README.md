# Provisionando um Bucket S3 com Terraform

Este guia explica como configurar e provisionar um **Amazon S3 Bucket** usando **Terraform**. Ele inclui os pré-requisitos, a configuração do ambiente, a criação do usuário IAM e a execução dos comandos Terraform necessários.

## 🛠️ Pré-requisitos

Antes de começar, certifique-se de ter os seguintes requisitos atendidos:

1. **Conta AWS** - Se você ainda não tem, crie uma conta em [aws.amazon.com](https://aws.amazon.com/).
2. **AWS CLI** instalado - Para gerenciar a AWS pela linha de comando.
   - Instale via [link oficial](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)
   - Verifique a instalação com:
     ```sh
     aws --version
     ```
3. **Terraform** instalado - Ferramenta para infraestrutura como código.
   - Baixe e instale via [terraform.io](https://developer.hashicorp.com/terraform/downloads)
   - Verifique a instalação com:
     ```sh
     terraform -version
     ```

## 🔑 Criando um usuário IAM na AWS

Para permitir que o Terraform crie recursos na AWS, precisamos configurar um usuário com permissões adequadas.

1. Acesse o console da AWS: [AWS IAM Console](https://console.aws.amazon.com/iam/)
2. Vá para **Users** → **Add User**
3. Escolha um nome (ex: `terraform-user`)
4. **Acesso:** Selecione **Programmatic access**
5. **Permissões:** Escolha **Attach existing policies** e selecione **AmazonS3FullAccess**
6. **Criação:** Finalize e anote as credenciais (**Access Key ID** e **Secret Access Key**).

## 📌 Configurando credenciais no AWS CLI

Depois de criar o usuário, configure suas credenciais com:

```sh
aws configure
```

Digite as informações conforme solicitado:
```
AWS Access Key ID [None]: SEU_ACCESS_KEY
AWS Secret Access Key [None]: SEU_SECRET_KEY
Default region name [None]: us-east-1  # Ou outra região desejada
Default output format [None]: json
```

## 🚀 Executando Terraform

### 1️⃣ Inicializar o Terraform
```sh
terraform init
```
Isso baixa os plugins necessários.

### 2️⃣ Planejar a infraestrutura
```sh
terraform plan
```
Isso mostra o que será criado sem aplicar.

### 3️⃣ Criar o bucket S3
```sh
terraform apply
```
Confirme com `yes` quando solicitado.

### 4️⃣ (Opcional) Deletar a infraestrutura
Se quiser remover tudo depois:
```sh
terraform destroy
```

## 🎯 Conclusão
Agora você configurou e provisionou um bucket S3 usando Terraform. 🚀

