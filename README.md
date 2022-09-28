### Um olhar sobre a indústria de jogos. 📊
Descobrindo e entendendo mais sobre a era dourada dos jogos eletrônicos.

## Ferramentas utilizadas no processo:
- SQL;
- Python;  
- PostgreSQL;  
- pgAdmin;
- Jupyter Notebook.  

## Objetivo:
Elaborar um storytelling baseado em **[dados](https://www.kaggle.com/datasets/holmjason2/videogamedata)** disponibilizados pela plataforma Kaggle para descobrir mais sobre o consenso da crítica especializada e dos jogadores a respeito dos jogos lançados entre 1977 e 2020.

## Introdução
Em **[pesquisa](https://www.mordorintelligence.com/industry-reports/global-gaming-market)** realizada pela Mordor Intelligence, a projeção é que o mercado de videogames movimente mais de 300 bilhões de dólares até 2027. Sendo um mercado tão grande, os desenvolvedores tem lançado uma obra atrás da outra, mas fica a questão: os jogos ainda tem qualidade?

<img src="https://s3.mordorintelligence.com/global-gaming-market/1646649226003_global-gaming-market_Market_Summary.webp" height=500>

A tabela a ser utilizada apresenta 357 registros diferentes, e é disposta da seguinte maneira:

<b>game_sales</b>
| Nomeclatura   | Tipo     |
| ------------- | -------- |
| Rank          | int      |
| Name          | varchar  |
| Platform      | varchar  |
| Publisher     | varchar  |
| Developer     | varchar  |
| Critic_Score  | decimal  |
| User_Score    | decimal  |
| Total_Shipped | decimal  |
| Year          | int      |

## Primeira etapa:

A partir da tabela principal, criar duas tabelas temporárias, a primeira chamada <i>games</i>, com informações sobre nome, plataforma, empresa que publicou, empresa que desenvolveu e o total de vendas, e a segunda, <i>reviews</i>, que possui a nota recebida pela crítica especializada pelos jogadores, conforme estrutura a seguir:

<b>games</b>
| Nomeclatura   | Tipo     |
| ------------- | -------- |
| Name          | varchar  |
| Platform      | varchar  |
| Publisher     | varchar  |
| Developer     | varchar  |
| Total_Shipped | decimal  |
| Year          | int      |

<b>reviews</b>
| Nomeclatura  | Tipo    |
| ------------ | ------- |
| Name         | varchar |
| Critic_Score | varchar |
| User_Score   | decimal |

Para resultados mais concisos, ao utilizar um LEFT JOIN de <i>games</i> e <i>reviews</i> foi descoberto que o total de jogos que possuem os campos <i>Critic_Score</i> e <i>User_Score</i> nulos são 34, o que representa menos de 10% do database, não influenciando de forma drástica no resultado final.

## Segunda etapa:

- As informações foram agrupadas por ano, exibindo a média de <i>Critic_Score</i> e o número de jogos lançados no período, excluindo-se os anos com menos de 4 lançamentos computados e limitando o resultado ao top 10.
- O mesmo foi realizado com <i>User_Score</i>.
- Obtivemos então, duas tabelas distintas:

![image](https://user-images.githubusercontent.com/114587036/192882425-227ebc07-e0b1-4693-b66f-39dc6990fadc.png)

## Terceira etapa:

- Através da ferramenta INTERSECT, pudemos então descobrir os anos dourados do jogos, aqueles que caíram nas graças tanto do público quanto da crítica especializada:

|year |
|-----|
|1998 |

## Referências

1. **[GAMING MARKET - GROWTH, TRENDS, COVID-19 IMPACT, AND FORECASTS (2022-2027)](https://www.mordorintelligence.com/industry-reports/global-gaming-market)**
2. **[Video Game Sales Data](https://www.kaggle.com/datasets/holmjason2/videogamedata)**
3. **[pgAdmin 4 6.14 Documentation](https://www.pgadmin.org/docs/pgadmin4/development/)**
