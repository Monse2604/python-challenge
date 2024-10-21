<<<<<<< HEAD
# python-challenge
This is the homework for the Python module in the botcamp :)
=======
>>>>>>> c550ff449ab85aaa1cf565c0a45ca803c8323b0c
import pandas as pd

# Importar Archivo CSV
file_path = 'C:/Users/monse/assigment1/python-challenge/PyBank/Resources/budget_data.csv'

# Cargar el archivo CSV usando pandas
df = pd.read_csv(file_path)

# Total de meses en el dataset
total_months = df['Date'].nunique()

# Suma neta de "Profit/Losses" en todo el periodo
net_total = df['Profit/Losses'].sum()

# Calcular los cambios en "Profit/Losses" en todo el periodo
df['Change'] = df['Profit/Losses'].diff()

# Promedio de esos cambios
average_change = df['Change'].mean()

# Mayor aumento en ganancias (fecha y monto)
greatest_increase = df.loc[df['Change'].idxmax()]

# Mayor disminución en ganancias (fecha y monto)
greatest_decrease = df.loc[df['Change'].idxmin()]

# Crear el análisis financiero como un string
financial_analysis = (
    "Financial Analysis\n"
    "----------------------------\n"
    f"Total Months: {total_months}\n"
    f"Total: ${net_total}\n"
    f"Average Change: ${average_change:.2f}\n"
    f"Greatest Increase in Profits: {greatest_increase['Date']} (${greatest_increase['Change']})\n"
    f"Greatest Decrease in Profits: {greatest_decrease['Date']} (${greatest_decrease['Change']})\n"
)

# Definir la ruta para guardar el archivo
output_path = 'C:/Users/monse/assigment1/python-challenge/PyBank/Resources/financial_analysis.txt'

# Guardar el análisis financiero en un archivo de texto
with open(output_path, 'w') as file:
    file.write(financial_analysis)

# Imprimir el análisis financiero en la terminal
print(financial_analysis)

<<<<<<< HEAD

=======
>>>>>>> c550ff449ab85aaa1cf565c0a45ca803c8323b0c
