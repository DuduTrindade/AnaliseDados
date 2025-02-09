![](https://github.com/DuduTrindade/AnaliseDados/blob/main/Projetos/Projeto%2001%20-%20An%C3%A1lise%20de%20Vendas%20com%20SQL/img/AN%C3%81LISE%20DE%20VENDAS.png)


## Introdução
No mundo atual, onde os dados são considerados o novo petróleo, a capacidade de analisar as informações de maneira eficaz tornou-se essencial para as empresas que 
buscam se manter competitivas. A análise de dados de vendas é uma das áreas mais críticas, pois permite entender o comportamento do consumidor, identificar tendências 
de mercado e otimizar estratégias de vendas.

Neste contexto, o SQL (Structured Query Language) se destaca como uma ferramenta poderosa para a análise de dados. Utilizada amplamente em sistemas de gerenciamento de banco
 de dados, a linguagem SQL permite consultar, manipular e extrair informações valiosas de grandes conjuntos de dados de maneira rápida e eficiente.

Analisarei dados de uma empresa fictícia de varejo que atua no segmento de eletrônicos, oferecendo desde dispositivos móveis e computadores até acessórios tecnológicos de ponta.
Com presença em múltiplos continentes e operando tanto online quanto em lojas físicas, a empresa atende uma base diversificada de clientes: indivíduos, pequenas e grandes 
empresas. 

Ao longo desta análise, utilizarei SQL para explorar e interpretar dados de vendas, buscando respostas para perguntas estratégicas que podem orientar decisões empresariais.
Desde a identificação dos produtos mais vendidos até a análise das taxas de devolução por loja, cada consulta SQL nos fornecerá insights que podem ser transformados em ações
concretas para melhorar o desempenho da empresa.. Retornar ao [início.](https://github.com/DuduTrindade/AnaliseDados/tree/main?tab=readme-ov-file#todos-os-meus-projetos)


## Estrutura do Conjunto de Dados

O conjunto de dados é composto pelas seguintes tabelas:
*	**Clientes**: Contém informações demográficas dos clientes.
*	**Devoluções**: Registra as devoluções de produtos.
*	**Itens**: Detalha os itens vendidos em cada venda.
*	**Localidades**: Armazena informações geográficas das lojas.
*	**Lojas**: Contém informações sobre as lojas.
*	**Produtos**: Armazena informações sobre os produtos vendidos.
*	**Vendas**: Registra as vendas realizadas.

Nesta análise estou utilizando o Sistema de Gerenciamento de Banco de Dados (SGBD) SQL Server da Microsoft. Abaixo segue o diagrama do banco chamado **Analise_Vendas** e seus 
respectivos relacionamentos.

![](https://github.com/DuduTrindade/AnaliseDados/blob/main/Projetos/Projeto%2001%20-%20An%C3%A1lise%20de%20Vendas%20com%20SQL/img/SCHEMA.png)
![](https://github.com/DuduTrindade/AnaliseDados/blob/main/Projetos/Projeto%2001%20-%20An%C3%A1lise%20de%20Vendas%20com%20SQL/img/DIAGRAMA%20VENDAS.png)

## Análise Explorativa dos Dados

Nesta etapa, realizaremos uma análise exploratória das tabelas disponíveis para entender como os dados estão organizados e identificar as informações mais relevantes. Essa 
análise é fundamental para obter insights e preparar o terreno para futuras análises mais aprofundadas.

### Tabela de Clientes
![](https://github.com/DuduTrindade/AnaliseDados/blob/main/Projetos/Projeto%2001%20-%20An%C3%A1lise%20de%20Vendas%20com%20SQL/img/TABELAS%20CLIENTES.png) 

Descrição: Esta tabela contém informações dos clientes. Segue abaixo os campos:

*	**Id_cliente**: Identificador único do cliente.
*	**Primeiro_nome**: Primeiro nome do cliente.
*	**Sobrenome**: Sobrenome do cliente.
*	**Email**: Endereço de e-mail do cliente.
*	**Gênero**: Gênero do cliente.
*	**Data_nascimento**: Data de nascimento do cliente.
*	**Estado_civil**: Estado civil do cliente (solteiro, casado, etc.).
*	**Num_filhos**: Número de filhos do cliente.
*	**Documento**: Documento de identificação do cliente.
*	**Id_localidade**: Identificador da localidade do cliente.

### Tabela de Devoluções
![](https://github.com/DuduTrindade/AnaliseDados/blob/main/Projetos/Projeto%2001%20-%20An%C3%A1lise%20de%20Vendas%20com%20SQL/img/TABELA%20DEVOLU%C3%87%C3%95ES.png)

Descrição: Esta tabela registra as devoluções de produtos. Segue abaixo os campos:

*	**Data_devolucao**: Data em que a devolução foi realizada.
*	**Id_Loja**: Identificador da loja onde a devolução foi realizada.
*	**SKU**: Código do produto devolvido.
*	**Qtde_Devolvida**: Quantidade de itens devolvidos.
*	**Motivo_Devolucao**: Motivo pelo qual o produto foi devolvido.
*	**Id_Devolução**: Identificador da devolução

### Tabela de Itens
![](https://github.com/DuduTrindade/AnaliseDados/blob/main/Projetos/Projeto%2001%20-%20An%C3%A1lise%20de%20Vendas%20com%20SQL/img/TABELA%20ITENS.png)

Descrição: Esta tabela detalha os itens vendidos em cada transação. Segue abaixo os campos:

*	**Id_item**: Identificador único de cada item vendido.
*	**Id_venda**: Identificador da venda associada ao item.
*	**SKU**: Código do produto.
*	**Qtde_vendida**: Quantidade vendida do item.

### Tabela de Localidades
![](https://github.com/DuduTrindade/AnaliseDados/blob/main/Projetos/Projeto%2001%20-%20An%C3%A1lise%20de%20Vendas%20com%20SQL/img/TABELA%20LOCALIDADES.png)

Descrição: Armazena informações geográficas. Segue abaixo os campos:

*	**Id_localidade**: Identificador único de cada localidade
*	**País**: nome do país
*	**Continente**: nome do continente

### Tabela de Lojas
![](https://github.com/DuduTrindade/AnaliseDados/blob/main/Projetos/Projeto%2001%20-%20An%C3%A1lise%20de%20Vendas%20com%20SQL/img/TABELA%20LOJAS.png)

Descrição: Esta tabela contém informações detalhadas sobre as lojas da empresa, essenciais para a análise de desempenho e gestão operacional. Segue os campos:

*	**Id_loja**: Identificador único de cada loja.
*	**Nome_loja**: Nome da loja.
*	**Quantidade_Colaboradores**: Número de colaboradores que trabalham na loja.
*	**Tipo**: Tipo de loja (por exemplo, física, online ou híbrida).
*	**Id_localidade**: Identificador da localidade onde a loja está situada, facilitando a correlação com dados geográficos.
*	**Gerente_Loja**: Nome do gerente responsável pela loja.
*	**Documento_Gerente**: Documento de identificação do gerente da loja.


### Tabela de Produtos
![](https://github.com/DuduTrindade/AnaliseDados/blob/main/Projetos/Projeto%2001%20-%20An%C3%A1lise%20de%20Vendas%20com%20SQL/img/TABELA%20PRODUTOS.png)

Descrição: Armazena informações sobre os produtos vendidos. Segue abaixo os campos: 

*	**SKU**: Código único do produto, utilizado para identificação e rastreamento.
*	**Produto**: Nome do produto.
*	**Marca**: Marca do produto.
*	**Tipo_Produto**: Categoria ou tipo do produto.
*	**Preco_Unitario**: Preço unitário do produto.
*	**Custo_Unitario**: Custo unitário do produto.
*	**Observação**: Campo para observações adicionais sobre o produto.

### Tabela de Vendas
![](https://github.com/DuduTrindade/AnaliseDados/blob/main/Projetos/Projeto%2001%20-%20An%C3%A1lise%20de%20Vendas%20com%20SQL/img/TABELA%20VENDAS.png)

Descrição: Esta tabela registra todas as vendas realizadas, fornecendo um histórico completo das transações de venda.

*	**Id_venda**: Identificador único de cada venda.
*	**Data_venda**: Data em que a venda foi realizada.
*	**Id_cliente**: Identificador do cliente que realizou a compra.
*	**Id_loja**: Identificador da loja onde a venda foi efetuada.


### Perguntas Sugeridas

1) **Distribuição de Clientes por Gênero e Faixa Etária**: Segmentar os clientes por gênero e faixa etária para entender a proporção dos dados.
2) **Distribuição Geográfica de Clientes**: Relacionar a tabela de Clientes com a tabela de Localidades para entender a distribuição geográfica de clientes por País e Continente
3) **Motivos de Devolução dos Produtos**: Analisar os principais motivos de devolução.
4) **Taxa de Devoluções**: Calcular a frequência de devoluções por produtos e lojas
5) **Produtos Mais Vendidos**: Identificar os produtos mais vendidos.
6) **Análise Temporal de Vendas**: Calcular a quantidade vendida por mês, trimestre e ano.
7) **Vendas por Loja**: Analisar a distribuição das vendas por loja.
8) **Vendas por Cliente**: Verificar a distribuição das vendas por cliente.
9) **Distribuição Geográfica das Lojas**: Criar um mapa de distribuição das lojas por estado e cidade.
10) **Concentração de Lojas**: Identificar regiões com maior concentração de lojas.
11) **Categorias de Produtos**: Analisar a distribuição dos produtos por categoria.


