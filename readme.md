# 🎓 Sistema de Apoio à Decisão Pedagógica: Predição ENCCEJA com K-NN

Este projeto foi desenvolvido sob a perspectiva de gestão educacional para um cursinho preparatório do **ENCCEJA (Exame Nacional para Certificação de Competências de Jovens e Adultos)**. O objetivo é utilizar inteligência de dados para personalizar o acompanhamento pedagógico de novos alunos com base em seus perfis socioeconômicos.

## 📋 Contexto e Desafio Gerencial

Como gestores, recebemos alunos com históricos de vida e condições socioeconômicas diversas. No ato da matrícula, não conhecemos o desempenho prático do aluno, mas precisamos decidir:
* Qual o nível de acompanhamento pedagógico necessário?
* O aluno precisará de reforço intensivo em quais áreas?
* Como alocar professores e materiais de forma eficiente?

Para responder a isso, utilizamos os **Microdados do ENCCEJA 2024**, comparando o perfil do novo aluno com candidatos históricos semelhantes para prever seu desempenho e riscos de reprovação.

## 🛠️ Tecnologias Utilizadas

* **Linguagem:** Python 3.x
* **Bibliotecas de Dados:** `Pandas`, `NumPy`
* **Machine Learning:** `Scikit-Learn` (KNeighborsRegressor, StandardScaler)
* **Ambiente:** Jupyter Notebook

## 📂 Metodologia e Pipeline

O projeto segue um fluxo estruturado de Ciência de Dados:

### 1. Preparação e Limpeza (`00_Importacao_Conversao`)
* **Carga de Dados:** Importação dos microdados oficiais (UTF-8/Latin-1).
* **Tratamento de Missing Values:** Remoção de registros sem notas ou informações socioeconômicas essenciais.
* **Engenharia de Atributos:** Seleção de variáveis críticas como Escolaridade Anterior, Situação de Trabalho e Renda Familiar.

### 2. Modelagem com K-Nearest Neighbors (K-NN)
O algoritmo K-NN foi escolhido por sua capacidade de encontrar "vizinhos" (alunos históricos) com perfis quase idênticos ao do novo aluno.
* **Encoding:** Transformação de variáveis categóricas (Sexo, UF, Trabalho) em valores numéricos via *One-Hot Encoding*.
* **Normalização:** Uso do `StandardScaler` para garantir que variáveis com escalas diferentes (ex: Idade vs Renda) tenham o mesmo peso no cálculo da "distância" entre os perfis.
* **Predição:** O modelo calcula a média das notas dos 5 vizinhos mais próximos para sugerir a nota esperada do novo candidato.



## 📊 Aplicação Prática e Recomendações

O sistema não entrega apenas números, mas **subsídios para decisão**:

| Resultado da Análise | Recomendação Pedagógica |
| :--- | :--- |
| **Notas abaixo da média dos vizinhos** | Alocação em turmas de reforço intensivo e monitoria individualizada. |
| **Vizinhos com histórico de reprovação** | Alerta de alto risco; necessidade de suporte socioemocional e plano de estudos personalizado. |
| **Notas acima da média dos vizinhos** | Oferecimento de materiais avançados e foco em manutenção de desempenho. |

## 🚀 Como Executar

1.  **Base de Dados:** Baixe os microdados no [Portal do INEP](https://www.gov.br/inep/pt-br/acesso-a-informacao/dados-abertos/microdados/encceja).
2.  **Diretórios:** Certifique-se de que o arquivo CSV tratado está em `../data/processed/`.
3.  **Notebooks:** Execute o notebook de importação e, em seguida, o de modelagem para gerar as predições e comparativos de vizinhança.

---
**Objetivo Final:** Aumentar as chances reais de aprovação do candidato através de uma gestão educacional baseada em evidências.