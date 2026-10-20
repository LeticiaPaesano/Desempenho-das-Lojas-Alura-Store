<h1 align="center">🏪 Alura Store: Qual loja priorizar para encerramento?</h1>

<p align="center">
  Análise de dados com visão de gestão financeira para apoiar uma decisão estratégica de encerramento de loja.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10%2B-3776AB?style=flat&logo=python&logoColor=white" alt="Python 3.10+">
  <img src="https://img.shields.io/badge/pandas-Data%20Analysis-150458?style=flat&logo=pandas&logoColor=white" alt="pandas">
  <img src="https://img.shields.io/badge/SciPy-Estat%C3%ADstica-8CAAE6?style=flat&logo=scipy&logoColor=white" alt="SciPy">
  <img src="https://img.shields.io/badge/Status-Conclu%C3%ADdo-2EA44F?style=flat" alt="Status: Concluído">
</p>

---

## 📌 Resumo Executivo

**Decisão em pauta:** qual das 4 lojas da rede deve ser priorizada para encerramento.

**Decisão:** com base nos dados comerciais disponíveis, a **Loja 4 é a unidade escolhida para encerramento**. Ela tem o pior desempenho em faturamento, ticket médio e tendência recente.

> ⚠️ **Decisão com ressalvas:** a base não contém custos, margens nem lucro. A decisão se apoia no **desempenho comercial**, não na rentabilidade (detalhes na seção final).


| Indicador                                            | Loja 4                        | Referência                                                   |
|------------------------------------------------------|-------------------------------|--------------------------------------------------------------|
| Faturamento acumulado (39 meses)                     | R$ 1.384.498 (23,6%)          | Último lugar                                                 |
| Ticket médio                                         | R$ 587,15                     | Média das demais: R$ 634,02 (-7,4%)                          |
| Variação nos últimos 12 meses                        | **-25,9%**                    | Lj3: -15,0% · Lj1: -3,8% · Lj2: -0,2%                        |
| Último trimestre vs. mesmo trimestre do ano anterior | **-41,3%**                    | Menor faturamento trimestral entre todas as lojas e períodos |
| Pior colocada no scorecard                           | **98%** de 10.000 ponderações | Consistência direcional, não probabilidade                   |

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

A Loja 4 tem o menor faturamento e o menor ticket médio. Como o número de vendas é praticamente igual entre as lojas (~2.359), a diferença **não é de volume, e sim de valor por venda**.

### 2. Tendência: onde a Loja 4 se destaca negativamente

<p align="center">
<img width="1628" height="620" alt="Faturamento trimestral e faturamento acumulado em 12 meses moveis" src="https://github.com/user-attachments/assets/c78ba0dd-0ac4-4340-bac7-d3974db784e7" />
</p>

No acumulado de 12 meses móveis, a Loja 4 cai de cerca de R$ 471 mil (2022T1) para R$ 349 mil (2023T1). uma perda de aproximadamente R$ 122 mil. O faturamento do último trimestre (cerca de R$ 76 mil) é o menor da série entre todas as lojas.

<p align="center">
<img width="1394" height="477" alt="Variacao anual do faturamento por trimestre" src="https://github.com/user-attachments/assets/03ef54b8-763d-4226-90e3-fc31caad9c2e" />
</p>

A Loja 4 acumula **4 trimestres consecutivos de queda** na comparação anual: -17%, -21%, -21% e -41%. A Loja 1 também teve quatro quedas seguidas (2022T1 a 2022T4), porém menos profundas e seguidas de recuperação (+30% em 2023T1). O que distingue a Loja 4 é a **profundidade e a continuidade** da queda.

<p align="center">
<img width="1082" height="532" alt="Variacao do faturamento ultimos 12 meses vs 12 meses anteriores" src="https://github.com/user-attachments/assets/0c6ef081-63f4-40d9-af92-5171c5e53817" />
</p>

| Loja | Variação em 12 meses | Leitura |
|---|---:|---|
| **Loja 4** | **-25,9%** | Queda mais profunda e contínua |
| Loja 3 | -15,0% | Parte é efeito de base: o pico atípico de 2021T4 (~R$ 177 mil) infla a comparação; o sinal real de queda aparece só em 2023T1 (-30%) |
| Loja 1 | -3,8% | Queda leve, com recuperação recente |
| Loja 2 | -0,2% | Estável |

**Efeito de base nos dois sentidos:** o +30% da Loja 1 no último trimestre vem de uma base fraca (em 12 meses ela está em -3,8%). Já o -41% da Loja 4 compara com um trimestre forte (2022T1, o melhor da série da loja). Por isso a análise prioriza a janela de 12 meses, que dilui esse efeito, e a queda da Loja 4 se mantém.

### 3. Scorecard e teste de sensibilidade

<p align="center">
<img width="1632" height="532" alt="Ranking por criterio e % das ponderacoes em que a loja e a pior" src="https://github.com/user-attachments/assets/a4510dce-722f-4797-ad1d-4591dc29e493" />
</p>

O scorecard combina faturamento, ticket médio, variação em 12 meses e proporção de avaliações baixas. Para não depender de uma ponderação única, foram sorteadas **10.000 combinações de pesos**:

| Loja | Pior em % das ponderações |
|---|---:|
| **Loja 4** | **98%** |
| Loja 1 | 2% |
| Loja 2 | 0% |
| Loja 3 | 0% |

