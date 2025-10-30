 Desafio AWS Step Functions – Workflows Automatizados na Nuvem

 **Meu Segundo Desafio Prático de Arquitetura AWS – Step Functions**  
Este projeto faz parte da minha jornada de aprendizado em **Arquitetura de Sistemas na Nuvem**, com foco em **automação e orquestração de processos** utilizando o **AWS Step Functions**.  
O objetivo é consolidar o entendimento de como projetar, executar e documentar workflows serverless dentro da AWS.

---

 Objetivos do Desafio

- Aplicar os conceitos aprendidos em ambiente prático;
- Criar e documentar um **workflow automatizado** com Step Functions;
- Integrar o Step Functions a outros serviços AWS (ex: Lambda, DynamoDB, S3);
- Aprimorar a documentação técnica em **Markdown** e o uso do **GitHub** como portfólio.

---

 O que é AWS Step Functions?

O **AWS Step Functions** é um serviço que permite **orquestrar múltiplos serviços da AWS** em fluxos de trabalho visuais, chamados de *state machines* (máquinas de estado).  
Cada etapa (state) representa uma tarefa, decisão ou chamada a outro serviço.

Principais características:
- Execução de fluxos **serverless**;
- **Integração nativa** com AWS Lambda, DynamoDB, S3, SNS, ECS, entre outros;
- **Controle visual** do fluxo de execução (sucesso, falha e ramificações);
- **Logs detalhados** no CloudWatch.

---

⚙️ Estrutura Prática do Projeto

 1. Criação do Workflow
- Criação de uma **State Machine** no AWS Step Functions;
- Escolha do tipo: **Standard Workflow** (execuções duráveis e completas);
- Definição dos estados em **JSON**, utilizando o **Amazon States Language**.

 2. Integração com AWS Lambda
- Criação de uma função Lambda para executar uma tarefa simples (ex: validação de dados, processamento ou cálculo);
- Conexão da função Lambda como um *Task State* no fluxo Step Functions.

🧩 3. Execução e Monitoramento
- Execução do fluxo manualmente;
- Verificação dos logs e status no painel do Step Functions;
- Validação de saída e erros.

---

 Exemplo Simplificado de Definição de Workflow (JSON)

```json
{
  "Comment": "Exemplo de workflow simples",
  "StartAt": "ProcessarDados",
  "States": {
    "ProcessarDados": {
      "Type": "Task",
      "Resource": "arn:aws:lambda:us-east-1:123456789012:function:processarDados",
      "Next": "ValidarResultado"
    },
    "ValidarResultado": {
      "Type": "Choice",
      "Choices": [
        {
          "Variable": "$.status",
          "StringEquals": "OK",
          "Next": "Sucesso"
        }
      ],
      "Default": "Falha"
    },
    "Sucesso": {
      "Type": "Succeed"
    },
    "Falha": {
      "Type": "Fail"
    }
  }
}

📚 Insights e Aprendizados

Durante este desafio, aprendi:

Como modelar fluxos de execução no AWS Step Functions usando o Amazon States Language;

A importância da integração entre Lambda e Step Functions para automação de processos;

Boas práticas de documentação e versionamento no GitHub;

Como monitorar execuções e depurar erros utilizando o CloudWatch.
