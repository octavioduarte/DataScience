
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