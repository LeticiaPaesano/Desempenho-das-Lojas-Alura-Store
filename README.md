<h1 align="center">🏪 Alura Store: Qual loja priorizar para encerramento?</h1>

<p align="center">
  Análise de dados com visão de gestão financeira para apoiar uma decisão estratégica de encerramento de loja.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10+-blue?logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/pandas-data%20analysis-150458?logo=pandas&logoColor=white" alt="pandas">
  <img src="https://img.shields.io/badge/SciPy-estat%C3%ADstica-8CAAE6?logo=scipy&logoColor=white" alt="SciPy">
  <img src="https://img.shields.io/badge/Status-conclu%C3%ADdo-success" alt="Status">
</p>

---

## 📌 Resumo Executivo

A rede Alura Store possui **4 lojas** e precisa decidir qual delas deve ser **priorizada para uma possível análise de encerramento**.


> **Resultado:** a **Loja 4** é a candidata mais forte. Ela tem o menor faturamento, o menor ticket médio e a maior queda nos últimos 12 meses, e foi a pior colocada em **98% de 10.000 ponderações simuladas** no scorecard.

| Indicador | Loja 4 |
|---|---|
| Faturamento acumulado | R$ 1.384.498 (23,6% do total) |
| Ticket médio | R$ 587,15 (média das demais: R$ 634,02) |
| Variação nos últimos 12 meses | **-25,9%** |
| Último trimestre vs. ano anterior | **-41,3%** |
| Pior colocada no scorecard | **98%** das simulações |