### Análise 



> 📝**Pergunta 1: Qual é a distribuição de clientes por gênero em cada faixa etária?**
<div  style="display: inline-block">
	<img align="Left" width='650' height = '450' src="https://github.com/DuduTrindade/AnaliseDados/blob/main/Projetos/Projeto%2001%20-%20An%C3%A1lise%20de%20Vendas%20com%20SQL/img/query%20clientes.png"/>
	<img align="Right" width='300' height = '250' src="https://github.com/DuduTrindade/AnaliseDados/blob/main/Projetos/Projeto%2001%20-%20An%C3%A1lise%20de%20Vendas%20com%20SQL/img/Resultado%20analise%20cliente.png"/><br>
	<img align="center" width='600' height = '450' src="https://github.com/DuduTrindade/AnaliseDados/blob/main/Projetos/Projeto%2001%20-%20An%C3%A1lise%20de%20Vendas%20com%20SQL/img/GRAFICO%20CLIENTES.png"/>
</div>

<br>
<br>






> 📝**Pergunta 4: Qual é o nível educacional mais comum entre os clientes?**
~~~SQL
SELECT 
	Nivel_Escolar AS Nivel_Educacional,
	COUNT(*) AS QTDE
FROM Clientes
GROUP BY Nivel_Escolar
ORDER BY QTDE DESC; 
~~~

