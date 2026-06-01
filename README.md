# Análise e Previsão de Churn — Connecta Telecom

Projeto de ciência de dados para identificar os principais fatores que levam clientes a cancelar o serviço (churn) e prever quais clientes estão em risco de cancelamento.

## Sobre o projeto

A **Connecta Telecom** (empresa fictícia de telecomunicações) enfrenta uma taxa de cancelamento acima da média do setor. Este projeto ataca o problema em duas frentes:

1. **Análise estatística** — entender *por que* os clientes cancelam, com interpretação em linguagem simples (sem odds ratio)
2. **Modelo preditivo** — prever *quem* vai cancelar, usando Machine Learning

## Estrutura do projeto

```
.
├── Analise_Churn_Previsao.ipynb   # Notebook principal
├── requirements.txt               # Dependências do projeto
└── README.md                      # Este arquivo
```

## Variáveis utilizadas

| Variável | Descrição |
|---|---|
| `Fidelidade_Meses` | Tempo de contrato em meses |
| `Tipo_Contrato` | Mensal, Anual ou Dois anos |
| `Servico_Internet` | Fibra Óptica, DSL ou Não |
| `Fatura_Mensal` | Valor da fatura em R$ |
| `Churn` | 1 = cancelou, 0 = não cancelou (variável alvo) |

## O que o notebook faz

### 1. Geração dos dados
Dados fictícios gerados com `numpy` simulando 2.000 clientes com padrões realistas de churn.

### 2. Análise Exploratória (EDA)
- Taxa geral de churn
- Churn por tipo de contrato
- Distribuição por tempo de fidelidade e fatura mensal

### 3. Análise estatística simplificada
Regressão Logística via `statsmodels` com interpretação por **efeitos marginais** — mostra o impacto de cada variável diretamente em pontos percentuais, sem necessidade de conhecer odds ratio.

### 4. Modelos preditivos
Dois algoritmos comparados:
- **Regressão Logística** (scikit-learn) — simples e interpretável
- **Random Forest** — capta relações não lineares entre variáveis

Avaliação com: precisão, recall, F1-score, AUC-ROC e matriz de confusão.

### 5. Previsão de novos clientes
Função `prever_churn()` que recebe os dados de um cliente e retorna a probabilidade de cancelamento com classificação de risco:

```python
prever_churn(
    fidelidade_meses=3,
    tipo_contrato='Mensal',
    servico_internet='Fibra Óptica',
    fatura_mensal=110
)
# Probabilidade de Churn: 94.2%
# Nível de Risco: ALTO 🔴
```

## Principais resultados

| Fator | Impacto |
|---|---|
| Contrato Mensal | Altíssimo risco de churn |
| Pouco tempo de fidelidade | Primeiros meses são os mais críticos |
| Fibra Óptica | Risco ~4x maior que DSL |
| Fatura alta | Risco moderado, crescente |
| Contrato de 2 anos | Fator de proteção |

## Como executar

1. Clone o repositório:
```bash
git clone https://github.com/seu-usuario/churn-connecta-telecom.git
cd churn-connecta-telecom
```

2. Instale as dependências:
```bash
pip install -r requirements.txt
```

3. Abra o notebook:
```bash
jupyter notebook Analise_Churn_Previsao.ipynb
```

## Requisitos

- Python 3.9+
- Ver `requirements.txt` para as bibliotecas necessárias

## Tecnologias

![Python](https://img.shields.io/badge/Python-3.9+-blue)
![scikit-learn](https://img.shields.io/badge/scikit--learn-1.3+-orange)
![Pandas](https://img.shields.io/badge/Pandas-2.0+-green)
![Plotly](https://img.shields.io/badge/Plotly-5.0+-purple)