⚠️ **Ressalva importante:** a base não contém custos, margens ou lucro. A conclusão é sobre **desempenho comercial**, não sobre rentabilidade. A decisão final depende dos custos reais da loja (veja a seção [Limitações](#-limitações)).

---

## 🎯 Motivação

Fechar uma loja é uma decisão cara e difícil de reverter. Comparar apenas o faturamento total pode levar a conclusões erradas, porque:

- as diferenças entre as lojas são **pequenas** (a Loja 1 fatura cerca de 10,8% a mais que a Loja 4 em 39 meses);
- um único trimestre bom ou ruim pode distorcer a leitura;
- o peso que se dá a cada critério muda o resultado.

Por isso, o projeto vai além do ranking simples: valida os dados, usa a série temporal completa, testa a robustez estatística e verifica se a conclusão **resiste a diferentes escolhas de pesos**.

---

## 🗂️ Dados

| Item | Descrição |
|---|---|
| Fonte | Base do Challenge de Data Science da Alura (4 arquivos CSV, um por loja) |
| Registros | 9.435 vendas (2.359 + 2.359 + 2.359 + 2.358) |
| Período | 01/01/2020 a 31/03/2023 (13 trimestres completos) |
| Variáveis | Produto, categoria, preço, frete, data, vendedor, local, avaliação, pagamento, parcelas, coordenadas |
| Qualidade | Sem nulos, duplicados, datas inválidas, preços/fretes inconsistentes ou notas fora da escala |

---

## 🧪 Metodologia

1. **Carga e validação:** consolidação das 4 bases e checagem de qualidade.
2. **Indicadores comerciais:** faturamento, participação, ticket médio, frete e avaliações.
3. **Tendência:** série trimestral completa, 12 meses móveis (elimina sazonalidade) e variação anual por trimestre.
4. **Robustez estatística:** Kruskal-Wallis, Mann-Whitney com correção de Holm e IC 95% por bootstrap.
5. **Scorecard com teste de sensibilidade:** 10.000 conjuntos aleatórios de pesos, para que a escolha não dependa de uma ponderação subjetiva.
6. **Diagnóstico de mix:** em quais categorias está a diferença.
7. **Visão financeira:** custo fixo de equilíbrio do fechamento, por cenário de margem e retenção de clientes.

---

## 📊 Resultados

### 1. Faturamento e ticket médio

<p align="center">
  <<img width="1522" height="587" alt="Faturamento acumulado e ticket medio por venda" src="https://github.com/user-attachments/assets/36edbd36-5005-4cef-b58b-839b3a248ac0" />
</p>

A Loja 4 tem o menor faturamento e o menor ticket. Como o número de vendas é praticamente igual entre as lojas (~2.359), a diferença **não é de volume, e sim de valor por venda**.

### 2. Tendência: onde a Loja 4 se destaca negativamente

<p align="center">
<img width="1628" height="620" alt="Faturamento trimestral e faturamento acumulado em 12 meses moveis" src="https://github.com/user-attachments/assets/c78ba0dd-0ac4-4340-bac7-d3974db784e7" />
</p>

No gráfico de 12 meses móveis, a Loja 4 cai de cerca de R$ 471 mil (2022T1) para R$ 349 mil (2023T1). A Loja 3 também cai, mas partiu de um pico atípico em 2021T4.

<p align="center">
<img width="1394" height="477" alt="Variacao anual do faturamento por trimestre" src="https://github.com/user-attachments/assets/03ef54b8-763d-4226-90e3-fc31caad9c2e" />
</p>

A Loja 4 acumula **4 trimestres consecutivos de queda** na comparação anual: -17%, -21%, -21% e -41%.

<p align="center">
<img width="1082" height="532" alt="Variacao do faturamento ultimos 12 meses vs 12 meses anteriores" src="https://github.com/user-attachments/assets/0c6ef081-63f4-40d9-af92-5171c5e53817" />
</p>

| Loja | Variação em 12 meses |
|---|---:|
| Loja 4 | **-25,9%** |
| Loja 3 | -15,0% |
| Loja 1 | -3,8% |
| Loja 2 | -0,2% |

> A Loja 1 teve +30% no último trimestre vs. o ano anterior, mas isso é efeito de base: em 12 meses ela está em -3,8%.

### 3. Scorecard e teste de sensibilidade

<p align="center">
<img width="1632" height="532" alt="Ranking por criterio e % das ponderacoes em que a loja e a pior" src="https://github.com/user-attachments/assets/a4510dce-722f-4797-ad1d-4591dc29e493" />
</p>

O scorecard combina faturamento, ticket médio, variação em 12 meses e proporção de avaliações baixas. Para não depender de uma ponderação única, sorteei **10.000 combinações de pesos**:

| Loja | Pior em % das ponderações |
|---|---:|
| **Loja 4** | **98%** |
| Loja 1 | 2% |
| Loja 2 | 0% |
| Loja 3 | 0% |

### 4. Onde está a diferença: mix de categorias

<p align="center">
<img width="1664" height="587" alt="Loja 4 vs media das demais e diferenca de participacao no mix" src="https://github.com/user-attachments/assets/9d669f4d-e557-47d3-862b-a6992d8e3680" />
</p>

- Do gap de **R$ 111 mil** frente à média das demais lojas, **99% vêm do ticket** e menos de 1% do volume.
- **Eletrodomésticos** concentram a diferença: -R$ 85 mil. Sua participação é de 27,3% na Loja 4, contra cerca de 30,9% na média das demais.
- Instrumentos musicais aparecem em seguida (-R$ 21 mil).

### 5. Visão financeira: o fechamento compensa?

<p align="center">
<img width="1015" height="422" alt="Custo fixo anual de equilibrio" src="https://github.com/user-attachments/assets/e7896cab-e504-4589-bf56-1ae34b587c98" />
</p>

A Loja 4 faturou **R$ 349 mil** nos últimos 12 meses. O fechamento só cria valor se o **custo fixo anual evitado** (aluguel, folha, outras despesas) for maior que a contribuição que a loja ainda gera:

| Margem de contribuição | Retenção 0% | 10% | 20% | 30% |
|---|---:|---:|---:|---:|
| 20% | R$ 70 mil | R$ 63 mil | R$ 56 mil | R$ 49 mil |
| 30% | R$ 105 mil | R$ 94 mil | R$ 84 mil | R$ 73 mil |
| 40% | R$ 140 mil | R$ 126 mil | R$ 112 mil | R$ 98 mil |

*Retenção = parcela da receita que migra para as outras lojas após o fechamento.*

---

## ✅ A escolha: por que a Loja 4?

| Critério | Resultado da Loja 4 |
|---|---|
| Faturamento acumulado | Último lugar |
| Ticket médio | Último lugar |
| Variação em 12 meses | Última (-25,9%) |
| Tendência recente | 4 trimestres seguidos de queda anual |
| Scorecard | Pior em 98% das simulações de pesos |
| Avaliação dos clientes | Intermediária (não é o fator de decisão) |

**Critérios que não diferenciam as lojas e foram descartados:**
- **Frete sobre faturamento:** idêntico (5,33%) em todas.
- **Avaliação dos clientes:** diferenças pequenas e não significativas (Kruskal-Wallis p = 0,23).

**Segunda loja a monitorar:** a **Loja 3** (-15,0% em 12 meses, com queda de 34% e 30% nos dois últimos trimestres).

---

## ⚠️ Limitações

Para uma leitura honesta dos resultados:

- **Sem custos, margens e lucro.** A análise mede desempenho comercial, não rentabilidade.
- **Premissas de margem (20% a 40%) e retenção (0% a 30%)** são cenários, não dados reais.
- **Custos de encerramento** (rescisões, multa de aluguel, estoque) não estão no modelo e reduzem o ganho no primeiro ano.
- **Evidência estatística moderada.** A diferença de ticket entre as Lojas 1 e 4 tem p = 0,01 bruto, mas **p = 0,08 após a correção de Holm**. O IC 95% do bootstrap (R$ 19 a R$ 109) exclui zero, mas a margem é ampla: é indício, não prova.
- **A tendência linear da Loja 4 não é significativa** (p = 0,09). O argumento se apoia na queda recente.
- **Série curta:** 13 trimestres.

---

## 💡 Recomendação

> [!CAUTION]
> ### 🔴 LOJA A PRIORIZAR PARA ENCERRAMENTO: **LOJA 4**
>
> Menor faturamento, menor ticket médio, maior queda em 12 meses (**-25,9%**) e pior colocada em **98%** das ponderações simuladas.

**Decisão final condicionada a:**

1. 🔴 custo fixo anual real da Loja 4 **superior** à faixa de equilíbrio da tabela acima (R$ 49 mil a R$ 140 mil);
2. estimativa dos custos de encerramento (rescisões, multa de aluguel, estoque).

**Se o custo fixo for baixo:** manter a Loja 4 com um plano de recuperação focado em eletrodomésticos e revisão trimestral. O reposicionamento do mix sozinho recuperaria no máximo ~R$ 37 mil de receita por ano (teto teórico), o que não reverte a queda de R$ 122 mil em 12 meses, então precisaria vir acompanhado de redução de custos.

**Segunda loja a monitorar:** 🟠 Loja 3 (-15,0% em 12 meses).

---

## 🚀 Como executar

abra diretamente no Google Colab: [![Open In Colab](https://github.com/LeticiaPaesano/Desempenho-das-Lojas-Alura-Store/blob/main/analise_financeira_alura_store.ipynb)

### Arquivos utilizados

As quatro bases CSV utilizadas nesta análise estão disponíveis na página de fontes de dados.

[**Consultar as fontes de dados**](fontes_dados.md)


## 🛠️ Tecnologias

Python · pandas · NumPy · Matplotlib · Seaborn · SciPy

---

## 👤 Autor

**Letícia Paesano Lima**
[LinkedIn](https://www.linkedin.com/in/leticiapaesano/) · [GitHub](https://github.com/LeticiaPaesano)

---

<p align="center">Projeto desenvolvido no Challenge de Data Science da Alura.</p>
