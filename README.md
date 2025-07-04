<p align="center">
  <img src="https://github.com/edemirtoldo/localstack/blob/main/images/localstack.png" alt="Localstack"/>
</p>

## LocalStack

`LocalStack` é uma ferramenta que permite emular serviços da AWS (Amazon Web Services) em um ambiente local. Ela é especialmente útil para desenvolvedores que desejam testar e desenvolver suas aplicações que interagem com serviços da AWS sem precisar se conectar à nuvem real, o que pode reduzir custos e aumentar a eficiência do desenvolvimento e dos testes.

### Principais Características do LocalStack

1. **Emulação de Serviços da AWS:** LocalStack suporta uma ampla gama de serviços da AWS, incluindo S3 (Simple Storage Service), DynamoDB, Lambda, SQS (Simple Queue Service), SNS (Simple Notification Service), e muitos outros. Isso permite testar funcionalidades complexas de aplicações localmente.

2. **Ambiente Local:** Ao rodar localmente, os desenvolvedores podem simular e interagir com os serviços AWS de maneira rápida e sem custos adicionais, evitando o uso excessivo de recursos reais da AWS durante o desenvolvimento e testes.

3. **Configuração Simples:** LocalStack pode ser facilmente instalado e configurado usando Docker, o que facilita a criação de um ambiente de desenvolvimento consistente em diferentes máquinas.

4. **Integração com Ferramentas de Desenvolvimento:** Ele se integra bem com ferramentas de desenvolvimento e CI/CD (Continuous Integration/Continuous Deployment), permitindo testes automatizados e integração contínua sem a necessidade de acessar a infraestrutura da AWS.

### Benefícios do Uso do LocalStack

- **Custo Reduzido:** Evita custos associados ao uso de serviços reais da AWS durante a fase de desenvolvimento e testes.
  calstack

- **Velocidade:** Testes e desenvolvimentos podem ser realizados mais rapidamente sem a latência de rede associada ao acesso à AWS.

- **Facilidade de Uso:** Simplifica a configuração de ambientes de teste locais e pode ser facilmente integrado a pipelines de CI/CD.

- **Consistência:** Garante que os desenvolvedores possam trabalhar em um ambiente de desenvolvimento local consistente, independentemente de onde estejam.

### Exemplos de Uso

- **Desenvolvimento Local:** Desenvolvedores podem criar, testar e depurar aplicações que utilizam serviços da AWS diretamente em suas máquinas locais.

- **Testes Automatizados:** LocalStack pode ser utilizado em pipelines de CI/CD para testar automaticamente mudanças de código que interagem com serviços da AWS.

- **Simulação de Serviços:** Permite a simulação de comportamentos de serviços AWS para testar cenários de falhas e outras condições que podem ser difíceis de reproduzir na AWS real.

### Conclusão

**LocalStack** é uma ferramenta poderosa para qualquer desenvolvedor que trabalha com serviços da AWS, oferecendo um ambiente local eficiente e econômico para desenvolvimento e testes.

### Tutorial

### 📋 Requisitos

| Name       | Version |
| ---------- | ------- |
| AWS CLI    | 2.17.0  |
| Terraform  | 1.12.2  |
| Docker     | 28.3.0  |
| Localstack | 4.5.0   |

### Instalação

- AWS CLI - [Documentação de Instalação do AWS Cli](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)

