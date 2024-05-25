
#### Contagem de valores 0 (zero) por colunas
~~~python
    df.isnull().sum()
~~~

#### Contagem de linhas duplicadas
~~~python
    df.duplicated().sum()
~~~

#### Verificar nosso DataFrame com os valores float tendo apenas duas casas decimais
~~~python
    count_columns_of_df = 30
    with pd.option_context("float_format", "{:.2f}".format, "display.max_columns", count_columns_of_df):
        display(df.describe())
~~~

#### Filtrar os "n" maiores registros filtrados por uma coluna
~~~python
    TOTAL_DE_REGISTROS_RETORNADOS = 10
    df.nlargest(TOTAL_DE_REGISTROS_RETORNADOS, "Nome Da Coluna")
~~~

#### Filtrar os "n" menores registros filtrados por uma coluna
~~~python
    TOTAL_DE_REGISTROS_RETORNADOS = 10
    df.nsmallest(TOTAL_DE_REGISTROS_RETORNADOS, "Nome Da Coluna")
~~~


#### Remover colunas cujo os valores não possuem variação
~~~python
    for c in df.columns:
        column = df[c]
        if (column.nunique() <= 1):
            df = df.drop(c, axis=1)
~~~


#### Visualizar todas as variações de valores de uma coluna
~~~python
for column in df.columns:
    print(f"{column}: {df[column].unique()}")
~~~



#### No Jupyter Notebook podemos consultar a documentação de um método utilizando '?' antes da declaração do método e presssionando Shift + Enter
~~~python
    # Digite em uma célula:
    ?df.pivot_table
    # Depois pressione  Shift + Enter
~~~


### Tenha cuidado ao analisar dados não inteiros, como médias ou percentuais, pois eles podem levar a conclusões equivocadas. Por exemplo, posso extrair de um conjunto de dados que a média das notas dos alunos canhotos é maior do que a dos destros. No entanto, essa média pode ser baseada em apenas 2 canhotos e 120 destros. Também posso afirmar que 100% dos alunos que escrevem com a mão esquerda têm notas acima de 8. Embora este exemplo pareça exagerado, ele ilustra como dados podem transmitir conclusões enganosas.