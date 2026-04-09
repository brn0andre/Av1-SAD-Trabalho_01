# 🛣️ Análise de Sinistros Viários: Planejamento Estratégico com Machine Learning

Este repositório contém um projeto de análise de dados e modelagem preditiva aplicado à segurança viária. Como analista de dados em um órgão público de trânsito, o objetivo é transformar dados históricos da **Polícia Rodoviária Federal (PRF)** em inteligência estratégica para a redução de sinistros nas rodovias brasileiras.

## 📋 Contexto do Projeto

Tradicionalmente, campanhas educativas são baseadas em estatísticas gerais. Este projeto adota um modelo **orientado por dados (Data-Driven)** para responder à questão: 
> *Quais características dos sinistros estão mais associadas à ocorrência de vítimas e devem ser priorizadas em ações preventivas?*

## 🛠️ Tecnologias Utilizadas

* **Linguagem:** Python 3.x
* **Manipulação de Dados:** `Pandas`, `NumPy`
* **Machine Learning:** `Scikit-Learn`
* **Ambiente:** Jupyter Notebook

## 📂 Estrutura do Pipeline

O projeto está dividido em notebooks modulares para facilitar a manutenção e o entendimento:

1.  **`00_carregando_dados`**: 
    * Coleta do dataset bruto (PRF 2025).
    * Tratamento de encoding (Latin-1 para UTF-8).
    * Padronização de diretórios (`raw` para `processed`).
2.  **`01_tratamento_dados`**: 
    * Limpeza e seleção de atributos críticos (UF, fase do dia, tipo de pista, causa, etc).
    * Engenharia de Atributos: Criação da variável **Target** (0 = Sem vítimas, 1 = Com vítimas).
    * Tratamento de valores nulos e conversão de tipos.
3.  **`02_machine_learning`**: 
    * Pré-processamento com *One-Hot Encoding*.
    * Implementação de **Árvore de Decisão** com critério de **Entropia** e **Ganho de Informação**.
    * Avaliação de desempenho (Acurácia, Matriz de Confusão e Recall).

## 🧠 O Modelo

Foi utilizado o algoritmo de **Árvore de Decisão** devido à sua alta interpretabilidade (modelo "caixa branca"), permitindo que gestores públicos entendam exatamente quais regras levam a um sinistro com vítimas.

**Parâmetros principais:**
* `criterion="entropy"`
* `max_depth=5` (para garantir a generalização do modelo)
* `stratify=y` (para manter a proporção de classes no treino e teste)

## 🚀 Como Utilizar

1.  **Dados:** Baixe o arquivo de sinistros de 2025 no [Portal de Dados Abertos do Governo Federal](https://dados.gov.br).
2.  **Arquivos:** Coloque o arquivo `.csv` na pasta `data/raw/` com o nome `datatran2025.csv`.
3.  **Execução:** Siga a ordem numérica dos notebooks para processar os dados e treinar o modelo.

## 📈 Impacto nas Políticas Públicas

Os resultados gerados — especialmente o ranking de **importância de atributos** — servem para:
* **Otimização de Recursos:** Direcionar orçamentos de publicidade para os perfis de acidentes mais letais.
* **Ações Educativas:** Criar campanhas específicas (ex: focadas em tipos de pista ou causas humanas recorrentes).
* **Prevenção:** Apoiar decisões estratégicas de fiscalização em trechos críticos identificados pelo modelo.

---
