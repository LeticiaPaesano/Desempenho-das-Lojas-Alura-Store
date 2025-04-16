# 📊 Desempenho das Lojas - Alura Store

Este repositório apresenta uma análise exploratória de dados sobre o desempenho de quatro lojas da Alura Store. O objetivo principal é fornecer uma base analítica sólida para apoiar a decisão de **qual loja deve ser vendida** para ajudar o senhor João, com base em métricas quantitativas e qualitativas extraídas dos dados.

---

## 🧭 Objetivo da Análise

A análise tem como foco comparar o desempenho das lojas utilizando indicadores relevantes, como:

- **Análise do Faturamento**
- **Vendas por Categoria**
- **Média de Avaliação das Lojas**
- **Produtos Mais e Menos Vendidos**
- **Frete Médio por Loja**

A partir dessas informações, identificar qual loja **apresenta o menor desempenho geral**, considerando fatores financeiros, operacionais e de satisfação do cliente.

---

## 📂 Estrutura do Projeto

- `dados/`: Dataset utilizado na análise.
- `graficos/`: Visualizações geradas para interpretação dos dados.
- `notebook/`: Notebook com todo o processo analítico.
- `README.md`: Documento explicativo sobre o projeto.

---

## 📈 Visualizações e Insights

# Gráfico de faturamento por loja
O gráfico abaixo apresenta o faturamento total de cada loja. A Loja 1 obteve o maior valor, com R$ 1.534.509,12, enquanto a Loja 4 teve o menor desempenho, com R$ 1.384.497,58.
Essa diferença evidencia que a Loja 4 tem menor retorno financeiro, sendo um dos principais indícios para considerá-la como a possível candidata à venda.