- Terraform - [Documentação de instalação do Terraform](https://developer.hashicorp.com/terraform/install)

- Docker - [Documentação como instalar o Docker](https://docs.docker.com/engine/install/)

- Guia básico de instalação para começar a usar o LocalStack em sua máquina local.
  [Documentação de Instalação do LocalStack](https://docs.localstack.cloud/getting-started/installation/)

A maneira mais rápida de começar a usar o LocalStack é usando a CLI do LocalStack. Ele permite que você inicie o LocalStack a partir da linha de comando. Certifique-se de ter um dockerambiente de trabalho em sua máquina antes de prosseguir.

A CLI inicia e gerencia o contêiner do Docker LocalStack. Para métodos alternativos de gerenciamento do contêiner LocalStack, consulte nossas [instruções de instalação alternativas](https://docs.localstack.cloud/getting-started/installation/#alternatives).

Vamos baixar o binario da Localstack versão 4.5.0 para uso no Linux.

```bash
curl --output localstack-cli-4.5.0-linux-amd64-onefile.tar.gz \
    --location https://github.com/localstack/localstack-cli/releases/download/v4.5.0/localstack-cli-4.5.0-linux-amd64-onefile.tar.gz
```

Vamos descompactar o pacote.

```bash
tar -xvzf localstack-cli-4.5.0-linux-amd64-onefile.tar.gz
```

Vamos mover o pacote.

```bash
sudo mv localstack /usr/local/bin
```

Para testar se o localstack está funcionando.

```bash
localstack
```

Caso seja aprentado o conteudo abaixo deu tudo certo.

```bash
Usage: localstack [OPTIONS] COMMAND [ARGS]...

  The LocalStack Command Line Interface (CLI)

Options:
  -v, --version       Show the version and exit.
  -d, --debug         Enable CLI debugging mode
  -p, --profile TEXT  Set the configuration profile
  -h, --help          Show this message and exit.

Commands:
  auth        (Beta) Authenticate with your LocalStack account
  completion  CLI shell completion
  config      Manage your LocalStack config
  logs        Show LocalStack logs
  restart     Restart LocalStack
  ssh         Obtain a shell in LocalStack
  start       Start LocalStack
  status      Query status info
  stop        Stop LocalStack
  update      Update LocalStack
  wait        Wait for LocalStack

Advanced:
  aws         Access additional functionality on LocalStack AWS Services
  dns         Manage LocalStack DNS host config
  extensions  (Beta) Manage LocalStack extensions
  license     (Beta) Manage and verify your LocalStack license
  pod         Manage the state of your instance via Cloud Pods.
  state       (Beta) Export, restore, and reset LocalStack state.
```

### Vamos iniciar o Localstack em modo daemon

```bash
localstack start -d
```

Resposta do comando

```bash
     __                     _______ __             __
    / /   ____  _________ _/ / ___// /_____ ______/ /__
   / /   / __ \/ ___/ __ `/ /\__ \/ __/ __ `/ ___/ //_/
  / /___/ /_/ / /__/ /_/ / /___/ / /_/ /_/ / /__/ ,<
 /_____/\____/\___/\__,_/_//____/\__/\__,_/\___/_/|_|

- LocalStack CLI: 4.5.0
- Profile: default
- App: https://app.localstack.cloud

[13:11:13] starting LocalStack in Docker mode 🐳                                                                       localstack.py:532
           preparing environment                                                                                       bootstrap.py:1307
           configuring container                                                                                       bootstrap.py:1315
           starting container                                                                                          bootstrap.py:1325
[13:11:15] detaching                                                                                                   bootstrap.py:1329
```

Vamos verificar o status

```bash
localstack status
```

Resposta do comando

```bash
┌─────────────────┬───────────────────────────────────────────────────────┐
│ Runtime version │ 4.5.1.dev64                                           │
│ Docker image    │ tag: latest, id: e457e8e83b45, 📆 2025-06-27T21:05:04 │
│ Runtime status  │ ✔ running (name: "localstack-main", IP: 172.17.0.2)   │
└─────────────────┴───────────────────────────────────────────────────────┘
```

Vamos verificar os logs

```bash
localstack logs
```

Resposta do comando

```bash
LocalStack version: 3.4.1.dev
LocalStack Docker container name: localstack-main
LocalStack Docker container id: 8bacdc4c848a
LocalStack Docker image sha: sha256:2e5eece2f1f55715d7fed4c2402acaba13260c80a1c53f5f21cdb08390c11ee0
LocalStack build date: 2024-06-12
LocalStack build git hash: 2b9cbc763

2024-06-13T12:33:09.608  INFO --- [  MainThread] localstack.utils.bootstrap : Execution of "start_runtime_components" took 607.29ms
Ready.
```

### Vamos preparar as credenciais do aws cli no localstack

Editar o arquivo `~/.aws/config`

```bash
[profile localstack]
region=us-east-1
output=json
endpoint_url = http://localhost:4566
```

Editar o arquivo `~/.aws/credentials`

```bash
[localstack]
aws_access_key_id = giropops
aws_secret_access_key = strigus
```

No caso da LocalStack as credenciais de acesso podem conter qualquer ID e senha

### Vamos executar Comandos Básicos do S3

:computer: **- Criar um Bucket**

```bash
aws s3 mb s3://giropops-bucket --profile localstack
```

O comando realiza a seguinte operação:

- Executa o comando `s3 mb`, que cria um novo bucket no S3 com o nome `giropops-bucket`.

- Utiliza o perfil de configuração `localstack` que foi definido no arquivo de configuração do AWS CLI. Este perfil contém credenciais e outras configurações que podem ser diferentes do perfil padrão.

:computer: **- Listar Buckets**

Para listar todos os buckets em sua conta S3:

```bash
aws s3 ls --profile localstack
```

O comando realiza a seguinte operação:

- Executa o comando `s3 ls`, que lista todos os buckets S3 disponíveis no endpoint especificado (neste caso, os buckets gerenciados pelo LocalStack).

- Utiliza o perfil de configuração `localstack` que foi definido no arquivo de configuração do AWS CLI. Este perfil contém credenciais e outras configurações que podem ser diferentes do perfil padrão.

:computer: **- Copiar arquivo para o bucket**

Criar o arquivo

```bash
touch testes
```

:computer: **- Copiar o arquivo `testes` para o bucket `s3://giropops-bucket`**

```bash
aws s3 cp testes s3://giropops-bucket --profile localstack
```

:computer: **- Vamos verificar se o arquivo foi copiado**

```bash
aws s3 ls s3://giropops-bucket --profile localstack
```

Resposta do comando:

```bash
2024-06-13 10:29:16          0 testes
```

:computer: **- Vamos remover o arquivo testes do bucket**

```bash
aws s3 rm s3://giropops-bucket/testes --profile localstack
```

Resposta do comando:

```bash
delete: s3://giropops-bucket/testes
```

:computer: **- Verificando a exclusão do arquivo testes do bucket**

```bash
aws s3 ls s3://giropops-bucket --profile localstack
```

:computer: **- Vamos excluir o bucket s3://giropops-bucket**

```bash
aws s3 rb s3://giropops-bucket --profile localstack
```

Resposta do comando:

```bash
remove_bucket: giropops-bucket
```

### Vamos testar o terraform no LocalStack

[Docs Terraform config - link](https://docs.localstack.cloud/user-guide/integrations/terraform/#manual-configuration)

Vamos fazer o clone do repositorio do [Badtux da LinuxTips](https://github.com/badtuxx/terraform-101).

```bash
git clone git@github.com:badtuxx/terraform-101.git
```

Vamos acessar o diretorio

```bash
cd terraform-101/terraform/main
```

Vamos corrigir o arquivo `variables.tf` modules/subnet/variables.tf

O arquivo está com os ips do modulo de subnets está errado deve ficar como esta abaixo:

```bash
variable "vpc_id" {
  description = "The VPC ID where subnets will be created"
  type        = string
}

variable "public_cidr_block" {
  description = "The CIDR block for the public subnet"
  type        = string
  default = "10.10.1.0/24"
}

variable "private_cidr_block" {
  description = "The CIDR block for the private subnet"
  type        = string
  default = "10.10.2.0/24"
}
```

Vamos criar o arquivo `providers.tf`

Com o seguinte conteudo

```bash
provider "aws" {
  access_key                  = "giropops"
  secret_key                  = "strigus"
  region                      = "us-east-1"
  s3_use_path_style           = false
  skip_credentials_validation = true
  skip_metadata_api_check     = true
  skip_requesting_account_id  = true

  endpoints {
    apigateway     = "http://localhost:4566"
    apigatewayv2   = "http://localhost:4566"
    cloudformation = "http://localhost:4566"
    cloudwatch     = "http://localhost:4566"
    dynamodb       = "http://localhost:4566"
    ec2            = "http://localhost:4566"
    es             = "http://localhost:4566"
    elasticache    = "http://localhost:4566"
    firehose       = "http://localhost:4566"
    iam            = "http://localhost:4566"
    kinesis        = "http://localhost:4566"
    lambda         = "http://localhost:4566"
    rds            = "http://localhost:4566"
    redshift       = "http://localhost:4566"
    route53        = "http://localhost:4566"
    s3             = "http://s3.localhost.localstack.cloud:4566"
    secretsmanager = "http://localhost:4566"
    ses            = "http://localhost:4566"
    sns            = "http://localhost:4566"
    sqs            = "http://localhost:4566"
    ssm            = "http://localhost:4566"
    stepfunctions  = "http://localhost:4566"
    sts            = "http://localhost:4566"
  }
}
```

### Vamos rodar o Terraform

```bash
terraform init
terraform plan
terraform apply --auto-approve
```

Vamos consultar os dados do EC2 criado

Detalhes de uma ou mais instâncias EC2.

```bash
aws ec2 describe-instances --profile localstack
```

Detalhes de um ou mais volumes EBS.

```bash
aws ec2 describe-volumes --profile localstack
```

Detalhes das interfaces de rede EC2.

```bash
aws ec2 describe-network-interfaces --profile localstack
```

Detalhes das regiões disponíveis.

```bash
aws ec2 describe-regions --profile localstack
```

Detalhes dos pares de chaves disponíveis.

```bash
aws ec2 describe-key-pairs --profile localstack
```

### Vamos destruir o terraform

```bash
terraform destroy --auto-approve
```

### Por fim vamos dar stop no LocalStack

```bash
localstack stop
```

Resposta do comando:

```bash
container stopped: localstack-main
```

Vamos confirmar que o LocalStack está parado

```bash
localstack status
```

Resposta do comando:

```bash
┌─────────────────┬───────────────────────────────────────────────────────┐
│ Runtime version │ 4.5.1.dev64                                           │
│ Docker image    │ tag: latest, id: e457e8e83b45, 📆 2025-06-27T21:05:04 │
│ Runtime status  │ ✖ stopped                                             │
└─────────────────┴───────────────────────────────────────────────────────┘
```

# FIM

> [!IMPORTANT]
> Documentação baseada no video SIMULANDO AWS COM LOCALSTACK E TERRAFORM: GUIA COMPLETO da LinuxtTips - https://www.youtube.com/watch?v=0nU9yvqg2Rw
