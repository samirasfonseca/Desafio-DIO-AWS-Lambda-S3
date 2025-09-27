# 🚀 Desafio DIO - AWS Lambda + S3

## 📌 Introdução
Este repositório contém a entrega do desafio proposto pela DIO para consolidar os conhecimentos em **Lambda Function** e **Amazon S3**.  
O objetivo foi criar uma automação simples, onde o envio de arquivos a um bucket S3 dispara uma função Lambda.

##

## 📌Tecnologias Usadas

[![AWS Lambda](https://img.shields.io/badge/AWS%20Lambda-FF9900?style=for-the-badge&logo=aws-lambda&logoColor=white)](https://aws.amazon.com/lambda/)
[![Amazon S3](https://img.shields.io/badge/Amazon%20S3-569A31?style=for-the-badge&logo=amazons3&logoColor=white)](https://aws.amazon.com/s3/)
[![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/)

##


## 🎯 Objetivos de Aprendizagem
- Aplicar conceitos de **serverless** na AWS.
- Automatizar tarefas com **Lambda + S3**.
- Documentar de forma clara todo o processo técnico.
- Utilizar o **GitHub** como portfólio técnico.

##

## 🛠️ Passo a Passo da Implementação

![Diagrama](./imagens%20aws/Diagrama.png)

### 1. Criação do bucket S3
- Acesse o serviço **Amazon S3** no console da AWS.  
- Clique em **Criar bucket**.  
- Nome do bucket: `meu-bucket-dio-2025`.  
- Região: `us-east-1`.  
- Configurações padrão → **Criar bucket**.

📸 *Print do bucket criado:*  
![Bucket criado](.//imagens%20aws/bucket%20criado.png)

##

### 2. Criação da função Lambda
- Serviço: **AWS Lambda**.  
- Nome da função: `processaUploadS3`.  
- Runtime: **Python 3.10**.  
- Código usado:

```python
import json

def lambda_handler(event, context):
    bucket = event['Records'][0]['s3']['bucket']['name']
    arquivo = event['Records'][0]['s3']['object']['key']

    print(f"Arquivo {arquivo} enviado para o bucket {bucket}")

    return {
        'statusCode': 200,
        'body': json.dumps(f"Processado arquivo {arquivo} no bucket {bucket}")
    }
````
##

📸 Print da função Lambda criada: 


![Lambda criada](.//imagens%20aws/lambda%20criada%201.png)

### 3. Configuração do gatilho (trigger)
- Dentro da Lambda → **Adicionar gatilho**.  
- Serviço: **S3**.  
- Bucket: `meu-bucket-dio-2025`.  
- Evento: **All object create events**.  
- Salvar.  

📸 *Print da configuração do trigger:*  
![Trigger configurado](./imagens%20aws/bucket%20s3%20adicionado%20ao%20lambda.png)

##

### 4. Teste da automação
- Upload do arquivo `senha+twuilo.txt` para o bucket S3.  
- A Lambda foi disparada automaticamente.  
- Log registrado no CloudWatch:

Arquivo senha+twuilo.txt enviado para o bucket meu-bucket-dio-2025


📸 *Print do log no CloudWatch:*  
![Logs CloudWatch](./imagens%20aws/arquivo%20adicionado%20ao%20bucket.png)

📸 *Print do teste no S3:*  
![Teste S3](./imagens%20aws/teste%20concluido.png)

##

## 📂 Estrutura do Repositório

dDesafio-DIO-AWS-lambda-S3/  <br>       
│<br>   
├── imagens_aws/     <br>            
│   ├── bucket criado.png<br>   
│   ├── lambda criada 1.png<br>   
│   ├── bucket s3 adicionado ao lambda.png<br>   
│   ├── arquivo adicionado ao bucket.png<br>   
│   └── teste concluido.png<br>   
│<br>   
├── lambda_function.py    <br>        
│
└── README.md    <br>                 


##




## 📌 Insights e Aprendizados
- Reforcei a importância de configurar corretamente permissões no IAM.  
- Entendi como eventos do **S3** podem disparar funções Lambda automaticamente.  
- Percebi como documentar é tão importante quanto implementar, pois ajuda a fixar o conhecimento.  

--

## ✅ Conclusão
Desafio concluído com sucesso 🎉  
Este projeto servirá como base para futuras automações e práticas com AWS Lambda e S3.