![image](https://github.com/user-attachments/assets/dd9d16b4-832d-4172-acd4-a7d05ea5e016)

# Vendas por categoria

Este gráfico apresenta a quantidade de produtos vendidos por categoria em cada loja. A categoria "móveis" se destaca com o maior volume de vendas em todas as unidades, especialmente na Loja 3, que lidera em volume geral. Categorias como "eletrônicos", "utilidades domésticas" e "brinquedos" também apresentam bons números, com desempenho consistente entre as lojas.
A Loja 4 demonstra força nas categorias de maior volume, o que reforça sua competitividade. Em contrapartida, categorias como "instrumentos musicais" e "livros" têm participação significativamente menor em todas as lojas, indicando menor impacto no desempenho comercial.

![image](https://github.com/user-attachments/assets/cec83851-82f2-4c7e-866d-c51ce67ae138)


# Avaliação média por loja

Média das avaliações feitas pelos clientes em cada loja. A **Loja 3** lidera com a maior média de avaliação **(4.05)**, seguida de perto pela **Loja 2 (4.04)** e **Loja 4 (4.00)**. A **Loja 1** teve o pior desempenho nesse quesito, com uma média de **3.98**.

Essa métrica é essencial para entender a satisfação do cliente, e pode impactar diretamente na reputação e fidelização. Embora a diferença entre as médias não seja tão alta, o padrão consistente reforça o bom desempenho da **Loja 3** e levanta um ponto de atenção para a **Loja 1**.

![image](https://github.com/user-attachments/assets/be3d085a-eb60-45d2-9b01-258d988c6c32)

# Produtos Mais e menos vendidos em todas as lojas

O gráfico a seguir mostra a quantidade de produtos vendidos em cada categoria, separada por loja. É possível perceber que a categoria "móveis" lidera as vendas em todas as unidades, com destaque para a **Loja 3** e **Loja 4**, que apresentam os maiores volumes.

Logo em seguida, as categorias "eletrônicos", "utilidades domésticas" e "brinquedos" também apresentam desempenho sólido e consistente entre todas as lojas. Isso indica uma tendência de consumo clara, que pode ser útil para decisões estratégicas de estoque e marketing.

Por outro lado, as categorias "instrumentos musicais" e "livros" representam uma fatia significativamente menor das vendas, sendo os itens menos vendidos em todas as lojas. Esses dados ajudam a compreender que, embora estejam disponíveis, esses produtos não têm grande impacto comercial.

![image](https://github.com/user-attachments/assets/58dd6d25-1db3-4633-a721-0680576b8776)

# Produto mais vendido

O produto mais vendido em cada loja: móveis. A **Loja 3** se sobressai com **499 unidades**, seguida pela **Loja 4 com 480**, demonstrando forte aderência do público a essa categoria. Essa evidência confirma a importância dos móveis na composição do faturamento e reforça sua liderança como carro-chefe nas vendas da Alura Store.

A consistência nas vendas de móveis entre todas as lojas mostra que essa categoria é essencial para a operação comercial, sendo um ponto forte a ser mantido independentemente da loja escolhida para venda.

![image](https://github.com/user-attachments/assets/a43ee448-06cb-44ef-84d3-891afc765e73)

# Produto menos vendido

O gráfico revela que utilidades domésticas e instrumentos musicais foram as categorias com menor volume de vendas nas quatro lojas. A **Loja 4** teve o menor número absoluto, com **170 unidades** de instrumentos musicais vendidas, enquanto a **Loja 2** vendeu **181 unidades** de utilidades domésticas, sendo a maior entre os menores.

Essas categorias representam baixa representatividade no total de vendas, sugerindo uma menor demanda do público e menor impacto no desempenho comercial geral. Isso pode orientar futuras decisões de estoque e marketing.

![image](https://github.com/user-attachments/assets/51e45397-b5ce-4254-83f3-3d3b1769d295)

# Frete médio por estado

Este gráfico de dispersão mostra a relação entre o frete total gasto e o frete médio por pedido em cada loja. A **Loja 1** apresenta tanto o maior custo total de frete quanto o maior frete médio, com destaque em relação às demais. Por outro lado, a **Loja 4** possui os menores valores em ambos os indicadores, demonstrando maior eficiência logística.

Lojas com frete mais alto podem impactar a satisfação do cliente e os custos operacionais. 

![image](https://github.com/user-attachments/assets/8f49bb3d-9c35-46aa-b140-36992631cc45)

# Mapa de calor com latitude e longitude das lojas

O mapa abaixo apresenta as unidades da Alura Store em diferentes pontos do Brasil, com cores representando cada loja:

🔴 Loja 1 (vermelho)

🔵 Loja 2 (azul)

🟢 Loja 3 (verde)

🟠 Loja 4 (laranja)

📌 Sobre os dados:
As localizações foram obtidas a partir das colunas "lat" e "lon" presentes no dataset, garantindo uma representação fiel das coordenadas reais registradas para cada pedido. Cada marcador representa a presença de uma loja com base nos dados analisados.

![image](https://github.com/user-attachments/assets/677b2cf1-f873-4326-b6e2-772a5fb0988d)

---

## 🧾 Recomendação Final: Venda da Loja 4

Após análise detalhada dos dados de desempenho das quatro unidades da Alura Store, conclui-se que a **Loja 4 é a mais indicada para ser vendida**. Abaixo estão os principais fatores que fundamentam essa decisão:

---

### 📉 1. Menor Faturamento Total  
A Loja 4 registrou o **menor faturamento entre todas as unidades**, totalizando **R$ 1.384.497,58**.

> Esta métrica é crítica, pois impacta diretamente a **lucratividade** e **viabilidade financeira** da operação.

---

### 🎯 2. Desempenho em Categorias de Produto  
Embora tenha bons resultados em categorias populares como **móveis**, a Loja 4 apresenta:

- **Menores vendas absolutas** de instrumentos musicais.  
- **Desempenho mediano** em diversas outras categorias.

> Isso pode indicar um **mix de produtos pouco atrativo** ou **mal adaptado à demanda regional**.

---

### 💬 3. Avaliação dos Clientes  
A nota média de avaliação da Loja 4 foi de **4.00**, inferior à:

- Loja 3: **4.05**  
- Loja 2: **4.04**

> Pequenas variações em avaliação refletem **diferenças significativas em retenção e fidelização de clientes** quando analisadas em larga escala.

---

### 🚚 4. Eficiência Logística  
A Loja 4 apresentou:

- **Menor custo de frete médio**  
- **Menor valor total de frete**

> Apesar do bom desempenho logístico, **isso não compensa os baixos resultados comerciais e de satisfação**.

---

### 🗺️ 5. Localização e Redundância  
A análise geoespacial revelou **sobreposição geográfica** com outras unidades, incluindo **repetição de coordenadas em cidades do interior de SP e MG**.

> Indica **ineficiência territorial** e **limitação na expansão de mercado**.

---

### ✅ Conclusão  
A **Loja 4 combina os piores indicadores de desempenho geral**, com:

- Faturamento reduzido  
- Baixa diversificação em vendas  
- Avaliação inferior  
- Redundância geográfica

> Apesar da logística enxuta, **não há justificativa estratégica para sua permanência**.  
**Recomenda-se sua venda**, permitindo ao Senhor João **realocar capital para empreendimentos com maior retorno e escalabilidade**.

## 🛠️ Tecnologias Utilizadas

Este projeto foi desenvolvido utilizando o **Google Colab**, um ambiente baseado em **Jupyter Notebook** com execução em nuvem.  
As bibliotecas utilizadas na análise incluem:

- **Python**: Linguagem principal utilizada para manipulação e visualização dos dados.
- **pandas**: Tratamento e análise de dados tabulares.
- **matplotlib**: Geração de gráficos estáticos.
- **folium**: Visualização geográfica.

---

📌 **Projeto desenvolvido para fins de estudo e demonstração de habilidades em análise exploratória de dados.**

