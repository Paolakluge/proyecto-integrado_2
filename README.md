# import pandas as pd
import random

# Crear el DataFrame simulado con las columnas clave
num_students = 100
subjects = ["Matemática", "Lengua", "Historia", "Geografía", "Ciencias Naturales", "Inglés"]
grades = [i for i in range(1, 11)]  # Calificaciones de 1 a 10
absences = [i for i in range(0, 31)]  # Faltas de 0 a 30

data = {
    "Materia Escolar": [random.choice(subjects) for _ in range(num_students)],
    "Nota 1er Trimestre": [random.choice(grades) for _ in range(num_students)],
    "Nota 2do Trimestre": [random.choice(grades) for _ in range(num_students)],
    "Nota 3er Trimestre": [random.choice(grades) for _ in range(num_students)],
    "Faltas a clases": [random.choice(absences) for _ in range(num_students)],
}

df = pd.DataFrame(data)

# Generar estadísticas descriptivas
statistics = df.groupby("Materia Escolar").agg(
    Promedio_1er_Trimestre=("Nota 1er Trimestre", "mean"),
    Promedio_2do_Trimestre=("Nota 2do Trimestre", "mean"),
    Promedio_3er_Trimestre=("Nota 3er Trimestre", "mean"),
    Total_Faltas=("Faltas a clases", "sum"),
    Promedio_Faltas=("Faltas a clases", "mean"),
)

statistics.reset_index(inplace=True)
statistics
