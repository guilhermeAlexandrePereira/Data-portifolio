# Projeto – Análise de Vendas (Superstore)

## 🎯 Objetivo

Desenvolver um dashboard analítico em Power BI para acompanhar o desempenho de vendas, lucro e clientes de uma operação de varejo (dataset Superstore), mostrando minha capacidade de:

- Tratar e enriquecer dados com Python
- Modelar e relacionar tabelas para BI
- Criar indicadores e visuais em Power BI
- Gerar insights acionáveis para o negócio

---

## 📂 Dados Utilizados

**Fonte:** Dataset público “Superstore” (Plotly / Kaggle)

Principais colunas:
- Datas: `Order Date`, `Ship Date`
- Cliente: `Customer ID`, `Customer Name`, `Segment`
- Geografia: `Country`, `Region`, `State`, `City`
- Produto: `Category`, `Sub-Category`, `Product Name`
- Métricas: `Sales`, `Quantity`, `Discount`, `Profit`

---

## 🛠️ Pipeline do Projeto

### 1. Preparação dos Dados (Python – Google Colab)

- Carreguei o dataset diretamente via URL
- Realizei:
  - Conversão de datas (`Order Date`, `Ship Date`)
  - Criação de colunas de tempo:
    - Ano, mês, trimestre, dia da semana, número da semana
  - Cálculo de métricas:
    - `Shipping Days` (tempo entre pedido e envio)
    - `Profit Margin` (% de margem)
    - `Revenue per Item` (venda por unidade)
  - Classificação da margem em faixas (Alta / Média / Baixa / Prejuízo)

### 2. Análise RFM (Recency, Frequency, Monetary)

- Agrupei os dados por `Customer ID` para calcular:
  - **Recency:** dias desde a última compra
  - **Frequency:** número de pedidos distintos
  - **Monetary:** total em vendas por cliente
- Criei scores R, F e M com base em quartis
- Combinei em um `RFM_Score` e segmentei clientes em:
  - **Champions**
  - **Loyal Customers**
  - **Potential Loyalists**
  - **At Risk**
  - **Hibernating**
- Juntei essas informações de volta ao dataset principal.

### 3. Tabelas Agregadas para BI

Gerei tabelas auxiliares em Python e exportei para CSV:

- `vendas_por_periodo.csv`  
  Métricas por ano / trimestre / mês:
  - Total de vendas, lucro, quantidade, nº de pedidos, nº de clientes
  - Margem % e ticket médio

- `analise_produtos.csv`  
  Performance por categoria / subcategoria / produto:
  - Vendas, lucro, quantidade, pedidos, margem %

- `analise_clientes.csv`  
  Métricas por cliente:
  - Vendas totais, lucro, nº de pedidos
  - Primeira e última compra, lifetime (dias)
  - Ticket médio

- `segmentacao_rfm.csv`  
  Tabela com Recency, Frequency, Monetary, RFM_Score e segmento do cliente.

---

## 📊 Modelagem no Power BI

### Relacionamentos principais

- `analise_clientes[Customer ID]` → `superstore_completo[Customer ID]` (1:N)
- `segmentacao_rfm[Customer ID]` → `superstore_completo[Customer ID]` (1:N)
- `analise_produtos[Product Name]` → `superstore_completo[Product Name]` (1:N)

A tabela `superstore_completo` funciona como fato principal (nível de detalhe = pedido).

---

## 🖥️ Estrutura do Dashboard

### Página 1 – Visão Geral Vendas

**Objetivo:** visão executiva do desempenho do negócio.

Principais elementos:
- **KPIs (cards):**
  - Vendas Totais
  - Lucro Total
  - Margem Média (%)
  - Total de Pedidos
- **Vendas ao longo do tempo**
- **Produtos por vendas:** 
- **Vendas por região geográfica**
- **Vendas por Segmento**

### Página 2 – Produtos

**Objetivo:** entender o perfil e a qualidade da base de clientes.

Elementos:
- **Contribuições de Produtos para as vendas**
- **Produtos por Cidade**
- **Clientes por Produtos**
- **Vendas de Produtos ao longo do Tempo**

  
---

## 🔍 Principais Insights (exemplos)

Alguns exemplos de insights que podem ser destacados:

- Produto office Supplies representa uma fatia relevante do faturamento, sendo o maior foc de vendas NY.
- Diferenças claras de performance entre **regiões** e **segmentos de clientes**.

---

## 🧰 Tecnologias Utilizadas

- **Python (Google Colab)**  
  - `pandas` para tratamento de dados
  - Exportação de CSVs para consumo no Power BI

- **Power BI Desktop**  
  - Power Query para conexão e tratamento leve
  - Modelagem relacional
  - Medidas em DAX para KPIs e cálculos adicionais
  - Criação de visuais interativos

---

## 📎 Arquivos deste projeto

- `notebooks/` – código Python usado para tratamento, RFM e agregações
- `data/` – arquivos CSV utilizados no Power BI
- `pbix/` – arquivo do relatório Power BI (se aplicável)
- `images/` – prints das páginas do dashboard

---

## 👤 Sobre mim

Analista de Dados com mais de 3 anos de experiência, com foco em:

- Construção de dashboards 
- Linguagens: **SQL, Python, DAX e M**
- Experiência em preparação de dados, criação de KPIs e suporte à tomada de decisão.

Este é o primeiro projeto do meu portfólio público, focado em análise de vendas e comportamento de clientes.
