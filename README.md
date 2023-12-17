# Data Science Independent Project #1 – Watching the Stock Market

## Descrição
Este projeto foi desenvolvido como parte de um curso de consultas SQL na plataforma Codecademy. O objetivo era praticar habilidades de análise de dados utilizando consultas SQL para obter informações sobre o mercado de ações. O projeto abrangeu desde a obtenção dos dados até a realização de análises e visualizações relevantes. Durante o projeto, foram aplicados conceitos como seleção, filtragem, ordenação e agregação de dados para extrair insights valiosos do mercado de ações. Este projeto serviu como uma oportunidade para aprimorar as habilidades em SQL e adquirir experiência prática na análise de dados financeiros.

A primeira etapa do processo foi a coleta de dados de 5 ações. Utilizei o Google Finanças para escolher as ações. Escolhi as empresas Google, Meta, Tesla, Apple e Amazon. Os preços das ações foram coletados as 9h, 12h e 15h, entre os dias 11/12 e 15/12, para popular o banco de dados.

Utilizei o SQLite e o DB Browser for SQLite para manupilação e consulta do banco de dados.

<details>
    <summary>Clique para ver os dados inseridos na tabela.</summary>

        -GOOGL
			'GOOGL', 'Google', '2023-12-11 09:00:00', 132.29
			'GOOGL', 'Google', '2023-12-11 12:00:00', 132.24
			'GOOGL', 'Google', '2023-12-11 15:00:00', 132.85

			'GOOGL', 'Google', '2023-12-12 09:00:00', 131.87
			'GOOGL', 'Google', '2023-12-12 12:00:00', 132.22
			'GOOGL', 'Google', '2023-12-12 15:00:00', 132.20

			'GOOGL', 'Google', '2023-12-13 09:00:00', 133.43
			'GOOGL', 'Google', '2023-12-13 12:00:00', 132.01
			'GOOGL', 'Google', '2023-12-13 15:00:00', 132.85

			'GOOGL', 'Google', '2023-12-14 09:00:00', 133.39
			'GOOGL', 'Google', '2023-12-14 12:00:00', 131.22
			'GOOGL', 'Google', '2023-12-14 15:00:00', 131.38

			'GOOGL', 'Google', '2023-12-15 09:00:00', 131.85
			'GOOGL', 'Google', '2023-12-15 12:00:00', 131.68
			'GOOGL', 'Google', '2023-12-15 15:00:00', 132.26
		-META
			'META', 'Meta', '2023-12-11 09:00:00', 329.44
			'META', 'Meta', '2023-12-11 12:00:00', 320.50
			'META', 'Meta', '2023-12-11 15:00:00', 325.44

			'META', 'Meta', '2023-12-12 09:00:00', 324.64
			'META', 'Meta', '2023-12-12 12:00:00', 329.60
			'META', 'Meta', '2023-12-12 15:00:00', 332.18

			'META', 'Meta', '2023-12-13 09:00:00', 334.00
			'META', 'Meta', '2023-12-13 12:00:00', 333.99
			'META', 'Meta', '2023-12-13 15:00:00', 336.05

			'META', 'Meta', '2023-12-14 09:00:00', 333.92
			'META', 'Meta', '2023-12-14 12:00:00', 331.41
			'META', 'Meta', '2023-12-14 15:00:00', 332.24

			'META', 'Meta', '2023-12-15 09:00:00', 332.29
			'META', 'Meta', '2023-12-15 12:00:00', 335.95
			'META', 'Meta', '2023-12-15 15:00:00', 335.95

		-TSLA
			'TSLA', 'Tesla', '2023-12-11 09:00:00', 242.67
			'TSLA', 'Tesla', '2023-12-11 12:00:00', 238.00
			'TSLA', 'Tesla', '2023-12-11 15:00:00', 240.05

			'TSLA', 'Tesla', '2023-12-12 09:00:00', 238.95
			'TSLA', 'Tesla', '2023-12-12 12:00:00', 234.96
			'TSLA', 'Tesla', '2023-12-12 15:00:00', 236.46

			'TSLA', 'Tesla', '2023-12-13 09:00:00', 234.31
			'TSLA', 'Tesla', '2023-12-13 12:00:00', 229.56
			'TSLA', 'Tesla', '2023-12-13 15:00:00', 237.33

			'TSLA', 'Tesla', '2023-12-14 09:00:00', 241.15
			'TSLA', 'Tesla', '2023-12-14 12:00:00', 249.71
			'TSLA', 'Tesla', '2023-12-14 15:00:00', 251.00

			'TSLA', 'Tesla', '2023-12-15 09:00:00', 250.99
			'TSLA', 'Tesla', '2023-12-15 12:00:00', 252.83
			'TSLA', 'Tesla', '2023-12-15 15:00:00', 251.57
		-AAPL
			'AAPL', 'Apple', '2023-12-11 09:00:00', 193.05
			'AAPL', 'Apple', '2023-12-11 12:00:00', 191.97
			'AAPL', 'Apple', '2023-12-11 15:00:00', 192.90

			'AAPL', 'Apple', '2023-12-12 09:00:00', 193.13
			'AAPL', 'Apple', '2023-12-12 12:00:00', 193.45
			'AAPL', 'Apple', '2023-12-12 15:00:00', 194.25

			'AAPL', 'Apple', '2023-12-13 09:00:00', 194.98
			'AAPL', 'Apple', '2023-12-13 12:00:00', 195.96
			'AAPL', 'Apple', '2023-12-13 15:00:00', 197.94

			'AAPL', 'Apple', '2023-12-14 09:00:00', 198.07
			'AAPL', 'Apple', '2023-12-14 12:00:00', 197.80
			'AAPL', 'Apple', '2023-12-14 15:00:00', 197.73

			'AAPL', 'Apple', '2023-12-15 09:00:00', 197.87
			'AAPL', 'Apple', '2023-12-15 12:00:00', 197.95
			'AAPL', 'Apple', '2023-12-15 15:00:00', 197.47
		-AMZN
			'AMZN', 'Amazon', '2023-12-11 09:00:00', 145.54
			'AMZN', 'Amazon', '2023-12-11 12:00:00', 145.17
			'AMZN', 'Amazon', '2023-12-11 15:00:00', 145.56

			'AMZN', 'Amazon', '2023-12-12 09:00:00', 145.43
			'AMZN', 'Amazon', '2023-12-12 12:00:00', 146.60
			'AMZN', 'Amazon', '2023-12-12 15:00:00', 147.04

			'AMZN', 'Amazon', '2023-12-13 09:00:00', 148.25
			'AMZN', 'Amazon', '2023-12-13 12:00:00', 147.36
			'AMZN', 'Amazon', '2023-12-13 15:00:00', 148.54

			'AMZN', 'Amazon', '2023-12-14 09:00:00', 149.94
			'AMZN', 'Amazon', '2023-12-14 12:00:00', 148.19
			'AMZN', 'Amazon', '2023-12-14 15:00:00', 147.09

			'AMZN', 'Amazon', '2023-12-15 09:00:00', 148.39
			'AMZN', 'Amazon', '2023-12-15 12:00:00', 148.96
			'AMZN', 'Amazon', '2023-12-15 15:00:00', 149.36

