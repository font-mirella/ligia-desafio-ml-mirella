# Desafio Individual - Detecção de Fraudes em Transaçõoes Financeiras com Machine Learning
**Candidata:** Mirella Fontinelle (mlfm@cin.ufpe.br)

**Eixo:** Machine Learning - PS Ligia 2026

Este repositório contém meu desenvolvimento para o desafio do Processo Seletivo da Liga Acadêmica de Inteligência Artificial (Ligia) do Centro de Informática para o eixo de Machine Learning.

## 📂 Organização do Repositório
O projeto está estruturado da seguinte forma:

* **`notebooks/`**: Contém o arquivo `.ipynb` com todo o pipeline (EDA, Tratamento de Dados, Treinamento e Inferência).
* **`models/`**: Contém o artefato do modelo final serializado (`.pkl`).
* **`reports/`**: Contém o relatório técnico em PDF seguindo o padrão IEEE.
* **`requirements.txt`**: Lista de dependências para garantir a reprodutibilidade do ambiente.

## 📊 Dados
Devido ao tamanho dos arquivos, os datasets originais não foram incluídos no repositório. Para reproduzir os resultados:
1. Baixe os arquivos `train.csv` e `test.csv` da plataforma oficial (Kaggle).
2. Crie uma pasta chamada `data/` na raiz deste projeto.
3. Insira os arquivos CSV dentro dessa pasta.

## 🚀 Como Executar
1. Instale as dependências necessárias:
   ```bash
   pip install -r requirements.txt
2. O código principal de treinamento e geração das predições está em `notebooks/`. Certifique-se de que o caminho dos dados esteja configurado como `../data/`.

## 🧠 Lógica e Decisões Técnicas
Baseado na análise detalhada presente no relatório:

**Análise Exploratória**: Identifiquei forte separabilidade espacial nas variáveis V17, V14 e V12.

**Feature Engineering**: Aplicação de escala logarítmica em Amount para reduzir a assimetria e tratamento da variável Time.

**Modelo Final**: Utilizei o XGBoost com ajuste de scale_pos_weight para lidar com o desbalanceamento de 0,17%, atingindo uma ROC-AUC média de 0,9872 em validação cruzada.

**Interpretabilidade (XAI)**: Utilizei SHAP para auditar as previsões e garantir que o modelo não opere como uma "caixa-preta", confirmando que os padrões aprendidos são consistentes com a teoria estatística.
