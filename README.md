# 🧪 LLM-as-a-Judge: Pipeline de Avaliação de Fidelidade e Latência em RAG

Pipeline automatizado desenvolvido em Python para avaliar a qualidade de respostas geradas por Grandes Modelos de Linguagem (LLMs) em arquiteturas RAG (*Retrieval-Augmented Generation*). O sistema utiliza a abordagem **LLM-as-a-Judge** para detectar alucinações, atribuir notas de fidelidade ao contexto e monitorar a latência das inferências.

## 🎯 Problema Resolvido
Em sistemas de IA generativa em produção, modelos podem extrapolar o contexto fornecido e gerar informações falsas (alucinações). Este projeto implementa uma camada de **Engenharia de IA e Governança**, automatizando testes de regressão e auditoria de qualidade antes e depois do deploy de modelos.

## 🛠️ Arquitetura e Stack Técnica
* **Linguagem:** Python 3
* **SDK & Modelo Juiz:** Google GenAI SDK (`gemini-3.8-flash`) configurado com `temperature=0.0` para máxima consistência e saída estruturada em `JSON`.
* **Processamento & Relatórios:** `Pandas` para estruturação das métricas e exportação automática em `.csv`.
* **Ambiente de Execução:** Google Colab.

## 📊 Resultados Obtidos na Execução
Durante a validação com um dataset de controle (contendo respostas fiéis e uma alucinação intencional sobre gratuidade de frete), o pipeline identificou com 100% de precisão a falha de fidelidade:

| ID | Pergunta | Nota (1-5) | Alucinação? | Diagnóstico do Avaliador |
| :--- | :--- | :---: | :---: | :--- |
| **1** | Qual é o prazo para devolução de produtos? | 5 | `False` | Resposta fiel ao contexto fornecido. |
| **2** | O frete de devolução é gratuito? | 1 | `True` | Inventou informação não presente no contexto. |
| **3** | Qual o horário de atendimento do suporte? | 5 | `False` | Reproduziu com precisão as regras de horário. |

## 🚀 Como Reproduzir
1. Instale as dependências:
   ```bash
   pip install google-genai pandas
