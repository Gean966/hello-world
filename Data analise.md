import pandas as pd
import matplotlib.pyplot as plt

# Carregar os dados do arquivo CSV
dados = pd.read_csv('dados_pandemia.csv')

# Exibir as primeiras linhas do conjunto de dados para verificar a estrutura
print(dados.head())

# Plotar o número total de casos e mortes por país
dados_por_pais = dados.groupby('Country').sum().reset_index()

# Ordenar os dados por número de casos
dados_por_pais = dados_por_pais.sort_values(by='Cases', ascending=False)

# Visualizar os 10 países com mais casos
top_10_paises_casos = dados_por_pais.head(10)
plt.figure(figsize=(12, 8))
plt.bar(top_10_paises_casos['Country'], top_10_paises_casos['Cases'], color='blue')
plt.xlabel('Países')
plt.ylabel('Número de Casos')
plt.title('Top 10 Países com Mais Casos de COVID-19')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()

# Visualizar os 10 países com mais mortes
top_10_paises_mortes = dados_por_pais.sort_values(by='Deaths', ascending=False).head(10)
plt.figure(figsize=(12, 8))
plt.bar(top_10_paises_mortes['Country'], top_10_paises_mortes['Deaths'], color='red')
plt.xlabel('Países')
plt.ylabel('Número de Mortes')
plt.title('Top 10 Países com Mais Mortes por COVID-19')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()

# Analisar a evolução temporal global de casos e mortes
dados_globais = dados.groupby('Date').sum().reset_index()

plt.figure(figsize=(12, 8))
plt.plot(dados_globais['Date'], dados_globais['Cases'], color='blue', label='Casos')
plt.plot(dados_globais['Date'], dados_globais['Deaths'], color='red', label='Mortes')
plt.xlabel('Data')
plt.ylabel('Quantidade')
plt.title('Evolução Global de Casos e Mortes por COVID-19')
plt.xticks(rotation=45)
plt.grid(True)
plt.legend()
plt.tight_layout()
plt.show()