![](https://github.com/DuduTrindade/Analises_de_Dados/blob/main/Projetos/Projeto%2001/img/pergunta%2004.png)

**Insight**: Entender o nível educacional pode ajudar a criar campanhas de marketing mais eficazes e ajustar a linguagem e o tom das comunicações.

### Análise de Produtos e Vendas

> 📝**Pergunta 5: Quais são os produtos mais vendidos?**

~~~SQL
SELECT TOP 10
	P.Produto AS Nome,
	COUNT(I.Qtd_Vendida) AS Qtde_Vendas,
	SUM(I.Qtd_Vendida * P.Preço_Unitario) AS Total
 FROM Produtos P INNER JOIN Itens I ON P.SKU = I.SKU
GROUP BY P.Produto	
ORDER BY Total DESC;
~~~
![](https://github.com/DuduTrindade/Analises_de_Dados/blob/main/Projetos/Projeto%2001/img/pergunta%2005.png)

**Insight**: Identificar os produtos que têm maior demanda para otimizar o estoque e promover os itens mais populares.


> 📝**Pergunta 6: Qual é a receita total por marca?**

~~~SQL
SELECT 
	P.Marca,
	SUM(P.Preço_Unitario * I.Qtd_Vendida) AS [Total Vendido]
FROM Produtos P INNER JOIN Itens I ON P.SKU = I.SKU
GROUP BY P.Marca
ORDER BY 2 DESC;	
~~~

![](https://github.com/DuduTrindade/Analises_de_Dados/blob/main/Projetos/Projeto%2001/img/pergunta%2006.png)


**Insight**: Calcular a receita total gerada por cada marca para identificar os produtos mais lucrativos.


> 📝**Pergunta 7: Qual é a receita média por venda?**

~~~SQL
SELECT
 -- Calcula a média da receita total de cada venda (Total_Vendas), obtida na subconsulta.
	AVG(Total_Vendas) AS Receita_Média
FROM (
-- Subconsulta para calcular a receita total de cada venda
	SELECT 
		V.Id_Venda,
		SUM(P.Preço_Unitario * I.Qtd_Vendida) AS Total_Vendas
	FROM Vendas V 
	INNER JOIN Itens I ON V.Id_Venda = I.Id_Venda
	INNER JOIN Produtos P ON P.SKU = I.SKU
	GROUP BY V.Id_Venda
) AS Receita_Vendas_Media;
~~~

![](https://github.com/DuduTrindade/Analises_de_Dados/blob/main/Projetos/Projeto%2001/img/pergunta%2007.png)

**Insight**: Calcular a receita média por venda ajuda a avaliar o ticket médio e otimizar estratégias de precificação.


> 📝**Pergunta 8: Quais produtos têm a maior margem de lucro?**

~~~SQL
SELECT 
	Produto,
	Preço_unitario,
	Custo_Unitario,
	(Preço_unitario - Custo_Unitario) AS 'Margem_Lucro(R$)',
	((Preço_unitario - Custo_Unitario) / Preço_unitario) * 100 AS 'Margem_Lucro(%)'
FROM PRODUTOS
WHERE ((Preço_unitario - Custo_Unitario) / Preço_unitario) * 100 >= 80
ORDER BY 5 DESC;
~~~

![](https://github.com/DuduTrindade/Analises_de_Dados/blob/main/Projetos/Projeto%2001/img/pergunta%2008.png)


**Insight**: Identificar produtos com maior margem de lucro pode ajudar a focar em produtos mais rentáveis.

### Análise de Devoluções

> 📝**Pergunta 9: Qual é o motivo de devolução mais comum?**

~~~SQL
SELECT 
	Motivo_Devolucao,
	COUNT(*) AS Qtde_Totais_Devolucao
FROM Devolucoes
GROUP BY Motivo_Devolucao
ORDER BY Qtde_Totais_Devolucao DESC;
~~~
![](https://github.com/DuduTrindade/Analises_de_Dados/blob/main/Projetos/Projeto%2001/img/pergunta%2009.png)

**Insight**: Analisar os motivos das devoluções para identificar problemas comuns com produtos ou processos de venda.

> 📝**Pergunta 10: Quais produtos tem as maiores quantidades de devoluções?**

~~~SQL
SELECT TOP 20
	P.Produto,
	COUNT(D.Qtd_Devolvida) AS Quant_Devolucoes
FROM Devolucoes D INNER JOIN Produtos P ON D.SKU = P.SKU
GROUP BY P.Produto
ORDER BY Quant_Devolucoes DESC;
~~~

![](https://github.com/DuduTrindade/Analises_de_Dados/blob/main/Projetos/Projeto%2001/img/pergunta%2010.png)

**Insight**: Identificar produtos que são frequentemente devolvidos, o que pode indicar problemas de qualidade ou expectativas dos clientes.

> 📝**Pergunta 11: Quais são as maiores taxas de devoluções por produto?**

~~~SQL
-- -- CTE para calcular o total de devoluções por produto
WITH Devolucoes_Totais AS (
	SELECT
		D.SKU,
		SUM(D.Qtd_Devolvida) AS Totais_Devolucao
	FROM Devolucoes D 
	GROUP BY D.SKU
),

-- CTE para calcular o total de vendas por produto
Vendas_Totais AS (
	SELECT
		I.SKU,
		SUM(I.Qtd_Vendida) AS Total_Vendido
	FROM Itens I INNER JOIN Vendas V ON V.Id_Venda = I.Id_Venda
	GROUP BY I.SKU
)

---- Seleção principal das 20 produtos com a maior taxa de devolução
SELECT TOP 20
	P.Produto,
	VT.Total_Vendido,
	DT.Totais_Devolucao,
	(SUM(DT.Totais_Devolucao) * 100.0 / SUM(VT.Total_Vendido)) AS [Taxa_Devolucao%]
FROM Produtos P 
INNER JOIN Vendas_Totais VT ON P.SKU = VT.SKU
INNER JOIN Devolucoes_Totais DT ON DT.SKU = P.SKU
GROUP BY P.Produto,VT.Total_Vendido, DT.Totais_Devolucao
ORDER BY [Taxa_Devolucao%] DESC;
~~~
![](https://github.com/DuduTrindade/Analises_de_Dados/blob/main/Projetos/Projeto%2001/img/pergunta%2011.png)

**Insight**: Calcular a taxa de devolução pode ajudar a identificar problemas com produtos específicos.

> 📝**Pergunta 12: Qual loja tem a maior taxa de devoluções?**

~~~SQL
-- CTE para calcular o total de devoluções por loja
WITH Devolucoes_Totais AS (
	SELECT
		D.ID_Loja,
		SUM(D.Qtd_Devolvida) AS Totais_Lojas_Devolucao
	FROM Devolucoes D 
	GROUP BY D.ID_Loja
),

-- CTE para calcular o total de vendas por loja
Vendas_Totais AS (
	SELECT
		V.ID_Loja,
		SUM(I.Qtd_Vendida) AS Total_Lojas_Vendas
	FROM Itens I INNER JOIN Vendas V ON V.Id_Venda = I.Id_Venda
	GROUP BY V.ID_Loja
)

-- Seleção principal das 20 lojas com a maior taxa de devolução
SELECT TOP 20
	L.ID_Loja,
	Total_Lojas_Vendas,
	Totais_Lojas_Devolucao,
	DT.Totais_Lojas_Devolucao * 100.0 / VT.Total_Lojas_Vendas AS [Taxa_Devolucao_por_Loja%]
FROM Lojas L
INNER JOIN Vendas_Totais VT ON VT.ID_Loja = L.ID_Loja
INNER JOIN Devolucoes_Totais DT ON DT.ID_Loja = L.ID_Loja
GROUP BY L.ID_Loja, Totais_Lojas_Devolucao, Total_Lojas_Vendas
ORDER BY [Taxa_Devolucao_por_Loja%] DESC;
~~~

![](https://github.com/DuduTrindade/Analises_de_Dados/blob/main/Projetos/Projeto%2001/img/pergunta%2012.png)

**Insight**: Identificar lojas com altas taxas de devolução pode apontar para problemas específicos de atendimento ou produto.


### Análise Geográfica

>📝 **Pergunta 13: Qual é a receita total de vendas por país ao longo dos anos?**

~~~SQL
-- CTE (Common Table Expression) para agregação de vendas por ano e país
WITH Vendas_agregadas AS
(
	SELECT 
		YEAR(V.Data_Venda) AS Ano,
		LC.País,

		-- Soma o preço unitário dos produtos vendidos para calcular o total de vendas no ano
		SUM(P.Preço_Unitario) AS Total_Vendas_Ano
	FROM Vendas V
	INNER JOIN Itens I ON V.Id_Venda = I.Id_Venda
	INNER JOIN Lojas L ON L.ID_Loja = V.ID_Loja
	INNER JOIN Localidades LC ON LC.ID_Localidade = L.id_Localidade
	INNER JOIN Produtos P ON P.SKU = I.SKU
	GROUP BY YEAR(V.Data_Venda), LC.País
	
)
-- Seleciona os resultados da CTE para realizar cálculos adicionais
SELECT
	Ano,
	País,
	Total_Vendas_Ano AS Total_Ano_Atual,

	-- Função LAG usada para pegar o total de vendas do ano anterior
	LAG(Total_Vendas_Ano, 1, Total_Vendas_Ano) OVER (PARTITION BY País ORDER BY Ano) AS Total_Ano_Anterior,

	-- Cálculo do crescimento percentual ano a ano (YoY)
	-- (Total_Ano_Atual / Total_Ano_Anterior) - 1 indica a variação percentual de crescimento
	(Total_Vendas_Ano / LAG(Total_Vendas_Ano, 1, Total_Vendas_Ano) OVER (PARTITION BY País ORDER BY Ano) -1) AS Crescimento_Percentual
FROM Vendas_agregadas
ORDER BY Ano, País
~~~

![](https://github.com/DuduTrindade/Analises_de_Dados/blob/main/Projetos/Projeto%2001/img/pergunta%2013.jpg)

**Insight**: Entender a receita total de vendas por país ao longo dos anos pode ajudar a identificar quais países 
estão contribuindo mais para a receita e quais precisam de estratégias de marketing mais focadas.


> 📝 **Pergunta 14: Qual é a média de vendas mensais por continente?**

~~~SQL
-- Seleciona o continente e a média mensal de vendas
SELECT
	Mensal_Vendas.Continente, -- Seleciona o continente calculado na subconsulta
	AVG(Mensal_Vendas.Total_Vendas_Mensal) AS Media_Mensal_Vendas -- Calcula a média de vendas mensais por continente
FROM (

	-- Subconsulta para calcular o total de vendas mensais por continente
	SELECT 
		LC.Continente,
		YEAR(V.Data_Venda) AS Ano,
		MONTH(V.Data_Venda) AS Mes,
		SUM(I.Qtd_Vendida * P.Preço_Unitario) AS Total_Vendas_Mensal
	FROM Vendas V 
	INNER JOIN Itens I ON V.Id_Venda = I.Id_Venda
	INNER JOIN Produtos P ON P.SKU = I.SKU
	INNER JOIN Lojas L ON L.ID_Loja = V.ID_Loja
	INNER JOIN Localidades LC ON LC.ID_Localidade = L.id_Localidade
	GROUP BY LC.Continente, YEAR(V.Data_Venda), MONTH(V.Data_Venda) 
) AS Mensal_Vendas 
GROUP BY Mensal_Vendas.Continente
~~~

![](https://github.com/DuduTrindade/Analises_de_Dados/blob/main/Projetos/Projeto%2001/img/pergunta%2014.png)

**Insight**: Avaliar a média de vendas mensais por continente pode ajudar a identificar padrões sazonais em diferentes regiões e ajustar as operações de acordo.


> 📝 **Pergunta 15: Qual é a média de devoluções por país durante os anos?**

~~~SQL
WITH Media_Devolucao_Pais AS
(
	SELECT 
		LC.País AS Pais,
		YEAR(D.Data_Devolucao) AS Ano,
		SUM(D.Qtd_Devolvida) AS Qtde_Devolvida
	FROM Devolucoes D
	INNER JOIN Lojas L ON L.ID_Loja = D.ID_Loja
	INNER JOIN Localidades LC ON LC.ID_Localidade = L.id_Localidade
	GROUP BY LC.País, YEAR(D.Data_Devolucao)
)

SELECT
	MDP.Pais,
	AVG(MDP.Qtde_Devolvida) AS Media_Devolucoes
FROM Media_Devolucao_Pais MDP
GROUP BY MDP.Pais
~~~
![](https://github.com/DuduTrindade/Analises_de_Dados/blob/main/Projetos/Projeto%2001/img/pergunta%2015.png)

**Insight**: Entender a média de devoluções por país pode ajudar a identificar possíveis problemas de qualidade ou de atendimento ao cliente em determinadas regiões.

> 📝 **Pergunta 16: Qual é a receita total de vendas por continente e tipo de loja?**

~~~SQL
WITH Receita_Total_Continente AS
(
	SELECT
		LC.Continente,
		L.Tipo,
		SUM(I.Qtd_Vendida * P.Preço_Unitario)AS Total_Continente
	FROM Vendas V
	INNER JOIN Itens I ON I.Id_Venda = V.Id_Venda
	INNER JOIN Produtos P ON P.SKU = I.SKU
	INNER JOIN Lojas L ON L.ID_Loja = V.ID_Loja
	INNER JOIN Localidades LC ON LC.ID_Localidade = L.id_Localidade
	GROUP BY LC.Continente, L.Tipo
)
SELECT 
	 R.Continente,
	 R.Tipo,	 
	 FORMAT(R.Total_Continente,	'C0') AS Valor_Tipo_Loja,
	 FORMAT(SUM(R.Total_Continente) OVER(PARTITION BY R.Continente), 'C0') AS Total_Continente	
FROM Receita_Total_Continente R
~~~
![](https://github.com/DuduTrindade/Analises_de_Dados/blob/main/Projetos/Projeto%2001/img/pergunta%2016.png)

**Insight**: Analisar a receita total de vendas por continente e tipo de loja pode ajudar a identificar quais tipos de lojas são mais bem-sucedidos em diferentes regiões.


### Análise de Performance das Lojas

> 📝 **Pergunta 17: Qual loja tem o maior número de vendas?**

~~~SQL
SELECT TOP 1
	L.Nome_Loja,
	SUM(I.Qtd_Vendida) AS Qtde_Vendida
FROM LOJAS L 
INNER JOIN Vendas V ON V.ID_Loja = L.ID_Loja
INNER JOIN Itens I ON I.Id_Venda = V.Id_Venda
GROUP BY L.Nome_Loja
ORDER BY Qtde_Vendida DESC;
~~~

![](https://github.com/DuduTrindade/Analises_de_Dados/blob/main/Projetos/Projeto%2001/img/pergunta%2017.png)

**Insight**: Determinar qual loja é a mais ativa em termos de vendas para entender melhor o desempenho das diferentes localidades.


> 📝 **Pergunta 18: Qual loja tem a maior receita total?**

~~~SQL
SELECT TOP 1
	L.Nome_Loja,
	FORMAT(SUM(P.Preço_Unitario * I.Qtd_Vendida), 'C2') AS Faturamento
FROM LOJAS L 
INNER JOIN Vendas V ON V.ID_Loja = L.ID_Loja
INNER JOIN Itens I ON I.Id_Venda = V.Id_Venda
INNER JOIN Produtos P ON P.SKU = I.SKU
GROUP BY L.Nome_Loja
ORDER BY Faturamento DESC;
~~~
![](https://github.com/DuduTrindade/Analises_de_Dados/blob/main/Projetos/Projeto%2001/img/pergunta%2018.png)

**Insight**: Determinar qual loja gera mais receita pode ajudar a identificar melhores práticas e replicar em outras lojas.

> 📝 **Pergunta 19: Qual é o faturamento total das lojas físicas em comparação com as lojas online?**

~~~SQL
SELECT 
	L.Tipo AS Tipo_Loja,
	FORMAT(SUM(P.Preço_Unitario * I.Qtd_Vendida), 'C2') AS Faturamento
FROM LOJAS L 
INNER JOIN Vendas V ON V.ID_Loja = L.ID_Loja
INNER JOIN Itens I ON I.Id_Venda = V.Id_Venda
INNER JOIN Produtos P ON P.SKU = I.SKU
GROUP BY L.Tipo
ORDER BY SUM(P.Preço_Unitario * I.Qtd_Vendida) DESC;
~~~
![](https://github.com/DuduTrindade/Analises_de_Dados/blob/main/Projetos/Projeto%2001/img/pergunta%2019.png)

**Insight**: Essa pergunta oferece uma visão clara de como cada tipo de loja contribui para o faturamento total da
 empresa, permitindo identificar qual canal está gerando mais receita


## Conclusão 
O projeto de análise de dados da TechGlobal Solutions teve como objetivo otimizar as operações e maximizar a rentabilidade de uma empresa fictícia de varejo de eletrônicos. 
Através de técnicas avançadas de análise de dados utilizando SQL, foram exploradas várias áreas críticas para o negócio, como o comportamento dos clientes, desempenho de
produtos, devoluções e a performance regional das lojas.

A análise de dados revelou padrões de compra, identificou os produtos mais rentáveis e destacou aqueles com maior taxa de devoluções. Isso possibilitou que a 
empresa ajustasse seu portfólio, melhorasse a qualidade dos produtos e otimizasse as descrições e imagens nas plataformas de venda. Também foram observadas variações 
no desempenho entre as diferentes regiões, permitindo que a empresa realocasse recursos e ajustasse suas estratégias de marketing de forma mais eficaz.

Como resultado, as ações tomadas com base nos dados não apenas reduziram custos operacionais, mas também melhoraram a satisfação dos clientes, aumentaram a retenção e 
reduziram as devoluções. No geral, a análise de dados ajudou a TechGlobal Solutions a tomar decisões informadas e a se posicionar de forma competitiva no mercado, garantindo 
maior eficiência e melhores resultados financeiros a longo prazo.















