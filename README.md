# Análise de Vendas e Clientes da Olist

![Status](https://img.shields.io/badge/status-em%20andamento-yellow)

## 📖 Visão Geral do Projeto

Este projeto apresenta uma análise de ponta a ponta do ecossistema de e-commerce da Olist, a maior loja de departamentos do Brasil. O objetivo foi além de uma análise exploratória, culminando na construção de um **Modelo de Dados Star Schema** otimizado para Business Intelligence.

A análise responde a uma pergunta de negócio central: **Quais são os principais fatores que impactam a retenção de clientes e como podemos segmentá-los para ações estratégicas?**

O pipeline de dados foi desenvolvido inteiramente em Python, e a camada de visualização e exploração de dados será implementada no Power BI.

---

## 🗃️ Estrutura do Projeto

O trabalho foi dividido em dois notebooks distintos para garantir a modularidade e as boas práticas de um projeto de dados:

1. `01_ETL_Olist.ipynb`: Responsável pela Extração, Transformação e Carga. Este notebook lida com a leitura dos dados brutos, limpeza, tratamento de valores nulos e anomalias, e a consolidação de todas as fontes em um dataset analítico (df_analise)

2. `02_Analise_e_Exportacao.ipynb`: Focado na Análise de Negócio e Engenharia de Dados para BI. A partir do dataset limpo, este notebook desenvolve:
   
   - Análise de comportamento do cliente com o modelo RFM (Recência, Frequência, Valor Monetário).

   - Análise logística para investigar a correlação entre o tempo de entrega e a satisfação do cliente.

   - **Criação e exportação das tabelas Fato e Dimensão** que compõem o Modelo Star Schema.

---

## 🛠️ Arquitetura do Modelo de Dados

Para garantir a performance e a escalabilidade no ambiente de BI, foi implementado um Modelo Star Schema, composto pelas seguintes tabelas:

`f_vendas`: Tabela central com a granularidade de cada item de pedido, contendo as chaves para as dimensões e as principais métricas de negócio.

`dim_clientes`: Dimensão com atributos únicos de cada cliente, enriquecida com a segmentação RFM.

`dim_produtos`: Dimensão com os atributos de cada produto, incluindo características físicas relevantes para a análise logística.

`dCalendario` (a ser criada no Power BI): Dimensão de tempo para possibilitar análises de Time Intelligence.

## 💡Principais Insights Descobertos

A análise revelou uma forte correlação entre a experiência de entrega e a lealdade do cliente:

1. **O "Vazamento no Balde":** A base de clientes da Olist é quase igualmente dividida entre clientes "saudáveis" (Campeões, Leais) e clientes "problemáticos" (Em Risco, Perdidos), indicando um alto custo de aquisição que não se converte em retenção.

2. **O Impacto Fatal do Atraso:** Embora a maioria das entregas chegue adiantada, os pedidos que sofrem atraso recebem, quase que invariavelmente, as piores notas de avaliação (1 e 2).

3. **A Causa da Perda de Clientes:** A inconsistência na operação logística foi validada como a causa mais provável para a alta taxa de churn, empurrando clientes para os segmentos "Em Risco" e "Perdidos" após uma única experiência ruim.

## 💻 Ferramentas Utilizadas

- **Linguagem:** Python
- **Bibliotecas Principais:**
  - `pandas`: Para manipulação e análise de dados, `matplotlib` e `seaborn` Para visualizações.
  - **BI:** Power BI Desktop

---

## 🚀 Como Executar o Projeto

1.  **Clone o repositório:**
    ```bash
    git clone https://github.com/mtferreira13/projeto-olist-dataset
    ```

2. **Estrutura de Pastas:** Certifique-se de que os dados brutos da Olist estejam na pasta data/unprocessed/.

3. **Execute o ETL:** Rode o notebook `01_ETL_Olist.ipynb` para gerar os dados processados na pasta data/processed/.

4. **Execute a Análise:** Rode o notebook `02_Analise_e_Exportacao.ipynb` para gerar as tabelas do modelo de dados na pasta `data/model/`.

5. **Abra no Power BI:** Carregue os arquivos da pasta `data/model/` e siga os próximos passos de modelagem.
---


