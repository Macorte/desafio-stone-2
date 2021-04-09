# **Desafio Stone** 

## **Ferramentas**
Para a resolução desse desafio foi utilizado Python através de notebooks Jupyter com o auxílio das bibliotecas: Pandas, Seaborn e Matplotlib

## **Processo** 

### - What is the average age of the customers in the database?

O priemiro passo foi plotar o histograma abaixo para que fosse possível vizualizar a distribuição das idades:

![Captura de Tela 2021-04-09 às 09 27 34](https://user-images.githubusercontent.com/62664736/114179795-d31a2100-9915-11eb-9025-0d57d0421102.png)

Após a vizualização, foi calculada a média da coluna `age` dessa forma chegando ao valor de **35,06**.

**Conclusão:**  A média de idades dos clientes é igual a 35.06, ou seja, aproximadamente 35 anos. Através do gráfico de frequência é possível observar que apesar da média ter o valor de 35.06, a distribuição das idades é bem variada indicando que a média de idade não é uma variável significativa para identificar algum padrão no *dataset* de clientes, sendo inclusive o intervalo de 35 anos um dos intervalos que possue uma das menores quantidades de dados.

### - How is the `card_family` ranked based on the `credit_limit` given to each card?

O primeiro passo foi plotar um gráfico para ilustrar a distribuição dos clientes de acordo com a `card_family` e o `credi_limit`

![Captura de Tela 2021-04-09 às 09 40 02](https://user-images.githubusercontent.com/62664736/114181185-918a7580-9917-11eb-856f-75e123bb0f48.png)

Após a vizualização foi possível notar que a `card_family` **Gold** e **Platinum** aparentemente possuiam uma faixa de limite bem definida, para facilitar ainda mais essa vizualização foi plotado outro gráfico, dessa vez, ilustrando o limite dos cartões de acordo com sua família.

![Captura de Tela 2021-04-09 às 09 44 05](https://user-images.githubusercontent.com/62664736/114181633-22615100-9918-11eb-8bd2-74f36f7e4f71.png)

Com essa vizualização ficou ainda mais claro que para a `card_family` **Gold** e **Platinum** há um intervalo de `credit_limit` bem definido, para a confirmação dessa hipótese, foi dividido os dados em grupos de acordo com a `card_family` e retornada as estatísticas abaixo:

![Captura de Tela 2021-04-09 às 09 47 36](https://user-images.githubusercontent.com/62664736/114182082-a0255c80-9918-11eb-96a4-5b1273709c26.png)

Apartir das estatísticas observadas é possível determinar que para as `card_family` **Gold** e **Platinum** o intervalo de `credit_limit` é:

- **Gold** [2.000 - 50.000]
- **Platinum** [51.000 - 200.000]

Para o **Premium** atravé desses testes não foi possível determinar um `credit_limit` por conta disso foi plotado um boxplot para que fosse possível identificar outliers:

![Captura de Tela 2021-04-09 às 10 00 16](https://user-images.githubusercontent.com/62664736/114183759-65bcbf00-991a-11eb-85bc-21f7efc17d01.png)

Após a vizualização do boxplot, não foi identificado outliers, assim não foi possível determinar algum padrão para a `card_family` **Premium**.

**Conclusão:** Após a relização das vizualizações dos gráficos e das estatísticas foi possível determinar as seguintes relações entre `card_family` e `credit_limit`:

- **Gold:** O `credit_limit` para essa família é determinado no intervalo entre [2.000 - 50.000].
- **Platinum:** O `credit_limit` para esssa família é determinado no intervalo entre [51.000 - 200.000].
- **Premium:** Para essa família não foi possível determinar um intervlo de limite, apenas é possível concluir que se o `credit_limit` > 200.000 a `card_family` é **Premium**.

### - For the transactions flagged as fraud, what are the ids of the transactions with the highest value?

Para esse desafio foi preciso fazer a seleção das `frauds` detro do *dataset* `transactions`, apartir disso foi gerado um novo *dataset* contendo apenas as transações fraudulentas, esse novo *dataset* foi organizado em ordem decrescente de acordo com a coluna `value`. Com isso para obter o `id` da transação fraudulenta de maior valor, bastou apenas retornar a primeira linha do *dataset* `frauds_transactions`.

**Conclusão:** A transação fraudulenta de maior valor tem o `id` = CTID20567160 e o `value` = 49155R$.
 


