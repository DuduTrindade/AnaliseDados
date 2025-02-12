


## Introdução

<div style="display: inline-block; width: 100%; style="text-align: justify; font-size: 16px; font-family: Arial, sans-serif;">
<p style="text-align: justify; font-size: 16px; font-family: Arial, sans-serif;">
No mundo atual, onde os dados são considerados o novo petróleo, a capacidade de analisar as informações de maneira eficaz tornou-se essencial para as empresas que buscam se manter competitivas. A análise de dados de vendas é uma das áreas mais críticas, pois permite entender o comportamento do consumidor, identificar tendências de mercado e otimizar estratégias de vendas. Neste contexto, o SQL (Structured Query Language) se destaca como uma ferramenta poderosa para a análise de dados. Utilizada amplamente em sistemas de gerenciamento de banco de dados, a linguagem SQL permite consultar, manipular e extrair informações valiosas de grandes conjuntos de dados de maneira rápida e eficiente.

Analisarei dados de uma empresa fictícia de varejo que atua no segmento de eletrônicos, oferecendo desde dispositivos móveis e computadores até acessórios tecnológicos de ponta. Com presença em múltiplos continentes e operando tanto online quanto em lojas físicas, a empresa atende uma base diversificada de clientes: indivíduos, pequenas e grandes 	empresas. 

