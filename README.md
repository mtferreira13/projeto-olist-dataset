# Análise de Vendas e Clientes da Olist

![Status](https://img.shields.io/badge/status-em%20andamento-yellow)

## 📖 Descrição

Este projeto consiste em uma análise exploratória e aprofundada do dataset público da **Olist Store**, o maior e-commerce do Brasil. O objetivo é extrair insights valiosos sobre o comportamento de vendas, a performance logística, o perfil dos clientes e a segmentação de mercado, utilizando técnicas de limpeza de dados, engenharia de atributos e análise RFM (Recência, Frequência e Valor Monetário).

O trabalho é desenvolvido em um notebook Jupyter (`olist-analise.ipynb`) e segue uma estrutura lógica desde a avaliação inicial de cada arquivo de dados até a construção de um modelo de segmentação de clientes.

---

## 🗃️ Sobre o Dataset

O conjunto de dados utilizado contém informações anonimizadas sobre mais de 100.000 pedidos realizados na Olist entre 2016 e 2018. Ele é composto por múltiplos arquivos CSV, que se relacionam para formar uma visão completa do ecossistema da loja.

Os principais arquivos utilizados nesta análise são:
- `olist_customers_dataset.csv`
- `olist_orders_dataset.csv`
- `olist_order_items_dataset.csv`
- `olist_products_dataset.csv`
- `olist_sellers_dataset.csv`
- `olist_order_payments_dataset.csv`
- `olist_order_reviews_dataset.csv`
- `olist_closed_deals_dataset.csv`
- `product_category_name_translation.csv`
- `olist_geolocation_dataset.cvs`
- `olist_marketing_qualified_leads_dataset`

---

## 🛠️ Metodologia Aplicada

A análise foi dividida nas seguintes etapas:

1.  **Análise Exploratória Inicial:**
    - Carregamento individual de cada arquivo CSV.
    - Verificação da estrutura, tipos de dados (`.info()`), contagem de valores nulos (`.isnull().sum()`) e estatísticas descritivas (`.describe()`) para cada dataset.
    - Identificação de chaves primárias e estrangeiras para futuras unificações.

2.  **Limpeza e Tratamento de Dados:**
    - Tratamento de valores nulos em colunas críticas, como `order_approved_at`, `product_category_name` e dimensões de produtos.
    - Estratégias de imputação aplicadas: substituição por "desconhecido", zero ou mediana, conforme o contexto de cada coluna.
    - Remoção de anomalias de dados, como pedidos com status "entregue" mas sem datas de aprovação ou envio, para garantir a integridade da análise.

3.  **Conversão e Engenharia de Atributos:**
    - Conversão de colunas de texto para o formato `datetime` para possibilitar cálculos temporais.
    - Criação de novas features para enriquecer a análise, como:
        - `tempo_entrega`: Diferença em dias entre a compra e a entrega.
        - `diferenca_entrega_estimada`: Atraso ou adiantamento da entrega em relação à estimativa.
        - `ano_compra`, `mes_compra`, `dia_semana_compra`: Para análise de sazonalidade.

4.  **Unificação dos Datasets:**
    - Realização de `merge` entre os diferentes DataFrames para consolidar todas as informações em um único DataFrame mestre (`df_master`), facilitando a análise cruzada.

5.  **Análise de Negócio e RFM:**
    - Cálculo de métricas de negócio, como receita total, sazonalidade de vendas e top 10 categorias de produtos.
    - Implementação da **Análise RFM (Recência, Frequência, Valor Monetário)** para segmentar os clientes com base no seu comportamento de compra.
    - Criação de scores (R, F, M) e um score RFM combinado para classificar os clientes.

---

## 💻 Ferramentas Utilizadas

- **Linguagem:** Python 3
- **Bibliotecas Principais:**
  - `pandas`: Para manipulação e análise de dados.
  - `matplotlib` e `seaborn`: Para visualização de dados (etapa futura).

---

## 🚀 Como Executar o Projeto

1.  **Clone o repositório:**
    ```bash
    git clone https://github.com/mtferreira13/projeto-olist-dataset
    cd seu-repositorio
    ```

2.  **Instale as dependências:**
    ```bash
    pip install pandas matplotlib seaborn jupyter
    ```

3.  **Execute o notebook Jupyter:**
    ```bash
    jupyter notebook olist-analise.ipynb
    ```
    *Certifique-se de que os arquivos de dados estejam na estrutura de pastas esperada (`../data/unprocessed/`).*

---

## 🔮 Próximos Passos

- [ ] Criar visualizações gráficas (histogramas, gráficos de linha, mapas de calor) para ilustrar os insights encontrados.
- [ ] Aprofundar a análise de segmentação RFM, definindo personas para cada cluster de clientes (Ex: "Clientes Campeões", "Clientes em Risco").
- [ ] Criar um dashboard interativo com Power BI para apresentar os resultados.
