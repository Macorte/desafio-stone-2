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

A partir das estatísticas observadas é possível determinar que para as `card_family` **Gold** e **Platinum** o intervalo de `credit_limit` é:

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

Para esse desafio foi preciso fazer a seleção das `frauds` detro do *dataset* `transactions`, a partir disso foi gerado um novo *dataset* contendo apenas as transações fraudulentas, esse novo *dataset* foi organizado em ordem decrescente de acordo com a coluna `value`. Com isso para obter o `id` da transação fraudulenta de maior valor, bastou apenas retornar a primeira linha do *dataset* `frauds_transactions`.

**Conclusão:** A transação fraudulenta de maior valor tem o `id` = CTID20567160 e o `value` = 49155R$.

### - Analyze whether or not the fraudulent transactions are somehow associated to other features in the dataset. Explain your results.

Para a realização dessa tarefa, foi necessário a realização de 5 testes com o objetivo de encontrar alguma relação com o *dataset* de `frauds` com os outros *dataset*.

- Nesse Desafio o *dataset* `frauds_transactions` contêm apenas as transações fraudulentas independente das adições feitas a ele.

#### Teste 1:Em algum intervalo de valor de transação há uma maior ocorrência de transações fraudulentas.

Para esses teste foi preciso fazer a seleçāo das `frauds` no *dataset* `transactions`, gerando assim o *dataset* `fraud_transactions`. Após a criação desse novo *dataset* foi plotado o histograma abaixo:

