# Tarea-2

def suma_vectores_complejos(v1, v2):
    return [v1[i] + v2[i] for i in range(len(v1))]

def inverso_aditivo_vector(v):
    return [-x for x in v]

def escalar_por_vector(escalar, v):
    return [escalar * x for x in v]

def suma_matrices_complejas(m1, m2):
    return [[m1[i][j] + m2[i][j] for j in range(len(m1[0]))] for i in range(len(m1))]

def inversa_aditiva_matriz(m):
    return [[-m[i][j] for j in range(len(m[0]))] for i in range(len(m))]

def escalar_por_matriz(escalar, m):
    return [[escalar * m[i][j] for j in range(len(m[0]))] for i in range(len(m))]

def transpuesta(m):
    return [[m[j][i] for j in range(len(m))] for i in range(len(m[0]))]

def conjugada(m):
    return [[x.conjugate() for x in fila] for fila in m]

def adjunta(m):
    return transpuesta(conjugada(m))

def producto_matrices(m1, m2):
    resultado = [[0] * len(m2[0]) for _ in range(len(m1))]
    for i in range(len(m1)):
        for j in range(len(m2[0])):
            resultado[i][j] = sum(m1[i][k] * m2[k][j] for k in range(len(m2)))
    return resultado

def accion_matriz_vector(m, v):
    return [sum(m[i][j] * v[j] for j in range(len(v))) for i in range(len(m))]

def producto_interno(v1, v2):
    return sum(v1[i].conjugate() * v2[i] for i in range(len(v1)))

def norma_vector(v):
    return sum(abs(x)**2 for x in v)**0.5

def distancia_entre_vectores(v1, v2):
    return norma_vector([v1[i] - v2[i] for i in range(len(v1))])

def valores_vectores_propios(m):
    a, b = m[0][0], m[0][1]
    c, d = m[1][0], m[1][1]
    traza = a + d
    determinante = a * d - b * c
    discriminante = (traza**2 - 4 * determinante)**0.5
    valor_prop_1 = (traza + discriminante) / 2
    valor_prop_2 = (traza - discriminante) / 2
    return [valor_prop_1, valor_prop_2]

def es_unitaria(m):
    identidad = [[1 if i == j else 0 for j in range(len(m))] for i in range(len(m))]
    producto = producto_matrices(m, adjunta(m))
    return all(abs(producto[i][j] - identidad[i][j]) < 1e-10 for i in range(len(m)) for j in range(len(m[0])))

def es_hermitiana(m):
    return m == adjunta(m)

def producto_tensor(m1, m2):
    filas1, columnas1 = len(m1), len(m1[0])
    filas2, columnas2 = len(m2), len(m2[0])
    return [[m1[i//filas2][j//columnas2] * m2[i % filas2][j % columnas2] for j in range(columnas1 * columnas2)] for i in range(filas1 * filas2)]