**Como interpretar o 98%:** faturamento e ticket médio têm rankings idênticos (o volume de vendas é praticamente igual), e a variação em 12 meses aponta na mesma direção, então três dos quatro critérios medem um sinal semelhante. A Loja 4 só deixa de ser a pior quando o peso se concentra em avaliações, critério que **não diferencia as lojas** (Kruskal-Wallis p = 0,23). O percentual indica consistência direcional, não probabilidade.

### 4. Onde está a diferença: mix de categorias

<p align="center">
<img width="1664" height="587" alt="Loja 4 vs media das demais e diferenca de participacao no mix" src="https://github.com/user-attachments/assets/9d669f4d-e557-47d3-862b-a6992d8e3680" />
</p>

- Do gap de **R$ 111 mil** frente à média das demais lojas, **99% vêm do ticket** e menos de 1% do volume.
- **Eletrodomésticos** concentram a diferença: -R$ 85 mil. Sua participação é de 27,3% na Loja 4, contra cerca de 30,9% na média das demais.
- Instrumentos musicais aparecem em seguida (-R$ 21 mil).
- O reposicionamento do mix recuperaria no máximo ~R$ 37 mil de receita por ano (teto teórico), valor insuficiente frente à queda de R$ 122 mil em 12 meses.

### 5. Visão financeira: ponto de equilíbrio do fechamento

<p align="center">
<img width="1015" height="422" alt="Custo fixo anual de equilibrio" src="https://github.com/user-attachments/assets/e7896cab-e504-4589-bf56-1ae34b587c98" />
</p>

A Loja 4 faturou **R$ 349 mil** nos últimos 12 meses. O fechamento cria valor se o **custo fixo anual evitado** (aluguel, folha, outras despesas) for maior que a contribuição que a loja ainda gera. A tabela mostra esse ponto de equilíbrio em cenários de margem e retenção:

| Margem de contribuição | Retenção 0% | 10% | 20% | 30% |
|---|---:|---:|---:|---:|
| 20% | R$ 70 mil | R$ 63 mil | R$ 56 mil | R$ 49 mil |
| 30% | R$ 105 mil | R$ 94 mil | R$ 84 mil | R$ 73 mil |
| 40% | R$ 140 mil | R$ 126 mil | R$ 112 mil | R$ 98 mil |

*Retenção = parcela da receita que migra para as outras lojas após o fechamento. Cálculo: R$ 349 mil × margem × (1 − retenção).*
Como a tabela usa a receita dos últimos 12 meses, ela é o cenário mais conservador contra o fechamento: se a receita continuar caindo, o custo fixo necessário para justificar o encerramento também diminui.*

---

## 💡 Decisão

> [!CAUTION]
> ### 🔴 LOJA ESCOLHIDA PARA ENCERRAMENTO: **LOJA 4**
>
> Menor faturamento, menor ticket médio, maior queda em 12 meses (**-25,9%**), 4 trimestres consecutivos de queda anual e pior colocada em **98%** das ponderações simuladas.

**Por que a Loja 4 e não outra:**

- **Loja 3:** é a segunda mais fraca, mas parte da queda é efeito de base e o sinal real surgiu só no último trimestre. É a **loja a monitorar**.
- **Loja 1:** tem o maior faturamento e já mostra recuperação.
- **Loja 2:** estável, sem sinal de alerta.

**Ação indicada:** priorizar a Loja 4 para o encerramento e acompanhar a Loja 3 nos próximos trimestres.

---

## ⚠️ Limitações e dados ausentes

A decisão acima se baseia exclusivamente nos dados comerciais disponíveis. Não estão na base e, portanto, **não foram considerados**:

- **Custos, margens e lucro por loja:** a análise mede desempenho comercial, não rentabilidade. As margens (20% a 40%) e a retenção (0% a 30%) da seção 5 são cenários, não dados reais.
- **Custo fixo da Loja 4:** o fechamento só gera valor se o custo fixo evitado superar o equilíbrio de R$ 49 mil a R$ 140 mil por ano.
- **Custos de encerramento** (rescisões, multa de aluguel, estoque): não estão no modelo e reduzem o ganho no primeiro ano.
- **Causas da queda recente:** não foi feita a decomposição por período (volume, ticket e categoria).

**Limites estatísticos:**

- A diferença de ticket entre as Lojas 1 e 4 tem p = 0,01 bruto, mas **p = 0,08 após a correção de Holm**. O IC 95% do bootstrap (R$ 19 a R$ 109) exclui zero, mas é amplo: é indício, não prova.
- A tendência linear da Loja 4 não é significativa (p = 0,09). O argumento se apoia na queda recente.
- A série é curta (13 trimestres) e o scorecard usa critérios parcialmente redundantes.

---
## 🚀 Como executar

abra diretamente no Google Colab: [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/LeticiaPaesano/Desempenho-das-Lojas-Alura-Store/blob/main/analise_financeira_alura_store.ipynb)

### Arquivos utilizados

As quatro bases CSV utilizadas nesta análise estão disponíveis na página de fontes de dados.

[**Consultar as fontes de dados**](fontes_dados.md)


## 🛠️ Tecnologias

Python · pandas · NumPy · Matplotlib · Seaborn · SciPy

---

## 👤 Autor

**Letícia Paesano Lima**
[LinkedIn](https://www.linkedin.com/in/leticiapaesano/) · [GitHub](https://github.com/LeticiaPaesano)

