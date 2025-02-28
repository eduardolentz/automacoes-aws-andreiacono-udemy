# Automação AWS - Projeto de Cinco Funções Lambda

## Objetivo do Projeto
Este projeto contém cinco automações utilizando **AWS Lambda** para executar tarefas específicas dentro da AWS, integradas com outros serviços como **S3, EC2 e EventBridge**. O objetivo é demonstrar como funções Lambda podem ser usadas para facilitar a automação de tarefas na nuvem.

As automações desenvolvidas neste projeto são baseadas em ideias do **curso de Python ministrado por André Iacono na Udemy**. Atualmente, **três das cinco automações** já foram implementadas e documentadas. As demais serão adicionadas futuramente.


## Automação 1 - Criação de Instância EC2
- **Descrição:** Utiliza AWS Lambda para iniciar uma instância EC2 com parâmetros definidos via variáveis de ambiente.
- **Serviços AWS Utilizados:** Lambda, EC2, CloudWatch Logs.
- **Detalhes:** [Leia mais](./1.script-ec2/README.md)

## Automação 2 - Redução de Imagem com S3
- **Descrição:** Sempre que uma imagem é enviada para um bucket S3, o Lambda redimensiona a imagem e armazena no bucket de destino.
- **Serviços AWS Utilizados:** Lambda, S3, CloudWatch Logs.
- **Observação:** Deve ser executado com **Python 3.12** para evitar erros de compatibilidade com a biblioteca Pillow.
- **Detalhes:** [Leia mais](./2.script-s3/README.md)

## Automação 3 - Snapshot de Instâncias EC2 com Tag Backup
- **Descrição:** Cria automaticamente snapshots das instâncias EC2 que possuem a tag `backup=true`.
- **Serviços AWS Utilizados:** Lambda, EC2, EventBridge, CloudWatch Logs.
- **Agendamento:** Executado automaticamente a cada 24 horas pelo **Amazon EventBridge**.
- **Detalhes:** [Leia mais](./3.script-backup/README.MD)

## Próximas Automações
Ainda serão adicionadas duas automações para completar o projeto:
1. **Automação 4** - [Em desenvolvimento]
2. **Automação 5** - [Em desenvolvimento]

## Como Executar
Para cada automação, é necessário configurar as permissões adequadas no IAM e garantir que os serviços AWS utilizados estejam corretamente configurados. Cada pasta contém um **README.md** detalhando a configuração específica.

## Contribuições e Melhorias
Este projeto está em constante evolução. Qualquer sugestão de melhoria ou contribuição é bem-vinda!

---
📌 **Este repositório será atualizado com as duas automações restantes em breve!** 🚀

