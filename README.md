# proyecto_prueba1

``` python
"""
Código que simula el ordenamiento del horario en una tarde. Cada materia dura
una hora.
"""

import random

class Materia:
    def __init__(self, nombre: str, grupo: int, profesor: str, horario: int) -> None:
        self.nombre = nombre
        self.grupo = grupo
        self.profesor = profesor
        self.horario = horario

    def __str__(self) -> str:
        return f"""Materia: {self.nombre} 
        \t Profesor: {self.profesor} 
        \t Grupo: {self.grupo} 
        \t Horario: {self.horario} P.M."""
    

# Función para seleccionar una materia de una lista evitando conflictos de horarios
def seleccionar(opciones: list[Materia], seleccionadas: list[Materia]) -> Materia:
    while True:
        seleccion = random.choice(opciones) # Elegir una materia al azar, aunque esto después se cambia priorizando las preferencias del usuario
        horarios_ocupados = [materia.horario for materia in seleccionadas]
        if seleccion.horario not in horarios_ocupados:
            return seleccion
        
# Materias con sus informaciones
calculo = [Materia("Calculo", 4, "Alex", 1),
           Materia("Calculo", 3, "Albert", 1),
           Materia("Calculo", 1, "Anthony", 3),
           Materia("Calculo", 2, "Anna", 2)]

algebra = [Materia("Algebra", 2, "Adam", 4),
           Materia("Algebra", 1, "Adrian", 2),
           Materia("Algebra", 3, "Angie", 2),
           Materia("Algebra", 4, "Ammelia", 3)]

fisica = [Materia("Fisica", 2, "Alexandra", 1),
          Materia("Fisica", 1, "Abraham", 3),
          Materia("Fisica", 3, "Adolf", 4),
          Materia("Fisica", 4, "Alan", 4)]

materias = [calculo, algebra, fisica]
seleccionadas = []


# Selección de materias
for materia in materias:
    seleccion = seleccionar(materia, seleccionadas)
    seleccionadas.append(seleccion)

# Mostrar selección final
print("Materias seleccionadas:")
for materia in seleccionadas:
    print("_" * 40)
    print(materia)

```
