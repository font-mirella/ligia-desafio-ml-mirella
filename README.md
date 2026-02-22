# Detecção de Fraudes em Transações Financeiras com Machine Learning

**Candidata:** Mirella Fontinelle (mlfm@cin.ufpe.br)  
**Eixo:** Machine Learning — PS Ligia 2026

Este repositório contém o pipeline completo desenvolvido para o Desafio  Individual do Processo Seletivo da Liga Acadêmica de Inteligência Artificial  (Ligia) — CIn/UFPE, eixo de Aprendizado de Máquina.

## 📂 Organização do Repositório
```
├── notebooks/
│   └── notebook_desafio_ml.ipynb       # Pipeline completo: EDA, pré-processamento, 
│                              # treinamento, SHAP e geração da submissão
├── models/
│   └── modelo_xgboost_ligia.pkl     # Modelo final serializado
├── reports/
│   └── relatorio_tecnico.pdf  # Relatório técnico no padrão IEEE
├── requirements.txt           # Dependências do projeto
└── README.md
```

## 📊 Dados

Os datasets não estão incluídos no repositório devido ao tamanho dos arquivos.
Para reproduzir os resultados:

1. Acesse a competição oficial no Kaggle e baixe `train.csv` e `test.csv`.
2. Crie uma pasta `data/` na raiz do projeto.
3. Insira os arquivos CSV dentro de `data/`.

## 🚀 Como Executar

### 1. Instale as dependências
```bash
pip install -r requirements.txt
```

### 2. Configure o caminho dos dados

No notebook, certifique-se de que o caminho dos dados aponta para `../data/`.

### 3. Execute o notebook

Abra e execute `notebooks/desafio_ml.ipynb` do início ao fim. O notebook está
organizado nas seguintes etapas:

- **EDA**: Análise exploratória completa com visualizações
- **Pré-processamento**: Transformações e preparação do pipeline
- **Modelagem**: Treinamento e comparação entre Regressão Logística, 
  Random Forest e XGBoost com validação cruzada estratificada
- **Interpretabilidade**: Análise SHAP global (Summary Plot) e local 
  (Waterfall Plot)
- **Submissão**: Geração automática de `submission_final_ligia.csv` 
  ao final do notebook

## 🧠 Decisões Técnicas Principais

| Decisão | Justificativa |
|---|---|
| ROC-AUC como métrica | Robusta a desbalanceamento; mede capacidade de ordenação de risco |
| `scale_pos_weight ≈ 577` | Penalização proporcional ao desbalanceamento sem modificar os dados |
| SMOTE descartado | Risco de data leakage quando aplicado antes da validação cruzada |
| StratifiedKFold (5 folds) | Preserva proporção de fraudes em cada fold — essencial com 0,17% de positivos |
| XGBoost com early stopping | Evita sobreajuste; convergência média em ≈559 árvores de um limite de 5000 |
| SHAP para interpretabilidade | Garante rastreabilidade das decisões; consistente com os coeficientes do modelo linear |

## 📈 Resultados

| Modelo | ROC-AUC (CV) | Desvio Padrão |
|---|---|---|
| Regressão Logística | 0,9805 | ±0,0114 |
| Random Forest | 0,9658 | ±0,0149 |
| XGBoost (baseline) | 0,9829 | ±0,0100 |
| **XGBoost (tuned)** | **0,9872** | **±0,0078** |