Ao longo desta análise, utilizarei SQL para explorar e interpretar dados de vendas, buscando respostas para perguntas estratégicas que podem orientar decisões empresariais. Desde a identificação dos produtos mais vendidos até a análise das taxas de devolução por loja, cada consulta SQL nos fornecerá insights que podem ser transformados em ações concretas para melhorar o desempenho da empresa.. Retornar ao [início.](https://github.com/DuduTrindade/AnaliseDados/tree/in?tab=readme-ov-file#todos-os-meus-projetos)
</p>
</div>

## Estrutura do Conjunto de Dados

O conjunto de dados é composto pelas seguintes tabelas:
*	**Clientes**: Contém informações demográficas dos clientes.
*	**Devoluções**: Registra as devoluções de produtos.
*	**Itens**: Detalha os itens vendidos em cada venda.
*	**Localidades**: Armazena informações geográficas das lojas.
*	**Lojas**: Contém informações sobre as lojas.
*	**Produtos**: Armazena informações sobre os produtos vendidos.
*	**Vendas**: Registra as vendas realizadas.

Nesta análise estou utilizando o Sistema de Gerenciamento de Banco de Dados (SGBD) SQL Server da Microsoft. Abaixo segue a imagem do Diagrama Entidade Relacionamento e seus respectivos relacionamentos.

<div align="center" style="display: inline-block;">
	<img  width="600" src="https://github.com/DuduTrindade/AnaliseDados/blob/main/Projetos/Projeto%2001%20-%20An%C3%A1lise%20de%20Vendas%20com%20SQL/img/DIAGRAMA%20VENDAS.png">
</div>


## Análise Explorativa dos Dados

Nesta etapa, realizaremos uma análise exploratória das tabelas disponíveis para entender como os dados estão organizados e identificar as informações mais relevantes. Essa análise é fundamental para obter insights e preparar o terreno para futuras análises mais aprofundadas.

### Tabela de Clientes

<div style="display: inline-block;">
	<img width="800" src="https://github.com/DuduTrindade/AnaliseDados/blob/main/Projetos/Projeto%2001%20-%20An%C3%A1lise%20de%20Vendas%20com%20SQL/img/TABELAS%20CLIENTES.png">
</div>


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

<div style="display: inline-block;">
	<img width="500" src="https://github.com/DuduTrindade/AnaliseDados/blob/main/Projetos/Projeto%2001%20-%20An%C3%A1lise%20de%20Vendas%20com%20SQL/img/TABELA%20DEVOLU%C3%87%C3%95ES.png">
</div>


Descrição: Esta tabela registra as devoluções de produtos. Segue abaixo os campos:

*	**Data_devolucao**: Data em que a devolução foi realizada.
*	**Id_Loja**: Identificador da loja onde a devolução foi realizada.
*	**SKU**: Código do produto devolvido.
*	**Qtde_Devolvida**: Quantidade de itens devolvidos.
*	**Motivo_Devolucao**: Motivo pelo qual o produto foi devolvido.
*	**Id_Devolução**: Identificador da devolução

### Tabela de Itens

<div style="display: inline-block;">
	<img width="300" src="https://github.com/DuduTrindade/AnaliseDados/blob/main/Projetos/Projeto%2001%20-%20An%C3%A1lise%20de%20Vendas%20com%20SQL/img/TABELA%20ITENS.png">
</div>




Descrição: Esta tabela detalha os itens vendidos em cada transação. Segue abaixo os campos:

*	**Id_item**: Identificador único de cada item vendido.
*	**Id_venda**: Identificador da venda associada ao item.
*	**SKU**: Código do produto.
*	**Qtde_vendida**: Quantidade vendida do item.

### Tabela de Localidades

<div style="display: inline-block;">
	<img width="300" src="https://github.com/DuduTrindade/AnaliseDados/blob/main/Projetos/Projeto%2001%20-%20An%C3%A1lise%20de%20Vendas%20com%20SQL/img/TABELA%20LOCALIDADES.png">
</div>



Descrição: Armazena informações geográficas. Segue abaixo os campos:

*	**Id_localidade**: Identificador único de cada localidade
*	**País**: nome do país
*	**Continente**: nome do continente

### Tabela de Lojas

<div style="display: inline-block;">
	<img width="650" src="https://github.com/DuduTrindade/AnaliseDados/blob/main/Projetos/Projeto%2001%20-%20An%C3%A1lise%20de%20Vendas%20com%20SQL/img/TABELA%20LOJAS.png">
</div>



Descrição: Esta tabela contém informações detalhadas sobre as lojas da empresa, essenciais para a análise de desempenho e gestão operacional. Segue os campos:

*	**Id_loja**: Identificador único de cada loja.
*	**Nome_loja**: Nome da loja.
*	**Quantidade_Colaboradores**: Número de colaboradores que trabalham na loja.
*	**Tipo**: Tipo de loja (por exemplo, física, online ou híbrida).
*	**Id_localidade**: Identificador da localidade onde a loja está situada, facilitando a correlação com dados geográficos.
*	**Gerente_Loja**: Nome do gerente responsável pela loja.
*	**Documento_Gerente**: Documento de identificação do gerente da loja.


### Tabela de Produtos

<div style="display: inline-block;">
	<img width="650" src="https://github.com/DuduTrindade/AnaliseDados/blob/main/Projetos/Projeto%2001%20-%20An%C3%A1lise%20de%20Vendas%20com%20SQL/img/TABELA%20PRODUTOS.png">
</div>



Descrição: Armazena informações sobre os produtos vendidos. Segue abaixo os campos: 

*	**SKU**: Código único do produto, utilizado para identificação e rastreamento.
*	**Produto**: Nome do produto.
*	**Marca**: Marca do produto.
*	**Tipo_Produto**: Categoria ou tipo do produto.
*	**Preco_Unitario**: Preço unitário do produto.
*	**Custo_Unitario**: Custo unitário do produto.
*	**Observação**: Campo para observações adicionais sobre o produto.

### Tabela de Vendas

<div style="display: inline-block;">
	<img width="300" src="https://github.com/DuduTrindade/AnaliseDados/blob/main/Projetos/Projeto%2001%20-%20An%C3%A1lise%20de%20Vendas%20com%20SQL/img/TABELA%20VENDAS.png">
</div>



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


### Análises


> 📝**Pergunta 1: Qual é a distribuição de clientes por gênero em cada faixa etária?**

~~~SQL
-- CTE para calcular qual é a distribuição de clientes por gênero em cada faixa etária
WITH CTE_Distribuicao_Genero (Genero, Faixa_Etaria)
AS
(
	SELECT 
		Genero,
		-- Calcula a faixa etária com base na diferença de anos entre a data de nascimento e a data atual.
		CASE 
			WHEN  DATEDIFF(YEAR, Data_Nascimento, GETDATE()) <= 17 THEN 1
			WHEN  DATEDIFF(YEAR, Data_Nascimento, GETDATE()) BETWEEN 18 AND 25 THEN 2
			WHEN  DATEDIFF(YEAR, Data_Nascimento, GETDATE()) BETWEEN 26 AND 35 THEN 3
			WHEN  DATEDIFF(YEAR, Data_Nascimento, GETDATE()) BETWEEN 36 AND 45 THEN 4
			WHEN  DATEDIFF(YEAR, Data_Nascimento, GETDATE()) BETWEEN 46 AND 55 THEN 5
			WHEN  DATEDIFF(YEAR, Data_Nascimento, GETDATE()) BETWEEN 56 AND 65 THEN 6
			ELSE  7
		END Faixa_Etaria
	FROM Clientes
)
SELECT
	Genero,
	CASE
		WHEN Faixa_Etaria = 1 THEN '0-17'  -- Faixa 1 corresponde ao intervalo '0-17 anos'.
		WHEN Faixa_Etaria = 2 THEN '18-25' -- Faixa 2 corresponde ao intervalo '18-25 anos'.
		WHEN Faixa_Etaria = 3 THEN '26-35' -- Faixa 3 corresponde ao intervalo '26-35 anos'.
		WHEN Faixa_Etaria = 4 THEN '36-45' -- Faixa 4 corresponde ao intervalo '36-45 anos'.
		WHEN Faixa_Etaria = 5 THEN '46-55' -- Faixa 5 corresponde ao intervalo '46-55 anos'.
		WHEN Faixa_Etaria = 6 THEN '56-65' -- Faixa 6 corresponde ao intervalo '56-65 anos'.
		ELSE '66+'					-- Faixa 7 corresponde ao intervalo '66 anos ou mais'.
	END	Faixa_Etaria,
	COUNT(Faixa_Etaria) AS Total_Genero
FROM CTE_Distribuicao_Genero
GROUP BY Faixa_Etaria, Genero
ORDER BY Faixa_Etaria, Total_Genero DESC;
~~~

<div style="display: inline-block;">
	<img width="300" src="https://github.com/DuduTrindade/AnaliseDados/blob/main/Projetos/Projeto%2001%20-%20An%C3%A1lise%20de%20Vendas%20com%20SQL/img/Resultado%20analise%20cliente.png">
	<img width="700" src="https://github.com/DuduTrindade/AnaliseDados/blob/main/Projetos/Projeto%2001%20-%20An%C3%A1lise%20de%20Vendas%20com%20SQL/img/GRAFICO%20CLIENTES.png">
</div> 
<br>
Observando o gráfico percebe-se que a faixa etária de 26-35 possui um número clientes de 6003 que representa um total de 33% do total geral, sendo que o percentual masculino é de 17% e feminino de 16%. A faixa de 36-45 possui um número de 5230 de clientes representando 29% do total geral, sendo 15% masculino e 14% feminino. A faixa etária de 46-55 tem soma um total de 3057 com percentual de 17% do total geral, sendo que 9% são femininos e 8% masculinos. Essas três faixas representam um total de 79% dos clientes.
<br><br>


> 📝**Pergunta 2: Qual é a distribuição Distribuição Geográfica dos Clientes?**

~~~sql
SELECT 
	L.Continente,	
	L.País,	
	COUNT(C.ID_Cliente) AS Total_Clientes,
	SUM(COUNT(C.ID_Cliente)) OVER(PARTITION BY L.Continente) AS Total_Continente
FROM Clientes C INNER JOIN Localidades L ON C.Id_Localidade = L.Id_Localidade
GROUP BY L.País, L.Continente
ORDER BY L.Continente, Total_Clientes DESC;
~~~

<div align="center" style="display: inline-block;">
	<img width="350" src="https://github.com/DuduTrindade/AnaliseDados/blob/main/Projetos/Projeto%2001%20-%20An%C3%A1lise%20de%20Vendas%20com%20SQL/img/distrib.%20clientes%20.png"><br>
	<img width="800" src="https://github.com/DuduTrindade/AnaliseDados/blob/main/Projetos/Projeto%2001%20-%20An%C3%A1lise%20de%20Vendas%20com%20SQL/img/analise_cliente.png">
</div> 
<br>









<br><br><br><br>

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















