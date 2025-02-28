# Automação AWS - Snapshot de Instâncias EC2 com Tag Backup

## Objetivo
Esta automação utiliza AWS Lambda para criar snapshots dos volumes de instâncias EC2 que possuem a tag `backup`. O processo é acionado automaticamente a cada 24 horas por meio do Amazon EventBridge.

## Serviços AWS Utilizados
- **AWS Lambda** (Executa a função de criação de snapshots)
- **Amazon EC2** (Gerencia instâncias e volumes)
- **Amazon EventBridge** (Agenda a execução do Lambda)
- **Amazon CloudWatch Logs** (Armazena logs gerados pelo Lambda)

## Pré-requisitos
- Criar uma Role no IAM com as permissões necessárias para executar o Lambda.
- Configurar o Amazon EventBridge para rodar o Lambda a cada 24 horas com a expressão:
  ```
  rate(24 hours)
  ```
  Ou, se precisar de um horário fixo, usar uma expressão cron como:
  ```
  cron(0 3 * * ? *)
  ```
  (Executa às 03:00 UTC todos os dias)

## Referências
- **Política de Permissões IAM:** [`policy.json`](./script3-IAM-Role.json)
- **Código-fonte da Automação:** [`lambda_function.py`](./script3-backup-instances.py)

## Observação
O Amazon EventBridge substituiu o antigo CloudWatch Events para o agendamento de execuções. O processo agora requer a criação de uma **Regra de Evento Agendado** no EventBridge, que define quando a função Lambda será acionada.

