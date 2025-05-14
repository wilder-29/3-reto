# 3-reto
def obtener_primos_y_no_primos(n):
    if n < 2:
        return [], list(range(n + 1)), [False] * (n + 1)

    es_primo = [True] * (n + 1)
    es_primo[0] = es_primo[1] = False

    for i in range(2, int(n**0.5) + 1):
        if es_primo[i]:
            for j in range(i * i, n + 1, i):
                es_primo[j] = False

    primos = []
    no_primos = []

    for i in range(2, n + 1):
        if es_primo[i]:
            primos.append(i)
        else:
            no_primos.append(i)
             
    return primos, no_primos, es_primo


n = int(input("*Introduce un numero n: "))
primos, no_primos, es_primo_lista = obtener_primos_y_no_primos(n)

#Resultados
print(f"\n *Números primos hasta el numero {n}: {primos}")
print(f" *Números NO primos que estan dentro de {n}: {no_primos}")

# Verificar si el numero n es primo o no
if es_primo_lista[n]:
    print(f" {n} *ES primo.")
else:
    print(f" {n} *NO es primo.")
