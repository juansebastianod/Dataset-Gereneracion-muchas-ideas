# DATASET - GENERACION DE MUCHAS IDEAS
La generación de muchas ideas es una estrategia creativa que impulsa la innovación y la resolución de problemas al fomentar la producción de una amplia gama de conceptos sin restricciones iniciales.

# LLUVIA DE IDEAS 
Descripción
En el proceso de innovación de generación de muchas ideas para el análisis de datos, nos sumergimos en la técnica de lluvia de ideas enfocadas en pro de la tecnología sobre el desarrollo de distintos tipos de software enfocados en temas como lo son la salud, cultura, educación, entre otros. Cada paso está meticulosamente alineado para extraer el máximo valor de nuestro conjunto de datos.

# Recopilación de la Data
Datos internos (Archivos de texto, csv)
Repositorio de datos abiertos (undata opendata)
Broker de Datos (Experian, Acxiom)
APIS
Web scrapyn.

# Requisitos 
Python
Bibliotecas:
  pandas
  sklearn
  matplotlib

# Instalación

Asegúrate de tener Python instalado en el sistema.

Abre una terminal de comandos.

Ejecuta el siguiente comando para instalar las bibliotecas requeridas:

pip install pandas sklearn matplotlib


# Importar Bibliotecas y Cargar Datos

import pandas as pd
from sklearn.linear_model import LinearRegression
data = pd.read_csv('./honeyproduction.csv')
data

import matplotlib.pyplot as plt

# Ordenar los datos por la columna 'Votes' en orden descendente y seleccionar las 10 ideas principales
top_ideas = data.sort_values(by='Votes', ascending=False).head(10)


plt.figure(figsize=(10, 6))
plt.bar(top_ideas['Idea'], top_ideas['Votes'], color='skyblue')
plt.xlabel('Idea')
plt.ylabel('Votes')
plt.title('Top 10 Voted Ideas')
plt.xticks(rotation=45, ha='right')  
plt.show()

import matplotlib.pyplot as plt

# Filtra los datos para incluir solo los temas con más de 10 votos
data = data[data["Votes"] > 10]

# Crea un diccionario para almacenar la cantidad de votos para cada tema
votes_by_topic = {}

# Itera sobre las filas del DataFrame utilizando iterrows
for index, row in data.iterrows():
    topic = row["Topic"]
    votes = int(row["Votes"])

    if topic not in votes_by_topic:
        votes_by_topic[topic] = 0

    votes_by_topic[topic] += votes

# Crea una lista de los temas ordenados por la cantidad de votos
sorted_topics = sorted(votes_by_topic, key=lambda topic: votes_by_topic[topic], reverse=True)

# Extrae las variables labels y sizes para el gráfico de pastel
labels = sorted_topics
sizes = [votes_by_topic[topic] for topic in sorted_topics]

# Configura el título
plt.title("Distribution of Votes by Topic")

# Crea el gráfico de pastel
plt.pie(sizes, labels=labels, autopct='%1.1f%%', startangle=90, colors=plt.cm.Paired.colors)

# Muestra la gráfica
plt.axis('equal')  # Hace que el gráfico de pastel sea circular
plt.show()

import matplotlib.pyplot as plt
plt.scatter(data['ID'], data['Comments'], color = "yellow")
plt.show()

data.boxplot(column=['ID','Votes', 'Comments'])
