# Automação AWS - Redução de Imagem com S3 e Lambda

## Objetivo
Esta automação utiliza AWS Lambda para reduzir o tamanho de imagens enviadas para a bucket `eduardolentz-origem` e armazená-las na bucket `eduardolentz-destino`. O processo ocorre automaticamente assim que uma imagem é carregada na bucket de origem.

## Serviços AWS Utilizados
- **AWS Lambda** (Executa a função de redimensionamento da imagem)
- **Amazon S3** (Armazena as imagens originais e reduzidas)
- **Amazon CloudWatch Logs** (Armazena logs gerados pelo Lambda)

## Pré-requisitos
- Criar uma Role no IAM com as permissões necessárias para executar o Lambda.
- Configurar a variável de ambiente no Lambda:
  - `DEST_BUCKET = eduardolentz-destino`
- Garantir que a função Lambda esteja configurada para rodar com o **Python 3.12**. Caso contrário, pode ocorrer um erro ao importar pacotes da biblioteca Pillow.

## Referências
- **Política de Permissões IAM:** [`policy.json`](./script2-IAM-Role.json)
- **Código-fonte da Automação:** [`lambda_function.py`](./script2-python.py)

## Observação Importante
É essencial configurar o ambiente do AWS Lambda para rodar com **Python 3.12**, pois versões anteriores podem gerar erros ao importar pacotes da biblioteca Pillow, necessária para o processamento de imagens.

Durante a investigação do erro, foi realizado o download manual da biblioteca Pillow e gerado um novo pacote ZIP para upload no Lambda. No entanto, o problema estava na versão do interpretador Python utilizada. A função estava configurada para rodar em **Python 3.13**, e a correção foi feita ao alterar para **Python 3.12**.