![Captura de Tela 2021-04-09 às 10 29 33](https://user-images.githubusercontent.com/62664736/114187534-7c651500-991e-11eb-9e08-1b1da7206310.png)

Com a vizualização do histogram foi possível vizualizar uma discrepância significativa no intervalo das transações com valor entre 30.000 e 40.000, após essa vizualização as `frauds_transactions` foram divididas em intervalos de 10.000 de acordo com o `value`, com essa separação e a vizualização das principais estatísticas foi possível notar que no intervalo de 30.000 e 40.000 há aproximadamente o dobro de ocorrência de transações fraudulentas, como ilustra a tabela abaixo:

![Captura de Tela 2021-04-09 às 10 35 54](https://user-images.githubusercontent.com/62664736/114188291-5f7d1180-991f-11eb-8e3b-7aeff7654f30.png)

**Conclusão Teste 1:** A partir do histograma  é possível notar uma ocorrência maior no intervalo entre 30.000 e 40.000, separando esses intervalos e analisando seus dados foi possível determinar que no intervalo de 30.000 a 40.000 há aproximadamente o dobro de ocorrência de fraudes.

#### Teste 2: A `card_family` tem relação com as transações fraudulentas.

Para esses teste foi necessário adcionar a `card_family` ao *dataset* de `frauds_transactions` após isso foram plotados os gráficos abaixo:

![Captura de Tela 2021-04-09 às 10 41 40](https://user-images.githubusercontent.com/62664736/114189091-2e511100-9920-11eb-9e0b-3fe713bbe13d.png)

Esse primeiro gráfico tinha como objetivo identificar algum padrão na distribuição das transações pelo valor da transferência e pela `card_family`. Com a vizualização do gráfico não foi possível retirar nada de substancial.

![Captura de Tela 2021-04-09 às 10 44 59](https://user-images.githubusercontent.com/62664736/114189502-a586a500-9920-11eb-86e8-f9fe16e401ad.png)

Esse segundo gráfico tinha como objetivo separar as transações pela `card_family` para facilitar ainda mais a vizualização da relação da `card_family` e o valor das transações fraudulentas. Com a vizualização do gráfico não foi possivel retira nada de substancial.

![Captura de Tela 2021-04-09 às 10 48 32](https://user-images.githubusercontent.com/62664736/114189936-22b21a00-9921-11eb-93e3-ace72721fa05.png)

O terceiro gráfico foi um histograma que tinha como objetivo identificar uma maior ocorrência de fraudes de acordo com a `card_family`. Com esse gráfico foi possível notar uma maior ocorrência em cartões com a família **Premium**, porém a discrepância aparentemente não é significativa para que se tirasse alguma conclusão.

Após a observação do gráfico, foi dividido o *dataset* `fraud_transactions` em grupos de acordo com a `card_family`, com essa separação foi retornada as estatísticas abaixo:

![Captura de Tela 2021-04-09 às 10 58 30](https://user-images.githubusercontent.com/62664736/114191188-87ba3f80-9922-11eb-8f89-5473daacdd26.png)

**Conclusão Teste 2:** A partir dos gráficos não é possível vizualizar nenhum padrão significativa, separando os dados pela família do cartão e olhando suas principais estatísticas támbem não é possível chegar a nenhuma conclusão plausível. Dessa forma podemos afirmar que a família do cartão não tem relação significativa com as transações fraudulentas.

### Teste 3: Há relação entre as datas das transações e as transações fraudulentas.

Para esse desafio, foi necessário gerar um *dataset* com a o numero de transações fraudulentas por mês. Após isso foram gerado gráficos para que fosse possível identificar discrepâncias.

![Captura de Tela 2021-04-09 às 11 09 29](https://user-images.githubusercontent.com/62664736/114192604-0fed1480-9924-11eb-8c69-da4c52ecfd3c.png)

Com essa primeira vizualização foi possível notar uma diferença aparentemente significativa no mês 09 , porém já tendo vizualizado as quantidades de transações de acordo com os meses, é notável que essa diferênça tão assimétrica foi fruto da escala do gráfico. Corrigindo essa escala temos essa nova vizualização.

![Captura de Tela 2021-04-09 às 11 16 27](https://user-images.githubusercontent.com/62664736/114193562-09ab6800-9925-11eb-8ec2-9d98c221e51d.png)

Com o novo gráfico se conclui que a diferença observada anteriormente era fruto da escala.

**Conclusão Teste 3:** Após separar a ocorrência de fraudes por mês e gerar a primeira time series, foi possível vizualizar uma discrepância aparentemente significativa no mês 09, porém analizando os valores foi possível concluir que essa discrepância era fruto da escala do gráfico, após a correção da escala e a analize dos valores foi possível concluir que as transações fraudulentas não possuem uma relação significativa com a data.

### Teste 4: A idade dos clientes tem relação com as trasações fraudulentas.

Para realizar esse teste foi necessário a adicionar ao *dataset* `fraud_transactions` os dados `customer_id` e `age`. Após essa adição foram plotados gráficos para identificar alguma relação entre `age` e as transações fraudulentas.

![Captura de Tela 2021-04-09 às 11 36 54](https://user-images.githubusercontent.com/62664736/114196598-e635ec80-9927-11eb-882c-ec6bd3f088ea.png)

A primeira vizualização feita, foi a partir desse histograma, com essa vizualização dá para notar que no intervalo de [40 - 45] anos aparentemente há uma maior ocorrência de fraudes. Com isso foi plotado o gráfico abaixo no intuito de vizualizar melhor essa distribuição.

![Captura de Tela 2021-04-09 às 11 43 11](https://user-images.githubusercontent.com/62664736/114197484-c5ba6200-9928-11eb-8261-a92d50e845fd.png)

A partir dessa segunda vizualização, a hipótese gerada no gráfico anterior se demonstra inválida já que nesse segundo gráfico a distribuição das das transações fraudulentas pela idade dos clientes parece não seguir nenhum padrão.

Com as duas vizualizações para definir uma conclusão concreta foi separado as transações em intervalos de idades e retirado seus dados, como ilustra a tabela abaixo:

![Captura de Tela 2021-04-09 às 11 49 01](https://user-images.githubusercontent.com/62664736/114198353-98ba7f00-9929-11eb-829c-dd79d58bbb19.png)

**Conclusão Teste 4:** Preparando o dataset e plotando o histograma, foi possível vizualizar uma discrepância no intervalo de 40 a 45 anos, já no outro gráfico indica que não há uma dispersão padronizada, separando as idades em intervalos e observando os dados é possível concluir que não há um padrão quanto a idade dos clientes que tiveram seus cartões fraudados, ou seja, podemos concluir que a idade não possui relação significativa com as transações fraudulentas.

### Teste 5: O `credit_limit` tem relação com as transações fraudulentas.

Nesse desafio foi necessário adicionar o `credit_limit` ao *dataset* `fraud_transactions`. A partir dessa adição foram plotados os seguintes gráficos:

![Captura de Tela 2021-04-09 às 12 01 46](https://user-images.githubusercontent.com/62664736/114200226-5f830e80-992b-11eb-81c3-8c55f67aece0.png)

Com esse histograma é possível notar que a maior parte das transações fraudulentas possui um `credit_limit`  <= 200.000. A partir dessa obsevaçāo foi plotado um segundo gráfico com a distribuição das transferências fraudulentas pelo limite do cartão de acordo com a família do cartão.

![Captura de Tela 2021-04-09 às 12 05 35](https://user-images.githubusercontent.com/62664736/114200775-e801af00-992b-11eb-91a2-c6a5d63c5e5e.png)

Nessa segunda observaçāo é possível notar que a maior parte das transações com `credit_limit`  <= 200.000 são feitas a partir de cartões de `card_family` **Gold** ou **Platinum**, que como observado no ranqueamento do cartão possuem limite máximo <= 200.000. Devido a esse fato é possível descartar essa relação.

**Conclusão Teste 5:** Vizualizando os dois gráficos é possível determinar que a maior parte das transações fraudulentas são feitas de cartões com limite menor que 200K, porém considerando 64 das 109 transações são feitas de cartões **Gold** e **Platinum** que possuem um limite máximo menor ou igual a 200K, a variável observada demonstra não possuir significância para a análise em questão, permitindo concluir que não há uma relação significativa entre as transações fraudulentas e o limite do cartão.

## Conclusão Geral

Após a realização de todos os testes, é possível concluir que o único dado obtido que possui alguma significância é o fato de que no intervalo de transações fraudulentas com valor entre 30.000 e 40.000, há aproximadamente o dobro de ocorrência de fraudes. Nos demais teste não foi possível observar mais nenhuma relação significativas entre os dados observados e as transações fraudulentas.
