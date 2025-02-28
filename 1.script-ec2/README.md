## Automação AWS - Criação de Instância EC2 via Lambda

### Objetivo
Esta automação utiliza AWS Lambda para criar uma nova instância EC2 de forma programática. Os parâmetros necessários para a criação são definidos por variáveis de ambiente.

### Serviços AWS Utilizados
- **AWS Lambda** (Executa o script para criar a instância)
- **Amazon EC2** (Serviço de infraestrutura para instâncias virtuais)
- **Amazon CloudWatch Logs** (Armazena logs gerados pelo Lambda)

### Pré-requisitos
- Criar uma Role no IAM com as permissões necessárias para executar o Lambda.
- Definir as seguintes variáveis de ambiente no Lambda:
  - `AMI`: ID da AMI a ser utilizada.
  - `INSTANCE_TYPE`: Tipo da instância (ex: t2.micro).
  - `KEY_NAME`: Nome do par de chaves para acesso SSH.
  - `SUBNET_ID`: ID da sub-rede onde a instância será criada.

### Referências
- **Política de Permissões IAM:** [`policy.json`](./script1-IAM-Role.json)
- **Código-fonte da Automação:** [`lambda_function.py`](./script1-python.py)

