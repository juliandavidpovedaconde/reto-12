# reto-12
```python
# 1. Ordenar valores de un diccionario en orden ascendente
# Diccionario de ejemplo
datos = {"uno": 5, "dos": 2, "tres": 9, "cuatro": 1}

# Extraer valores y ordenar con bubble sort
valores = []
for clave in datos:
    valores.append(datos[clave])

for i in range(len(valores)):
    for j in range(len(valores) - 1):
        if valores[j] > valores[j+1]:
            aux = valores[j]
            valores[j] = valores[j+1]
            valores[j+1] = aux

# Imprimir resultados
print("Valores ordenados:")
for v in valores:
    print(v)

# 2. Mezclar dos diccionarios
def mezclar_diccionarios(dic1, dic2):
    resultado = {}
    # Copiar todos los pares de dic2
    for clave in dic2:
        resultado[clave] = dic2[clave]
    # Copiar todos los pares de dic1 (reemplaza si existe)
    for clave in dic1:
        resultado[clave] = dic1[clave]
    return resultado

# Ejemplo
_d1 = {"a": 1, "b": 2, "c": 3}
_d2 = {"b": 9, "d": 4}
mez = mezclar_diccionarios(_d1, _d2)
print("Diccionario mezclado:")
print(mez)

# 3. Buscar datos en un archivo JSON
import json
# Leer archivo JSON
ing = open("personas.json", "r", encoding="utf-8")
datos_json = json.load(ing)
ing.close()

# Buscar por deporte
deporte = input("Ingrese un deporte para buscar: ")
print("Personas que practican " + deporte + ":")
for clave in datos_json:
    usuario = datos_json[clave]
    for d in usuario["deportes"]:
        if d == deporte:
            nombre = usuario["nombres"] + " " + usuario["apellidos"]
            print(nombre)

# Buscar por rango de edad
min_edad = int(input("Ingrese edad mínima: "))
max_edad = int(input("Ingrese edad máxima: "))
print("Personas entre " + str(min_edad) + " y " + str(max_edad) + " años:")
for clave in datos_json:
    usuario = datos_json[clave]
    if min_edad <= usuario["edad"] <= max_edad:
        nombre = usuario["nombres"] + " " + usuario["apellidos"]
        print(nombre)

# 4. Consumir 3 APIs y mostrar pares clave:valor
import requests

def imprimir_pares(dic):
    for clave in dic:
        print(clave + ": " + str(dic[clave]))

# API 1: Cat Fact
resp1 = requests.get("https://catfact.ninja/fact")
d1 = resp1.json()
print("Cat Fact:")
imprimir_pares(d1)
print("")

# API 2: Bored API
resp2 = requests.get("https://www.boredapi.com/api/activity")
d2 = resp2.json()
print("Actividad sugerida:")
imprimir_pares(d2)
print("")

# API 3: Dog CEO
resp3 = requests.get("https://dog.ceo/api/breeds/image/random")
d3 = resp3.json()
print("Imagen de perro aleatoria:")
imprimir_pares(d3)