</details>
<br>

Em seguida, criei a tabela no banco de dados, utilizando o SQLite.

```sql
CREATE TABLE stocks (
	symbol TEXT,
	name TEXT,
	datetime TEXT,
	price NUMERIC
);
```

E adicionei os dados acima:

```sql
INSERT INTO stocks (symbol, name, datetime, price)
    VALUES (...);
```

Em seguida, respondi as seguintes perguntas do projeto:

**- Quais são as ações distintas na tabela?**

```sql
SELECT DISTINCT(name) FROM stocks;
```

R: Google, Meta, Tesla, Apple, Amazon.

**- Consulte todos os dados de uma unica ação. Você percebe alguma tendência geral?**

```sql
SELECT * 
FROM stocks
WHERE name = 'Meta';
```

R: Durante a semana em que os dados coletados, a empresa Meta estava com uma alta no preço das ações.


**- Quais linhas têm um preço acima de 100? entre 40 a 50, etc?**

```sql
SELECT * 
FROM stocks
WHERE price > 100;
```

R: Todos os dados coletados tem um valor de ações acima de 100, resultando em 75 linhas. Mas se aumentarmos os valores para 200. Há um total de 30 linhas. Com ações apenas das empresas Meta e Tesla.


**- Classifique a tabela por preço. Quais são os preços mínimo e máximo?**

```sql
SELECT * 
FROM stocks
ORDER BY price;
```

Alternativamente, podemos utilizar as funções MIN e MAX para chegar aos valores solicitados na questão:

```sql
SELECT symbol, name, datetime, min(price)
FROM stocks;
```

```sql
SELECT symbol, name, datetime, max(price)
FROM stocks;
```

R: Que irá resultar nas ações da Google, com o valor de 131.22, no dia 14/12 às 12h. E nas ações da Meta, com o valor de 336.05, no dia 13/12 às 15h.


## Considerações finais
Me diverti bastante fazendo este projeto. Consegui entender melhor como funciona a coleta dos dados e como preparar um banco de dados para fazer uma análise.

Segue o link do projeto (em inglês) e do curso que estou fazendo, caso queiram dar uma olhada:

https://discuss.codecademy.com/t/data-science-independent-project-1-watching-the-stock-market/419943

https://www.codecademy.com/career-journey/data-scientist-aly