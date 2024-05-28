<h2>Alguns pontos importantos ao analisar um Dataset:</h2>

    * Identificar os valores mínimos das colunas, podemos identificar possíveis erros como números negativos, zeros e etc... Números que não fariam sentido para aquela coluna.

    * O número 0 exige atenção, é usado em alguns casos de ausência de valor, mas isso pode impactar de forma negativa para fins de estatística ou até em um modelo de Machine Learning (isso quando fazem sentido em um registro e não são um erro que contradizem inclusive o propósito de uma determinada coluna do Dataset).

    * Verificar se o desvio padrão (std no pandas) de uma determinada coluna é 0, isso significa que existe apenas um valor para todos os registros. Esse tipo de dado costuma ser desconsiderado em uma análise... Entende-se que é algo padronizado dos registros.


<br/>
<br/>
<br/>

<h2>O que são Quartis:</h2>

    Quartis são valores que dividem nosso conjunto de dados em 4 partes iguais. O primeiro quartil (Q1) é o valor que deixa 25% dos dados abaixo e 75% acima, o segundo quartil (Q2) é a mediana, que deixa 50% dos dados abaixo e 50% acima. O terceiro quartil (Q4) deixa 75% dos dados abaixo e 25% doas dados acima.

    Um exemplo, supondo que utilizemos o método .describe() do Pandas e verificamos que para a coluna idade do nosso DataSet temos: 

            Q1    Q2   Q3   Q4 (MAX)
    std:    30    36   43   60


    Podemos concluir que: 

      - 25% das pessoas deste Dataset tem 30 anos ou menos (Q1)
      - 50% das pessoas deste Dataset tem 36 anos ou menos (Q2)
      - 75% das pessoas deste Dataset tem 43 anos ou menos (Q3)
      - 100% das pessoas deste Dataset tem 60 anos ou menos
 

<h2>O que são Outliers:</h2>

    Outliers são valores que fogem do padrão de um conjunto de dados. São valores muito alto ou muito baixos que podem influenciar negativamente em uma análise dos dados. Por exemplo, se temos um conjunto de dados com salários de funcionários de uma empresa e um dos salários é muito maior do que os outros esse valor pode ser considerado um outlier.

    Estatisticamente um outlier é um valor que está 1.5 vezes o intervalo interquartil acima do Q3 ou a mais de 1.5 vezes o intervalo interquartil abaixo do Q1. O intervalo interquartil é a diferença entre o  Q3 e o Q1


<h2>O cuidado com Datasets desbalanceados:</h2>


    Datasets desbalanceados são aqueles onde a coluna "alvo" que usaremos para treinar nosso modelo não tem uma grande variação em seus valores.

    Um exemplo se montarmos um modelo de Machine Learning para prevenção de fraude em compras de cartão de crédito, convenhamos que não é tão comum que as compras de um cliente sejam resultado de uma fraude, por tanto, se tivéssemos uma coluna que indicasse que a compra é fraude ou não, algo do tipo "is_fraud" grande parte dos valores seriam false, por que boa parte das compras foram de fato realizada pelo cliente, por tanto, ao treinar um modelo com estes dados sem estratégias de balanceamento fará com que nosso modelo tenha uma tendência a aceitar (quase) quaisquer compras como legitimas o que não pode ser tomado como uma verdade em todos os casos. 


<h2>Atenção com colunas que são identificadores:</h2>


    Colunas que tem o propósito de identificar um registro (normalmente com o nome id) são normalmente descartadas de um Dataset que servirá para o treinamento de um modelo, isso por que são colunas que não agregam muito para um treinamento, em resumo na boa parte dos casos vale a pena remove-las do nosso Dataset.


<h2>Histogramas x Gráfico de barras:</h2>


    Apesar da semelhança visual um histograma e um gráfico de barras tem diferentes propósitos, enquanto o **gráfico de barras serve pra visualizarmos os dados por categorias**, por exemplo, quantidade de funcionários por departamento (departamento  é categórico), o **histrograma serve para ver a quantidade de pessoas por faixa etária (faixa etária não é categórica)**.






Links úteis: </br>
    [Introdução ao Pivot Table](https://www.youtube.com/watch?v=Ns5qXfPrBm8)