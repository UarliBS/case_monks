# 🚀 Case Monks — Data Cleaning, Análise e Insights de Pipeline

## 📌 Visão Geral

Este projeto tem como objetivo transformar uma base de dados bruta de oportunidades comerciais em um dataset confiável para análise e tomada de decisão.

A base original apresentava inconsistências estruturais, duplicidade de registros (nível de produto vs oportunidade), problemas de padronização e divergências financeiras.

O trabalho foi dividido em três etapas principais:

1. Limpeza e padronização dos dados
2. Análise exploratória e geração de insights
3. Comunicação executiva dos resultados

---

## 🧠 Abordagem do Problema

### 🔍 Desafio inicial

A base fornecida não estava pronta para análise. Os principais problemas identificados:

* Granularidade incorreta (dados no nível de produto, não de oportunidade)
* Duplicidade de oportunidades
* Campos categóricos inconsistentes (Lead Source, Stage, Lead Office)
* Valores monetários em formatos mistos
* Divergência entre `Amount` e soma dos produtos
* Registros fora do escopo analítico

---

### 🧹 Etapa 1 — Limpeza e Preparação dos Dados

Foi desenvolvido o script `script_case_monks`, responsável por:

#### ✔️ Padronização

* Normalização de `Lead_Source`, `Stage` e `Lead_Office`
* Criação da coluna `Lead_Source_Category` (taxonomia analítica)

#### ✔️ Tratamento numérico

* Conversão de valores monetários com formatos inconsistentes
* Padronização para formato numérico utilizável

#### ✔️ Reconciliação financeira

* Ajuste de `Amount` quando divergente da soma de `Total_Product_Amount`

#### ✔️ Controle de escopo

* Separação de registros fora do escopo analítico

#### ✔️ Deduplicação

* Consolidação de oportunidades únicas (`deals_unicos`)
* Eliminação de dupla contagem causada por múltiplos produtos

---

### 📦 Outputs da Etapa 1

**📄 `opps_corrigido.xlsx`**

* `base_produto_corrigida` → dados originais corrigidos + `Lead_Source_Category`
* `apoio_limpeza_produto` → colunas auxiliares de transformação
* `deals_unicos` → base consolidada por oportunidade
* `registros_excluidos` → dados fora do escopo

**🌐 `relatorio_erros.html`**

* Resumo executivo dos problemas encontrados
* Classificação por categoria de erro
* Exemplos reais da base
* Quantidade de linhas impactadas
* Explicação em linguagem não técnica

---

## 📊 Etapa 2 — Análise e Insights

Foi desenvolvido o script `script_analise_case_monks`, que gera um relatório interativo:

**📄 `analise.html`**

### Principais análises:

1. Receita Closed Won mês a mês (2026)
2. Participação por Lead Source
3. Top 10 oportunidades em aberto
4. Win rate por canal
5. Ticket médio por tipo de negócio
6. Pipeline por estágio
7. Mix New Business vs Upsell
8. Ciclo médio de vendas
9. Top clientes do ano
10. Idade do pipeline

### 🎯 Diferenciais

* Uso de base deduplicada (evita distorções)
* Visual interativo com hover
* Observações executivas em cada gráfico

---

## 📈 Principais Insights

* Forte concentração de receita em **Customer Success (expansão)**
* Pipeline robusto em estágios avançados, mas com risco de conversão
* Dependência relevante de **upsell vs new business**
* Variação significativa de performance por canal de aquisição
* Existência de oportunidades envelhecidas no pipeline

---

## 🧾 Etapa 3 — Comunicação Executiva

Foi construída uma apresentação estratégica (8 slides) com foco em:

* Clareza para stakeholders não técnicos
* Tradução de dados em decisão
* Recomendações práticas de processo

### Principais recomendações:

* Validação de dados diretamente no CRM
* Regras automáticas para consistência financeira
* Monitoramento contínuo da qualidade do pipeline

---

## 🛠️ Tecnologias Utilizadas

* Python
* Pandas
* HTML (geração de relatórios)

---

## 💡 Aprendizados

* Qualidade de dados impacta diretamente a leitura do negócio
* Estrutura da base (granularidade) é tão importante quanto os valores
* Sem padronização, métricas como win rate e receita podem ser distorcidas
* A etapa de limpeza não é suporte, é a parte central da análise

---

## 📂 Estrutura do Projeto

```
case_monks/
├── script_case_monks.py
├── script_analise_case_monks.py
├── opps_corrigido.xlsx
├── relatorio_erros.html
├── analise.html
└── README.md
```

---

## 🚀 Como Executar

```bash
# gerar base corrigida + relatório de erros
python script_case_monks.py

# gerar análise e insights
python script_analise_case_monks.py
```

---

## 📌 Conclusão

Este projeto demonstra como transformar uma base inconsistente em uma fonte confiável de insights estratégicos.

Mais do que limpar dados, o foco foi:

* garantir integridade analítica
* evitar interpretações equivocadas
* gerar valor real para tomada de decisão

---
