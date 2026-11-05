#  Segmentação de Risco no SCR (BACEN) com Spark ML

**Instituição:** IESB  
**Disciplina:** Processamento de Dados Massivos  
**Nome:** Eduardo Alves de Araújo
**Problema Sorteado:** Clusterização (Aprendizado Não Supervisionado)  

---

##  Descrição do Projeto

Este trabalho aplica o algoritmo **K-Means** via **PySpark ML** sobre **7,49 milhões de registros públicos** do Sistema de Informações de Crédito (SCR) do Banco Central do Brasil (2024–2025). O objetivo é identificar partições latentes de risco de crédito e segmentação institucional de carteiras de forma automatizada e reprodutível.

---

##  Checklist de Requisitos da Disciplina

- [x] **1. Contextualização:** Descrição da base (7.492.208 linhas, 24 variáveis), pergunta de negócio e justificativa do uso de processamento distribuído.
- [x] **2. Ingestão:** Leitura automatizada por código e definição manual de esquema (`StructType`).
- [x] **3. Exploração e Limpeza:** Tratamento de nulos (0%), duplicatas, valores inválidos e auditoria de sigilo estatístico ($\le 15$ operações).
- [x] **4. Engenharia de Atributos:** Transformações `log1p()`, *ratios* de inadimplência/ativo problemático, `OneHotEncoder`, `VectorAssembler` e `StandardScaler(withMean=False)` organizados em um `Pipeline`.
- [x] **5. Modelagem:** Experimentos para $K \in [2, 8]$ com análise de WSSSE (Inércia) e Coeficiente de Silhueta.
- [x] **6. Avaliação e Interpretação:** Escolha justificada de $K = 2$ (Silhouette Score: 0,1427) e *profiling* descritivo e financeiro dos grupos.
- [x] **7. Persistência:** Modelo final salvo com o método `save()` do Spark ML.
- [x] **8. Conclusão:** Resumo dos achados econômicos, implicações para PCLD/gestão de risco e limitações do estudo.

---

##  Principais Resultados ($K = 2$)

| Cluster | Denominação | Carteira Ativa Média | Inadimplência Média | Ativo Problemático Médio | Proporção |
| :---: | :--- | :---: | :---: | :---: | :---: |
| **Cluster 0** | **Carteiras de Maior Exposição e Menor Risco Relativo** | R$ 43,87 mi | 3,43% | 9,14% | 21,80% |
| **Cluster 1** | **Carteiras de Menor Exposição e Maior Risco Relativo** | R$ 14,93 mi | 18,61% | 27,87% | 78,20% |

---

##  Tecnologias Utilizadas

- **Linguagem:** Python 3.10+
- **Framework de Big Data:** PySpark (Spark SQL & Spark ML)
- **Persistência & Cache:** `DISK_ONLY`
- **Ambiente:** Jupyter Notebook
