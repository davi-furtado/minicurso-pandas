# Pandas na prática: usando Python para análise de dados

Neste repositório estão os arquivos usados no minicurso de Pandas dado pelos alunos **Davi Reis Furtado** e **Gabriel de Almeida Dias**

Segue um pequeno roteiro do minicurso:

1. Importar a biblioteca *pandas* com apelido *pd* - `import pandas as pd`
2. Criação de dataframes
   a. A partir de dicionários - `df = pd.DataFrame(dict)`
   b. Vazio - `df = pd.DataFrame()`
   c. Vazio com colunas pré-definidas - `df = pd.DataFrame(columns=['column1', 'column2'])`
3. Selecionando colunas
   a. Uma única - `df['column']`
   b. Mais de uma - `df[['column_a', ... , 'column_z']]`
   c. Valores únicos de uma coluna com `.unique()`
   d. Quantidades de valores únicos de uma coluna com `.nunique()`
   e. Valores e suas frequências com `.value_counts()`
4. `df.loc[...]`
   a. `df.loc[n]` - Seleciona uma linha
   b. `df.loc[n, ‘column’]` - Seleciona o elemento na linha n e na coluna column
   c. `df.loc[n, [’column_a’, … , ’column_z’]]` - Seleciona a linha n com as colunas especificadas
   d. `df.loc[condition]` - Seleciona a linha se a condição for satisfeita
   e. `df.loc[condition, ‘column’]` - Seleciona o elemento na linha na coluna column se a condição for satisfeita
   f. `df.loc[condition, [’column_a’, … , ’column_z’]]` - Seleciona a linha com as colunas especificadas se a condição for satisfeita
5. `print(df)` - Mostra a tabela no terminal, mas sem formatação
6. `display(df)` - Mostra a tabela com formatação no terminal, mas só em arquivos `.ipynb`
7. Importando arquivo Excel (`.xlsx`) pra dentro do python - `pd.read_excel('file.xlsx')`
8. `df = df.drop_duplicates()` - Deleta linhas duplicadas
9. `df/df[column] = df/df[column].replace(old, new)` - Troca os elementos iguais a old por new
10. `df.head(n=5)` - Pega as primeiras *n* linhas de uma tabela (se não colocar nada, *n* vale 5)
11. `df.shape` - Pega o número de colunas e o número de linhas do dataframe
12. `df.describe()` - Faz um ‘resuminho’ das colunas com valores numéricos
13. Juntar DataFrames com mesmas colunas com `new_df = pd.concat([df1, df2], ignore_index=True)`
14. Inserir um DataFrame no Excel com `df.to_excel(‘nome’, index=False)`
15. Apagar
    a. Linhas - `new_df = df.drop(0, *axis*=0)`
    b. Colunas - `vendas_df.drop(0, *axis*=0)`
16. Deletando/completando valores vazios
    a. `df = df.dropna(how='all', axis=1)`  - Deleta todas as colunas (pois axis=1) completamente vazias
    b. `df = df.dropna()`  - Deleta todas as linhas (pois axis=0) com pelo menos 1 valor vazio
    c. `df['column'] = df['column'].fillna(0)`  - Todos os valores vazios viram 0
    d. `df['column'] = df['column'].fillna(df['column'].mean())`  - Todos os valores vazios viram a média da coluna
    e. `df.ffill(inplace=True)`  - Preenche os valores vazios com o primeiro valor válido encontrado acima
17. Gerando mini relatório com `relatorio = df[['column1', 'column2']].groupby('column1').sum()`  também podemos usar com `.mean()` e outros parâmetros
18. Unindo DataFrames ‘parecidos’ com `df1 = df1.merge(df2)`
19. Podemos usar `inplace=True` como argumento de algumas funções para não precisar ficar reatribuindo
