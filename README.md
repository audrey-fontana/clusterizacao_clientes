# 🛍️ Análise de Métricas RFM e Clusterização de Clientes de E-commerce

Este projeto realiza uma Análise de Métricas RFM (Recência, Frequência, Valor Monetário) e aplica técnicas de Clusterização para segmentar a base de clientes de uma empresa de e-commerce. O objetivo é identificar padrões de comportamento de compra e gerar insights que permitam a personalização de campanhas de marketing.

## 🎯 Objetivo do Projeto

* Entender o Comportamento do Cliente: Utilizar a análise RFM para quantificar e categorizar o comportamento de compra dos clientes.
* Segmentação: Agrupar clientes em clusters com base em suas métricas RFM.
* Geração de Insights: Extrair características comuns de cada cluster para segmentação e personalização de estratégias de marketing (promoções, ofertas, onboarding, etc.).

## 🧱 Estrutura e Métricas

RFM - Recência, Frequência e Valor Monetário

O RFM é a base analítica que orienta estratégias de marketing personalizadas.

* R - Recência: Há quantos dias o cliente fez sua última compra.
* F - Frequência: A frequência com que o cliente realiza compras em um período.
* M - Valor Monetário: O valor médio total que o cliente gasta por transação.

#### Técnicas de Clusterização Aplicadas

Para a segmentação, foram exploradas e comparadas diferentes abordagens de clustering:

* K-Means (Modelo de melhor desempenho)
* Clustering Hierárquico (AgglomerativeClustering)
* Gaussian Mixture (GMM)
* DBSCAN

### 💾 Sobre os Dados

Os dados utilizados são de transações de compras de uma loja de e-commerce.

Fonte Original: https://www.kaggle.com/datasets/carrie1/ecommerce-data

Volume: Mais de 540.000 transações e 4.000 clientes únicos.

Escopo: Transações de e-commerce em 38 países e territórios.

### ⚙️ Pré-requisitos e Bibliotecas

O projeto foi desenvolvido em Python e requer as seguintes bibliotecas:

Manipulação:
* pandas, numpy, sidetable -> Limpeza, EDA, Cálculo de RFM e visualização de dados faltantes.

Visualização:
* matplotlib.pyplot, seaborn, plotly.express -> Visualizações 2D, boxplots, gráficos 3D interativos.

Machine Learning:
* sklearn (KMeans, GMM, DBSCAN, etc.)	-> Modelos de Clusterização, Pré-processamento (StandardScaler, PowerTransformer).

Validação:
* yellowbrick -> Visualização do método Elbow para seleção de k ideal.

Para instalar as dependências necessárias, você pode usar o seguinte comando:

pip install pandas numpy sidetable seaborn plotly scikit-learn yellowbrick

### 📈 Análise Exploratória e Pré-processamento

Limpeza de Dados:
* Remoção de valores faltantes (NaN) na coluna CustomerID.
* Tratamento de valores negativos em Quantity e UnitPrice.
* Tratamento e remoção de outliers extremos em Quantity e UnitPrice.
* Criação da coluna price_total.

Cálculo de RFM:
* As métricas R, F e M foram calculadas para cada CustomerID.
* Um outlier extremo (Cliente 15098) foi removido da análise RFM.

Transformação e Escalonamento:
* Os outliers nas métricas RFM foram atenuados usando o percentil 95 (.clip(upper=x.quantile(.95))).
* Os dados de RFM foram escalonados (utilizando scale ou StandardScaler) para garantir que todas as métricas tivessem a mesma importância na clusterização.

### 🌟 Resultados da Clusterização (K-Means)

O modelo K-Means demonstrou o melhor desempenho e interpretabilidade, segmentando os clientes em 4 clusters (conforme indicado pelo método Elbow e métricas de validação).

#### Interpretação dos Clusters (Métricas Escaladas)

A análise dos centróides (médias) de cada cluster revela as seguintes características:

* Cluster 0: Clientes Novos / Potenciais -> Foco no Onboarding e Cross-selling para aumentar Frequência e Valor.
* Cluster 1:	Clientes	Fiéis	-> Manter engajamento, programas de fidelidade, campanhas personalizadas.
* Cluester 2: Clientes	Em Risco / Perdidos	-> Campanhas urgentes de Reengajamento (win-back), descontos agressivos.
* Cluster 3: Clientes	Campeões (Maior Receita)	-> Recompensar, programas de fidelidade exclusivos, lançar novos produtos primeiro.


Sinta-se a vontade para reproduzir esse projeto e para sugerir melhorias!!









