# Automação AWS - Iniciar e Parar Instâncias EC2 em Horários Programados

## Objetivo
Esta automação utiliza AWS Lambda para **parar** instâncias EC2 às **20h** e **iniciá-las** novamente às **6h** do dia seguinte, de segunda a sexta-feira. O objetivo é **evitar custos desnecessários** mantendo as instâncias desligadas fora do horário comercial e durante o final de semana. O processo é acionado automaticamente pelo **Amazon EventBridge Scheduler**.

## Serviços AWS Utilizados
- **AWS Lambda** (Executa as funções de iniciar e parar instâncias)
- **Amazon EC2** (Gerencia as instâncias)
- **Amazon EventBridge Scheduler** (Agenda as execuções do Lambda)
- **Amazon CloudWatch Logs** (Armazena logs gerados pelo Lambda)

## Pré-requisitos
- Criar uma Role no IAM com as permissões necessárias para executar o Lambda.
- Criar duas regras no **Amazon EventBridge Scheduler**:
  - **Para desligar instâncias às 20h de segunda a sexta:**
    ```
    cron(0 20 ? * MON-FRI *)
    ```
  - **Para ligar instâncias às 6h de segunda a sexta:**
    ```
    cron(0 6 ? * MON-FRI *)
    ```


## Referências
- **Política de Permissões IAM:** [`policy.json`](./script4-IAM-Role.json)
- **Código para Parar Instâncias (`stop`):** [`stop_instances.py`](./script4-Python-Stop-Instances.py)
- **Código para Iniciar Instâncias (`start`):** [`start_instances.py`](./script4-Python-Start-Instances.py)


## Observação
Esta automação garante que instâncias EC2 sejam desligadas fora do horário comercial para otimizar custos e religadas no início do expediente automaticamente. O agendamento é feito utilizando o **Amazon EventBridge Scheduler**, que substituiu o antigo CloudWatch Events.

