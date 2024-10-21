import csv

# Ruta del archivo CSV
file_path = 'C:/Users/monse/assigment1/python-challenge/PyPoll/Resources/election_data.csv'

# Inicializar variables
total_votes = 0
candidates = {}
winner = ""
winning_votes = 0

# Leer el archivo CSV
with open(file_path, newline='') as csvfile:
    csvreader = csv.reader(csvfile)
    next(csvreader)  # Omitir el encabezado

    # Contar votos y candidatos
    for row in csvreader:
        total_votes += 1
        candidate = row[2]
        if candidate in candidates:
            candidates[candidate] += 1
        else:
            candidates[candidate] = 1

# Generar resultados
result = "Election Results\n"
result += "-------------------------\n"
result += f"Total Votes: {total_votes}\n"
result += "-------------------------\n"

for candidate, votes in candidates.items():
    percentage = (votes / total_votes) * 100
    result += f"{candidate}: {percentage:.3f}% ({votes})\n"
    if votes > winning_votes:
        winner = candidate
        winning_votes = votes

result += "-------------------------\n"
result += f"Winner: {winner}\n"
result += "-------------------------\n"

# Imprimir resultados en la terminal
print(result)

# Guardar resultados en un archivo de texto
output_file = 'C:/Users/monse/assigment1/python-challenge/PyPoll/Resources/election_results.txt'
with open(output_file, 'w') as file:
    file.write(result)
