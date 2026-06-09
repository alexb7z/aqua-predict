# 💧 AquaPredict
### Sistema Inteligente de Previsão de Consumo para Reservatórios de Água

> Projeto Final — Disciplina de Sistemas Inteligentes  
> Universidade Federal Rural do Semi-Árido (UFERSA)

---

## 👥 Autores

| Nome |
|------|
| Alex Bruno |
| Carlos Henrique |
| José Veríssimo |
| Thallys Araújo |

---

## 📌 Sobre o Projeto

Sistemas convencionais de gerenciamento de reservatórios operam de forma **reativa** — acionando bombas e válvulas apenas após a detecção de níveis críticos. Isso gera desperdício de energia, acionamentos desnecessários e risco de desabastecimento.

O **AquaPredict** é um sistema baseado em Inteligência Artificial que opera de forma **preditiva**, capaz de:

- 📈 **Prever o consumo futuro** de água na próxima hora com base em padrões históricos
- ⏱️ **Estimar o tempo** até o reservatório atingir nível crítico
- 🔔 **Recomendar o acionamento antecipado** da bomba para evitar desabastecimento

---

## 🧠 Modelos Implementados

O projeto implementa e compara dois modelos de predição, utilizando o mesmo conjunto de features e métricas para uma comparação justa.

### Entradas (comuns aos dois modelos)

| Feature | Descrição |
|--------|-----------|
| Hora do dia | Extraída da coluna `Time` |
| Dia da semana | Extraído da coluna `Date` |
| Consumo da última hora | Coluna `Consumption` (lag) |
| Temperatura | Coluna `Temperature` |
| Chuva | Coluna `Rain` |
| Incidência solar | Coluna `Sun` |

**Saída:** consumo previsto (em litros) para a próxima hora

---

### 🔵 Modelo 1 — Regressão Linear

`notebooks/AquaPredict_RegressaoLinear.ipynb`

Modelo de referência (*baseline*) baseado em **Regressão Linear Múltipla**. Por ser um modelo mais simples e interpretável, serve como base de comparação para avaliar o ganho real obtido pela rede neural.

### 🟠 Modelo 2 — MLP (Rede Neural)

`notebooks/AquaPredict_MLP.ipynb`

Modelo principal baseado em **Rede Neural MLP (Multilayer Perceptron)**. Capaz de capturar relações não-lineares entre as variáveis, espera-se que supere a Regressão Linear nas métricas de avaliação.

---

### 📊 Comparação entre Modelos

Ambos os notebooks são avaliados com as mesmas métricas, permitindo comparação direta:

| Métrica | Descrição |
|---------|-----------|
| MAE | Erro Médio Absoluto |
| RMSE | Raiz do Erro Quadrático Médio |
| R² | Coeficiente de Determinação |

---

## 📂 Estrutura do Repositório

```
aquapredict/
│
├── README.md
├── .gitignore
│
├── data/
│   └── waterconsumption_noNaN_fixedTimechange.csv
│
├── docs/
│   ├── Pitch.pptx
│   └── artigo/
│       └── AquaPredict_artigo.pdf
│
└── notebooks/
    ├── AquaPredict_RegressaoLinear.ipynb
    └── AquaPredict_MLP.ipynb
```

| Caminho | Descrição |
|--------|-----------|
| `notebooks/AquaPredict_RegressaoLinear.ipynb` | Modelo baseline com Regressão Linear |
| `notebooks/AquaPredict_MLP.ipynb` | Modelo principal com Rede Neural MLP |
| `data/waterconsumption_noNaN_fixedTimechange.csv` | Dataset de consumo hídrico (46.032 registros horários) |
| `docs/Pitch.pptx` | Apresentação oral do projeto |
| `docs/artigo/AquaPredict_artigo.pdf` | Artigo científico sobre a solução desenvolvida |

---

## 📊 Dataset

**Arquivo:** `waterconsumption_noNaN_fixedTimechange.csv`  
**Registros:** 46.032 leituras horárias (sem valores nulos)  
**Período:** a partir de 01/01/2016

| Coluna | Tipo | Descrição |
|--------|------|-----------|
| `Date` | string | Data da medição (dd/mm/aaaa) |
| `Time` | string | Intervalo horário (ex: `00:00-01:00`) |
| `Consumption` | int | Consumo de água no intervalo (litros) |
| `Temperature` | float | Temperatura registrada (°C) |
| `Rain` | float | Volume de chuva (mm) |
| `Sun` | int | Incidência solar (0 ou 1) |

---

## 🗒️ Estrutura dos Notebooks

Ambos os notebooks seguem a mesma estrutura base, diferindo apenas na seção de implementação do modelo.

1. **Introdução** — contextualização do problema e objetivos
2. **Conjunto de Dados** — descrição das variáveis e carregamento
3. **Análise Exploratória (EDA)** — visualização de padrões de consumo, temperatura, chuva e sol
4. **Pré-processamento** — engenharia de features, normalização e divisão treino/teste
5. **Implementação do Modelo** — Regressão Linear *ou* MLP (conforme o notebook)
6. **Avaliação do Modelo** — métricas (MAE, RMSE, R²) e gráfico de previsão vs. real
7. **Sistema de Recomendação** *(apenas no notebook MLP)* — tempo até nível crítico e lógica de acionamento
8. **Conclusão**

---

## ▶️ Como Executar

1. Acesse o notebook desejado pelo Google Colab
2. Faça upload do arquivo `data/waterconsumption_noNaN_fixedTimechange.csv` quando solicitado
3. Execute as células sequencialmente (`Runtime > Run all`)

> O projeto foi desenvolvido inteiramente em Python, utilizando Google Colab.

---

## 🛠️ Tecnologias Utilizadas

- Python 3
- NumPy / Pandas
- Scikit-learn
- Matplotlib / Seaborn
- Google Colab

---

## 📋 Avaliação

Este projeto compõe a **Unidade III** da disciplina, com os seguintes critérios:

| Item | Peso |
|------|------|
| (a) Mapeamento da problemática e solução via programação | 4 |
| (b) Apresentação oral | 3 |
| (c) Artigo escrito | 3 |