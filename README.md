Dada una matriz de 9x9 y suponiendo que los valores de la misma es la solución dada por un usuario,hacer un programa que haga las sumas correspondientes y determine si la solución dada es correcta.




def es_valida(matriz):
    # Verificar filas
    for fila in matriz:
        if sorted(fila) != list(range(1, 10)):
            return False

    # Verificar columnas
    for col in range(9):
        columna = [matriz[fila][col] for fila in range(9)]
        if sorted(columna) != list(range(1, 10)):
            return False

    # Verificar subcuadros 3x3
    for i in range(0, 9, 3):
        for j in range(0, 9, 3):
            subcuadro = []
            for k in range(3):
                for l in range(3):
                    subcuadro.append(matriz[i + k][j + l])
            if sorted(subcuadro) != list(range(1, 10)):
                return False

    return True

Ejemplo de uso
solucion = [
    [5,3,4,6,7,8,9,1,2],
    [6,7,2,1,9,5,3,4,8],
    [1,9,8,3,4,2,5,6,7],
    [8,5,9,7,6,1,4,2,3],
    [4,2,6,8,5,3,7,9,1],
    [7,1,3,9,2,4,8,5,6],
    [9,6,1,5,3,7,2,8,4],
    [2,8,7,4,1,9,6,3,5],
    [3,4,5,2,8,6,1,7,9]
]

if es_valida(solucion):
    print("La solución es válida.")
else:
    print("La solución es incorrecta.")
