## LocalStack

![localstack](https://github.com/edemirtoldo/localstack/blob/main/images/localstack.png)

`LocalStack` é uma ferramenta que permite emular serviços da AWS (Amazon Web Services) em um ambiente local. Ela é especialmente útil para desenvolvedores que desejam testar e desenvolver suas aplicações que interagem com serviços da AWS sem precisar se conectar à nuvem real, o que pode reduzir custos e aumentar a eficiência do desenvolvimento e dos testes.

### Principais Características do LocalStack

1. **Emulação de Serviços da AWS:** LocalStack suporta uma ampla gama de serviços da AWS, incluindo S3 (Simple Storage Service), DynamoDB, Lambda, SQS (Simple Queue Service), SNS (Simple Notification Service), e muitos outros. Isso permite testar funcionalidades complexas de aplicações localmente.

2. **Ambiente Local:** Ao rodar localmente, os desenvolvedores podem simular e interagir com os serviços AWS de maneira rápida e sem custos adicionais, evitando o uso excessivo de recursos reais da AWS durante o desenvolvimento e testes.

3. **Configuração Simples:** LocalStack pode ser facilmente instalado e configurado usando Docker, o que facilita a criação de um ambiente de desenvolvimento consistente em diferentes máquinas.

4. **Integração com Ferramentas de Desenvolvimento:** Ele se integra bem com ferramentas de desenvolvimento e CI/CD (Continuous Integration/Continuous Deployment), permitindo testes automatizados e integração contínua sem a necessidade de acessar a infraestrutura da AWS.

### Benefícios do Uso do LocalStack

- **Custo Reduzido:** Evita custos associados ao uso de serviços reais da AWS durante a fase de desenvolvimento e testes.

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

#### Instalação

Guia básico de instalação para começar a usar o LocalStack em sua máquina local.
[Instalação](https://docs.localstack.cloud/getting-started/installation/)

A maneira mais rápida de começar a usar o LocalStack é usando a CLI do LocalStack. Ele permite que você inicie o LocalStack a partir da linha de comando. Certifique-se de ter um dockerambiente de trabalho em sua máquina antes de prosseguir. Duvidas na instalação do `Docker` acesse: [Como instalar o Docker](https://docs.docker.com/engine/install/).

A CLI inicia e gerencia o contêiner do Docker LocalStack. Para métodos alternativos de gerenciamento do contêiner LocalStack, consulte nossas [instruções de instalação alternativas](https://docs.localstack.cloud/getting-started/installation/#alternatives).

Vamos baixar o binario da localstack para uso no Linux.

```bash
curl -Lo localstack-cli-3.4.0-linux-amd64-onefile.tar.gz \
    https://github.com/localstack/localstack-cli/releases/download/v3.4.0/localstack-cli-3.4.0-linux-amd64-onefile.tar.gz
```

Vamos descompactar o pacote.

```bash
tar -xvzf localstack-cli-3.4.0-linux-amd64-onefile.tar.gz
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

**Vamos iniciar o localstack**

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

 💻 LocalStack CLI 3.4.0
 👤 Profile: default

[09:33:05] starting LocalStack in Docker mode 🐳                                      localstack.py:495
           preparing environment                                                      bootstrap.py:1269
           configuring container                                                      bootstrap.py:1277
           starting container                                                         bootstrap.py:1287
[09:33:07] detaching                                                                  bootstrap.py:1291
```

Vamos verificar o status

```bash
localstack status
```

Resposta do comando

```bash
┌─────────────────┬───────────────────────────────────────────────────────┐
│ Runtime version │ 3.4.1.dev                                             │
│ Docker image    │ tag: latest, id: 2e5eece2f1f5, 📆 2024-06-12T16:04:43 │
│ Runtime status  │ ✔ running (name: "localstack-main", IP: 172.17.0.2)   │
└─────────────────┴───────────────────────────────────────────────────────┘
```

Vamos verificar os logs

```bash
localstack logs    
```

Resposta do comando

`LocalStack version: 3.4.1.dev
LocalStack Docker container name: localstack-main
LocalStack Docker container id: 8bacdc4c848a
LocalStack Docker image sha: sha256:2e5eece2f1f55715d7fed4c2402acaba13260c80a1c53f5f21cdb08390c11ee0
LocalStack build date: 2024-06-12
LocalStack build git hash: 2b9cbc763

2024-06-13T12:33:09.608  INFO --- [  MainThread] localstack.utils.bootstrap : Execution of "start_runtime_components" took 607.29ms
Ready.`


#### Vamos preparar as credenciais do aws cli no localstack

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

#### Vamos executar Comandos Básicos do S3

**- Listar Buckets**
Para listar todos os buckets em sua conta S3:

```bash
aws --profile localstack --endpoint-url http://localhost:4566 s3 ls
```

O comando realiza a seguinte operação:

- Utiliza o perfil de configuração `localstack` que foi definido no arquivo de configuração do AWS CLI. Este perfil contém credenciais e outras configurações que podem ser diferentes do perfil padrão.

- Conecta-se ao endpoint `http://localhost:4566` em vez dos endpoints da AWS. Este endpoint é provavelmente uma instância do LocalStack ou outro emulador de serviços AWS rodando localmente, o que permite testar interações com a AWS sem usar os serviços reais na nuvem.

- Executa o comando `s3 ls`, que lista todos os buckets S3 disponíveis no endpoint especificado (neste caso, os buckets gerenciados pelo LocalStack).

**- Criar um Bucket**

```bash
aws --profile localstack --endpoint-url http://localhost:4566 s3 mb s3://giropops-bucket
```

O comando realiza a seguinte operação:

- Utiliza o perfil de configuração `localstack` que foi definido no arquivo de configuração do AWS CLI. Este perfil contém credenciais e outras configurações que podem ser diferentes do perfil padrão.

- Conecta-se ao endpoint `http://localhost:4566` em vez dos endpoints da AWS. Este endpoint é provavelmente uma instância do LocalStack ou outro emulador de serviços AWS rodando localmente, o que permite testar interações com a AWS sem usar os serviços reais na nuvem.

- Executa o comando `s3 mb`, que cria um novo bucket no S3 com o nome `giropops-bucket`.

**- Copiar arquivo para o bucket**

Criar o arquivo

```bash
touch testes
```

Copiar o arquivo `testes` para o bucket `s3://giropops-bucket`

```bash
aws --profile localstack --endpoint-url http://localhost:4566 s3 cp testes s3://giropops-bucket
```

Vamos verificar se o arquivo foi copiado

```bash
➜  ~ aws --profile localstack --endpoint-url http://localhost:4566 s3 ls s3://giropops-bucket
```

Resposta do comando:

`2024-06-13 10:29:16          0 testes`

Vamos remover o arquivo testes do bucket

```bash
➜  ~ aws --profile localstack --endpoint-url http://localhost:4566 s3 rm s3://giropops-bucket/testes
```

Resposta do comando:

`delete: s3://giropops-bucket/testes`

Verificando a exclusão do arquivo testes do bucket

```bash
aws --profile localstack --endpoint-url http://localhost:4566 s3 ls s3://giropops-bucket    
```

Vamos excluir o bucket s3://giropops-bucket

```bash
aws --profile localstack --endpoint-url http://localhost:4566 s3 rb s3://giropops-bucket
```




aws s3 cp caminho/para/o/arquivo.ext s3://nome-do-seu-bucket/

Em outro terminal vamos fazer o clone do repositorio.

```bash
git clone git@github.com:badtuxx/terraform-101.git
```

```bash
cd terraform-101/terraform/main
```


aws s3 ls --profile localstack --endpoint-url=http://localhost:4566

➜  localstack 

➜  ~ localstack stop    
container stopped: localstack-main
➜  ~ 


-------

Rodando comandos

Terraform

> Documentação baseada no video SIMULANDO AWS COM LOCALSTACK E TERRAFORM: GUIA COMPLETO da LinuxtTips - https://www.youtube.com/watch?v=0nU9yvqg2Rw
