# 🐼 Pandas

![License: MIT](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white)
![Jupyter Notebook](https://img.shields.io/badge/jupyter-%23FA0F00.svg?style=for-the-badge&logo=jupyter&logoColor=white)
![Visual Studio Code](https://img.shields.io/badge/Visual%20Studio%20Code-0078d7.svg?style=for-the-badge&logo=visual-studio-code&logoColor=white)
![Microsoft Excel](https://img.shields.io/badge/Microsoft_Excel-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white)

_Pandas na prática: usando Python para análise de dados_

Este repositório contém os arquivos utilizados no minicurso de introdução ao **Pandas**, ministrado por **Davi Reis Furtado** e **Gabriel de Almeida Dias**. O objetivo é apresentar os principais conceitos e comandos da biblioteca **Pandas**, amplamente utilizada para análise de dados em Python.

## 👨🏽‍💻 Pré-requisitos
Antes de iniciar o minicurso, é necessário ter instalado as seguintes ferramentas

### 🧰 Ferramentas
- Python
- Visual Studio Code

### 🧩 Extensões para VS Code
- Jupyter Notebook
- Office Viewer

### 📦 Bibliotecas Python
- `pandas`
- `openpyxl`

---

## 📚 Conteúdo do Minicurso

### 1. Introdução ao Pandas
- Importar a biblioteca *pandas* e dando o apelido *pd*
  ```python
  import pandas as pd
  ```

### 2. Criação de DataFrames
- A partir de um dicionário
  ```python
  df = pd.DataFrame(dict)
  ```
- DataFrame vazio
  ```python
  df = pd.DataFrame()
  ```
- DataFrame vazio com colunas definidas
  ```python
  df = pd.DataFrame(columns=['column_x', 'column_y'])
  ```

### 3. Leitura e Escrita de Arquivos
- Ler arquivos Excel
  ```python
  pd.read_excel('file.xlsx')
  ```
- Exportar para Excel
  ```python
  df.to_excel('file_name.xlsx', index=False)
  ```

### 4. Visualização de Dados
- Exibir DataFrame no terminal
  ```python
  print(df)
  ```
- Exibir DataFrame formatado (só no Jupyter Notebook)
  ```python
  display(df)
  ```
- Ver as primeiras linhas
  ```python
  df.head(n=5)  # n é opcional, o padrão é 5
  ```
- Ver as últimas linhas
  ```python
  df.tail(n=5)  # n é opcional, o padrão é 5
  ```
- Ver dimensões do DataFrame
  ```python
  df.shape  # tupla com (altura, largura)
  df.shape[0]  # altura
  df.shape[1]  # largura
  ```
- Estatísticas descritivas
  ```python
  df.describe()
  ```

### 5. Seleção de Dados
- Selecionar uma coluna
  ```python
  df['column']
  ```
- Selecionar múltiplas colunas
  ```python
  df[['column_x', 'column_y']]
  ```
- Média dos valores de uma coluna
  ```python
  df['column'].mean()
  ```
- Valores únicos em uma coluna
  ```python
  df['column'].unique()
  ```
- Contagem de valores únicos em uma coluna
  ```python
  df['column'].nunique()
  ```
- Valores únicos e suas frequências em uma coluna
  ```python
  df['column'].value_counts()
  ```

### 6. Indexação com `.loc`
- Selecionar uma linha específica
  ```python
  df.loc[index]
  ```
- Selecionar um intervalo de linhas
  ```python
  df.loc[start_index:end_index]
  ```
- Selecionar célula específica
  ```python
  df.loc[index, 'column']
  ```
- Selecionar linha com colunas específicas
  ```python
  df.loc[index, ['column_x', 'column_y']]
  ```
- Selecionar com condição
  ```python
  df.loc[df['column'] == value]
  ```
- Selecionar coluna com condição
  ```python
  df.loc[df['column_x'] == value, 'column_y']
  ```
- Selecionar múltiplas colunas com condição
  ```python
  df.loc[df['column_x'] == value, ['column_y', 'column_z']]
  ```

### 7. Limpeza de Dados
- Remover linhas duplicadas
  ```python
  df.drop_duplicates(inplace=True)
  ```
- Substituir valores
  ```python
  df.replace(old, new, inplace=True)  # do DataFrame em geral
  df['column'].replace(old, new, inplace=True)  # de uma parte do DataFrame selecionada
  ```
- Remover linhas ou colunas
  ```python
  df.drop(index, axis=0, inplace=True)  # remove linha - axis é opcional, o padrão é 0
  df.drop('column', axis=1, inplace=True)  # remove coluna
  ```
- Tratar valores ausentes (`None`)
  ```python
  df.dropna(how='all', axis=1, inplace=True)  # remove colunas totalmente vazias
  df.dropna(how='any', inplace=True)  # remove linhas com pelo menos um valor vazio - Nesse caso 'how' é opcional, pois o padrão já é 'any'
  df['column'].fillna(value, inplace=True)  # preenche valores vazios com 'value'
  df.ffill(inplace=True)  # Preenche com o valor anterior
  ```

### 8. Manipulação de DataFrames
- Juntar/concatenar DataFrames
  ```python
  new_df = pd.concat([df1, df2], ignore_index=True)
  ```
- Mesclar DataFrames *parecidos*
  ```python
  df_merged = df1.merge(df2)
  ```
- Agrupar dados
  ```python
  grouped_x = df[['column_x', 'column_y']].groupby('column_x').function()  # alguns exemplos de .function() possíveis são: .sum()/.mean()/.max()/.min()
  ```

### 9. Dica útil
Muitas funções do Pandas aceitam o argumento `inplace=True`, que aplica a modificação diretamente no DataFrame, sem precisar reatribuir