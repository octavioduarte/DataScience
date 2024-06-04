<h2>Alguns pontos importantos ao analisar um Dataset:</h2>

* Identificar os valores mínimos das colunas, podemos identificar possíveis erros como números negativos, zeros e etc... Números que não fariam sentido para aquela coluna.

* O número 0 exige atenção, é usado em alguns casos de ausência de valor, mas isso pode impactar de forma negativa para fins de estatística ou até em um modelo de Machine Learning (isso quando fazem sentido em um registro e não são um erro que contradizem inclusive o propósito de uma determinada coluna do Dataset).

* Verificar se o desvio padrão (std no pandas) de uma determinada coluna é 0, isso significa que existe apenas um valor para todos os registros. Esse tipo de dado costuma ser desconsiderado em uma análise... Entende-se que é algo padronizado dos registros.


<br/>
<br/>
<br/>


<h2>Percentil e Quartil:</h2>

Percentil é uma medida de posição, ele é útil para entendermos como nossos dados estão distribuídos. Utilizando um exemplo muito comum de blogs de cientistas de dados vamos criar um exemplo com 20 notas de uma prova entre 0 e 100:

~~~python
    [14, 20, 24, 29, 34, 39, 44, 49, 54, 59, 64, 69, 74, 79, 84, 89, 92, 94, 96, 100]
~~~

Agora desejo obter um valor onde 25% dos dados são menores ou igual a ele, para isso utilizamos a seguinte formula:

    (Percentual x Tamanho dos Dados) / 100

Aplicando com os dados do exemplo acima: 

    (25 * 20) / 100 =  5

A posição 5 no nosso intervalo de dados é 34, ou seja, 25% das notas são iguais ou menores a 34.
Em termos técnicos podemos dizer que o percentil 25 dos nosso dados é 34.


Agora podemos falar sobre Quartis, na prática são o Percentil 25%, 50% e 75% técnicamente chamados de Q1, Q2 e Q3. 

Importante lembrar que:

    O Q2, o P50 e a Mediana serão sempre o mesmo valor.


<br/>
<br/>
<br/>


<h2>O que são Outliers:</h2>

Outliers são valores que fogem do padrão de um conjunto de dados. São valores muito alto ou muito baixos que podem influenciar negativamente em uma análise dos dados. Por exemplo, se temos um conjunto de dados com salários de funcionários de uma empresa e um dos salários é muito maior do que os outros esse valor pode ser considerado um outlier.

Estatisticamente um outlier é um valor que está 1.5 vezes o intervalo interquartil acima do Q3 ou a mais de 1.5 vezes o intervalo interquartil abaixo do Q1. O intervalo interquartil é a diferença entre o  Q3 e o Q1.

<br/>
<br/>
<br/>

<h2>O cuidado com Datasets desbalanceados:</h2>

Datasets desbalanceados são aqueles onde a coluna "alvo" que usaremos para treinar nosso modelo não tem uma grande variação em seus valores.

Um exemplo se montarmos um modelo de Machine Learning para prevenção de fraude em compras de cartão de crédito, convenhamos que não é tão comum que as compras de um cliente sejam resultado de uma fraude, por tanto, se tivéssemos uma coluna que indicasse que a compra é fraude ou não, algo do tipo "is_fraud" grande parte dos valores seriam false, por que boa parte das compras foram de fato realizada pelo cliente, por tanto, ao treinar um modelo com estes dados sem estratégias de balanceamento fará com que nosso modelo tenha uma tendência a aceitar (quase) quaisquer compras como legitimas o que não pode ser tomado como uma verdade em todos os casos. 

<br/>
<br/>
<br/>

<h2>Atenção com colunas que são identificadores:</h2>


Colunas que tem o propósito de identificar um registro (normalmente com o nome id) são normalmente descartadas de um Dataset que servirá para o treinamento de um modelo, isso por que são colunas que não agregam muito para um treinamento, em resumo na boa parte dos casos vale a pena remove-las do nosso Dataset.

<br/>
<br/>
<br/>

<h2>Histogramas x Gráfico de barras:</h2>


Apesar da semelhança visual um histograma e um gráfico de barras tem diferentes propósitos, enquanto o **gráfico de barras serve pra visualizarmos os dados por categorias**, por exemplo, quantidade de funcionários por departamento (departamento  é categórico), o **histrograma serve para ver a quantidade de pessoas por faixa etária (faixa etária não é categórica)**.

<br/>
<br/>
<br/>

<h2>Variáveis categóricas:</h2>


Dentro de um dataset vamos ter colunas categóricas, são colunas com pouca variação de valores que agrupam um conjunto de registros. Um exemplo seria um Dataset contendo dados de funcionários de uma empresa, onde o departamento é uma variável cateórica, pois não possui grande variação de registros, agrupa (representa) um cojunto de dados:


| ID          | Nome             | Departmento | Posição            | Email                       |
|-------------|------------------|-------------|--------------------|-----------------------------|
| 001         | John Doe         | Marketing   | Gerente            | john.doe@example.com        |
| 002         | Jane Smith       | Vendas      | Executivo de vendas| jane.smith@example.com      |
| 003         | Michael Johnson  | TI          | Developer          | michael.johnson@example.com |
| 004         | Emily Davis      | RH          | Especialista de RH | emily.davis@example.com     |
| 005         | William Brown    | Finanças    | Contador           | william.brown@example.com   |
| 006         | John Doe         | Marketing   | Gerente            | john.doe@example.com        |
| 007         | Jane Smith       | Vendas      | Executivo de Vendas| jane.smith@example.com      |
| 008         | Michael Johnson  | TI          | Desenvolvedor      | michael.johnson@example.com |
| 009         | Emily Davis      | RH          | Especialista de RH | emily.davis@example.com     |
| 0010        | William Brown    | Finanças    | Contador           | william.brown@example.com   |

Dentro do conceito de variáveis categóricas temos **Variáveis Categóricas Ordenadas** e **Variáveis Categóricas Não Ordernadas**, entende-se as categóricas ordenadas como variáveis onde suas categorias possuem uma hierarquia, ascendencia ou coisas do tipo. O exemplo do departamento não é um exemplo de variável categórica ordenada, não podemos determinar uma hierarquia entre diferentes departamentos de uma empresa, mas um bom exemplo é a coluna "Posição" ela é uma variável categórica e podemos determina-la como ordenada pois há uma hierarquia entre suas classe, como dizer que um "gerente" responde a um "diretor" que por sua vez responde a um "presidente".  

Links úteis: </br>
    [Introdução ao Pivot Table](https://www.youtube.com/watch?v=Ns5qXfPrBm8)