
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