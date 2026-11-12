# Spotify-Popularity-Predictor

> Atividade desenvolvida para a disciplina de Métodos Quantitativos para Análise Multivariada (ACH2036) da Escola de Artes, Ciências e Humanidades da Universidade de São Paulo (EACH-USP).

Este repositório armazena o notebook e os resultados da aplicação prática de **Modelos de Regressão Linear Múltipla** sobre a base de dados *Spotify Tracks Dataset*. O projeto abrange desde a limpeza estrutural, recodificação de variáveis categóricas e transformações não lineares de escala até a seleção automatizada de preditores, diagnóstico formal de resíduos (premissas LINE) e estimação robusta à heterocedasticidade.

---

## 📑 Sumário

* [Estrutura do Repositório](#estrutura-do-repositório)
* [Tecnologias Utilizadas](#tecnologias-utilizadas)
* [Conjunto de Dados e Análises](#conjunto-de-dados-e-análises)
* [Metodologia Aplicada](#metodologia-aplicada)
* [Como Executar o Projeto](#como-executar-o-projeto)


---

## Estrutura do Repositório

```
Regressao-Linear-Multipla-Spotify/
├── notebooks/
│   └── Exploracao_Spotify_Songs.ipynb
├── .gitignore
├── requirements.txt
└── README.md
```

---

## Tecnologias Utilizadas

A análise exploratória de dados (AED), as transformações matemáticas, a seleção de variáveis e o ajuste dos modelos econométricos foram desenvolvidos em Python 3.13 (via Jupyter Notebook / Google Colab), utilizando as seguintes bibliotecas:

* **Pandas**: Manipulação e estruturação dos dados em DataFrames.
* **kagglehub**: Download automatizado e gerenciamento de cache local do conjunto de dados diretamente do Kaggle. 
* **NumPy**: Operações matemáticas vetorizadas para aplicação das transformações de escala.
* **Matplotlib & Seaborn**: Construção de todas as visualizações de dados (gráficos de dispersão, histogramas, etc).
* **Statsmodels**: ajuste de Regressão Linear Múltipla através dos Mínimos Quadrados Ordinários (OLS), ANOVA Tipo II (Teste F Parcial), Fator de Inflação da Variância (VIF), testes de homocedasticidade (Breusch-Pagan e White), estatística de Durbin-Watson, QQ-Plots e erros-padrão. 
* **SciPy**: Diagnóstico de resíduos, plotagem de QQ-Plots e execução do teste de normalidade de Shapiro-Wilk.

Todas as dependências estão listadas no arquivo [`requirements.txt`](requirements.txt).

---

## Conjuntos de Dados e Análises

O estudo utiliza a base pública Spotify Tracks Dataset, compilada via API Web do Spotify, contendo originalmente 114.000 faixas distribuídas igualmente entre 114 gêneros musicais (1.000 faixas por gênero).  

* **Problema de Regressão:** Avaliar e quantificar em que medida os atributos acústicos, rítmicos e estruturais intrínsecos de uma gravação musical explicam sua popularidade (popularity, escala de 1 a 100) no catálogo ativo do Spotify.
* **Curadoria e Universo Amostral:** Após a supressão de índices, eliminação de duplicatas, exclusão de anomalias de extração, desduplicação de 23.809 repetições de track_id (para preservar a independência dos erros) e filtragem do piso censurado de faixas inativas (popularity == 0, 9.443 registros), a base final de modelagem consolidou-se com $n = 80.135$ músicas únicas ativas.  udo biológico focado na modelagem do peso de jacarés (variável resposta) a partir do seu comprimento (variável preditora).
---

## Metodologia Aplicada

Para cada conjunto de dados, os notebooks implementam um pipeline estatístico:

* **Limpeza Estrutural e Recodificação**: Remoção de variáveis identificadoras, análise exploratória isolada de track_genre e tradução de códigos numéricos/booleanos para categorias nominais explícitas.
* **Diagnóstico de Assimetria e Transformações de Escala**.
* **Associações Bivariadas e Multicolinearidade**: Inspeção por Scatter Plot Matrix adaptada, curvas não paramétricas LOWESS e cálculo do Fator de Inflação da Variância (VIF), comprovando ausência de multicolinearidade severa entre os preditores.   
* **Seleção de variáveis**: Avaliação combinando Teste F Parcial (ANOVA Tipo II), AIC e BIC. O critério BIC selecionou o modelo parcimonioso final.  
* **Ajuste e Premissas LINE**: Avaliação global e individual dos parâmetros estimados, análise visual, bateria de testes formais de normalidade e homocedasticidade, e correção de erros-padrão.

---

## Como Executar o Projeto

### Pré-requisitos

* Ter o **Python 3.10+** instalado na sua máquina ou utilizar a plataforma Google Colab.
### Clonar o repositório

```bash
git clone https://github.com/beatriz7227/Spotify-Popularity-Predictor.git
```

```bash
cd Spotify-Popularity-Predictor
```

### Instalar as dependências

```bash
pip install -r requirements.txt
```

### Executar os notebooks

```bash
jupyter notebook
```

* Abra o notebook e execute as células sequencialmente para reproduzir os resultados.
  
## 👥 Desenvolvido por:

* **Arthur Brandão** - [@ArthurBrandaoM](https://github.com/ArthurBrandaoM)
* **Beatriz dos Santos** - [@beatriz7227](https://github.com/beatriz7227)
