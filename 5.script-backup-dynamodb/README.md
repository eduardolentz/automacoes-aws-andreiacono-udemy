# Automação AWS - Backup Automático de Tabelas DynamoDB

## Objetivo
Esta automação utiliza AWS Lambda para criar backups automáticos da tabela **carros** no **Amazon DynamoDB**. O backup é gerado diariamente e recebe um nome único com a data e hora da criação, garantindo versões organizadas.

## Serviços AWS Utilizados
- **AWS Lambda** (Executa a criação dos backups)
- **Amazon DynamoDB** (Gerencia as tabelas e backups)
- **Amazon EventBridge** (Agendamento da execução diária do Lambda)
- **Amazon CloudWatch Logs** (Armazena logs gerados pelo Lambda)

## Pré-requisitos
- Criar uma Role no IAM com as permissões necessárias para executar o Lambda.
- Criar uma regra no **Amazon EventBridge** para executar o Lambda a cada 24 horas:
  ```
  rate(24 hours)
  ```
- Configurar o evento do EventBridge para passar o nome da tabela como entrada:
  ```json
  {
    "TableName": "carros"
  }
  ```


## Referências
- **Política de Permissões IAM:** [`policy.json`](./script5-IAM-Rule.json)
- **Código da Função Lambda:** [`lambda_function.py`](./script5-Backup-DynamoDB.py)

## Observação
Para que a automação funcione corretamente, é necessário que o **EventBridge Scheduler** passe a variável `TableName` no evento com o nome da tabela. No caso desta implementação, a tabela configurada foi `carros`.

