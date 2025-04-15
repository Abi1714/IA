Dada una matriz de 9x9 y suponiendo que los valores de la misma es la solución dada por un usuario,hacer un programa que haga las sumas correspondientes y determine si la solución dada es correcta.




def es_valido(lista):
    return sorted(lista) == list(range(1, 10))

def validar_sudoku(matriz):
    # Validar filas
    for fila in matriz:
        if not es_valido(fila):
            return False

    # Validar columnas
    for col in range(9):
        columna = [matriz[fila][col] for fila in range(9)]
        if not es_valido(columna):
            return False

    # Validar subcuadros 3x3
    for fila in range(0, 9, 3):
        for col in range(0, 9, 3):
            subcuadro = []
            for i in range(3):
                for j in range(3):
                    subcuadro.append(matriz[fila + i][col + j])
            if not es_valido(subcuadro):
                return False

    return True

# Ejemplo de uso
sudoku = [
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

if validar_sudoku(sudoku):
    print("La solución es válida.")
else:
    print("La solución es incorrecta.")
