# 💧 AquaPredict
### Sistema Inteligente de Previsão de Nível para Reservatórios de Água

> Projeto Final — Disciplina de Sistemas Inteligentes  
> Universidade Federal Rural do Semi-Árido (UFERSA)

---

## 👥 Autores

| Nome | E-mail | GitHub |
|------|--------|--------|
| Alex Bruno Duarte | alex.duarte@alunos.ufersa.edu.br | [<img src="https://upload.wikimedia.org/wikipedia/commons/9/91/Octicons-mark-github.svg" width="16" style="vertical-align: middle;"> GitHub](https://github.com/alexb7z) |
| Carlos Henrique de Queiroz | carlos.queiroz53447@alunos.ufersa.edu.br | [<img src="https://upload.wikimedia.org/wikipedia/commons/9/91/Octicons-mark-github.svg" width="16" style="vertical-align: middle;"> GitHub](https://github.com/CarlossQueiroz) |
| José Veríssimo de Oliveira Queiroz | jose.queiroz58390@alunos.ufersa.edu.br | [<img src="https://upload.wikimedia.org/wikipedia/commons/9/91/Octicons-mark-github.svg" width="16" style="vertical-align: middle;"> GitHub](https://github.com/JV-ANUBIS) |
| Thallys Araújo de Morais | thallys.araujo@alunos.ufersa.edu.br | [<img src="https://upload.wikimedia.org/wikipedia/commons/9/91/Octicons-mark-github.svg" width="16" style="vertical-align: middle;"> GitHub](https://github.com/ThallysAM) |

---

## 📌 Sobre o Projeto

Sistemas convencionais de gerenciamento de reservatórios operam de forma reativa, acionando bombas e válvulas apenas após a detecção de níveis críticos. Isso gera desperdício de energia, acionamentos intermitentes desnecessários e risco de desabastecimento.

O **AquaPredict** é um sistema baseado em Inteligência Artificial que opera de forma proativa. Utilizando séries temporais de alta granularidade, o modelo é capaz de prever o nível de água com **1 hora de antecedência**, viabilizando o acionamento preventivo de bombas hidráulicas na borda (*edge computing*).

---

## 🧠 Modelagem Preditiva

O projeto concentra-se em um único *notebook*, onde dois modelos são implementados e rigorosamente comparados sob as mesmas métricas de validação.

### Entradas e Saídas (Features)

Para que a rede neural aprendesse os padrões do sistema hídrico, os dados brutos passaram por uma engenharia de atributos focada em sazonalidade e histórico recente:

| Variável | Tipo | Descrição |
|--------|------|-----------|
| Sazonalidade | Entrada | Hora, Minuto e Dia da Semana extraídos do `timestamp` |
| Lags 1 a 4 | Entrada | Variáveis de memória que representam as 4 últimas leituras do sensor (última 1 hora) |
| Target | Saída | Previsão do nível/estado do sistema hídrico para 4 intervalos no futuro (1 hora à frente) |

### Algoritmos Comparados

- **Modelo Principal (MLP):** Uma Rede Neural Artificial do tipo *Multilayer Perceptron*. Projetada para lidar com picos agressivos de variação e extrair a dinâmica não-linear da série temporal.
- **Baseline (Regressão Linear):** Modelo de Regressão Linear Múltipla implementado especificamente como linha de base estatística, servindo para comprovar a superioridade metodológica da IA na resolução do problema.

---

## 📊 Dataset

Para o treinamento e teste, foi utilizado o contemporâneo **SOWEKI Water Demand Dataset** (publicado no Zenodo em abril de 2026).

* **Arquivo:** `soweki_wdd_1.csv`
* **Estrutura:** Série temporal contínua
* **Granularidade:** Intervalos curtos de 15 minutos, ideais para previsões preditivas de curtíssimo prazo e lógicas de acionamento de atuadores.

---

## 📂 Estrutura do Repositório

```text
aquapredict/
│
├── README.md
├── .gitignore
│
├── data/
│   └── soweki_wdd_1.csv
│
├── docs/
│   └── artigo.pdf
│
└── notebook/
    └── aquapredict.ipynb
