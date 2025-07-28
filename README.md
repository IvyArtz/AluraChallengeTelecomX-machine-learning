# AluraChallengeTelecomX-machine-learning
# 📊 Previsão de Churn com Random Forest

Este projeto tem como objetivo prever clientes com alta probabilidade de cancelamento (churn) usando dados de uma operadora de telecomunicações. Através de um pipeline de machine learning com `RandomForestClassifier`, identificamos padrões de comportamento e fornecemos insights estratégicos para retenção de clientes.

---

## 🎯 Objetivo

Identificar clientes propensos a cancelar o serviço com base em dados demográficos, de serviços contratados e cobranças, permitindo ações proativas de retenção.

---

## 🗂️ Etapas do Projeto

### 1. Coleta e Estruturação
- Fonte: [`TelecomX_Data.json`](https://raw.githubusercontent.com/alura-cursos/challenge2-data-science/refs/heads/main/TelecomX_Data.json) ou `dados_churn.csv`
- Dados aninhados (dicionários) convertidos em colunas com `pandas.json_normalize`
- Dataset unificado contendo atributos de cliente, telefone, internet e conta

### 2. Limpeza e Preparação
- Conversão de colunas como `Charges.Total` para formato numérico
- Remoção de valores ausentes
- Codificação de variáveis categóricas
- Normalização com `MinMaxScaler` (via pipeline)

---

## 📊 Análise Exploratória

- **Correlação negativa** entre `tenure` (tempo de contrato) e churn: clientes antigos tendem a ficar
- **Gastos totais** também indicam menor probabilidade de churn
- Distribuições e gráficos evidenciam perfil de risco de cancelamento

---

## 🤖 Modelagem

### Algoritmo:
- `RandomForestClassifier` com `class_weight='balanced'` (tratamento de desbalanceamento)

### Pipeline:
- Pré-processamento com `MinMaxScaler`
- Classificação com Random Forest usando melhores hiperparâmetros:
  - `max_depth=6`
  - `n_estimators=144`
  - `min_samples_split=7`
  - `min_samples_leaf=4`
  - `max_features='log2'`

### Validação:
- Divisão treino/teste (`train_test_split`)
- Validação cruzada estratificada (`StratifiedKFold`)
- Otimização via `RandomizedSearchCV`

---

## 📈 Métricas de Avaliação

### Teste:
- `Accuracy`, `Recall`, `Precision`, `F1-Score`
- **Matriz de confusão** para análise de FP/FN

### Cross-Validation:
- `recall`, `precision`, `accuracy`, `roc_auc`

> ⚠️ **Foco no recall**: identificar o maior número possível de clientes que irão cancelar.

---

## 🧠 Interpretação

### Variáveis mais importantes:
- `Contract`
- `tenure`
- `MonthlyCharges`
- `InternetService`

### Perfil de risco:
- Clientes com **contrato mensal**, **baixo tempo de permanência** e **fibra óptica** estão mais propensos ao churn.

---

## 📌 Recomendações

- Criar campanhas de retenção para clientes com contrato mensal e baixo tenure
- Oferecer descontos ou upgrades nos primeiros meses
- Investigar insatisfação em clientes com `MonthlyCharges` altos e churn elevado

---

## 💾 Próximos Passos

- Exportar modelo com `joblib`
- Criar um dashboard visual com métricas e previsões
- Implantar modelo como API para consumo em sistemas internos
- Explorar explicabilidade com SHAP

---

## 📚 Tecnologias Utilizadas

- Python
- Pandas, NumPy
- Seaborn, Matplotlib
- Scikit-learn
- Pipeline, RandomizedSearchCV, StratifiedKFold

---


