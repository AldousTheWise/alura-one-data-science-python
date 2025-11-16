### RESUMEN DE groupby() EN PANDAS

## 🔹 ¿Qué es groupby()?

Es un método que agrupa filas según los valores de una o más columnas y luego permite aplicar funciones estadísticas (mean, sum, count, max, min, etc.) a cada grupo.

## 🔹 Patrón interno (muy importante)

`groupby()` funciona siguiendo el esquema:

1. Split → divide el DataFrame en grupos
2. Apply → aplica una función a cada grupo
3. Combine → reúne los resultados en una nueva tabla

---

## 🔹 Sintaxis básica

```python
df.groupby("columna")
```

**Para ver resultados necesitas aplicar una función:**

```python
df.groupby("columna").mean()
```

---

## 🔹 Agrupar y calcular el promedio (lo más usado)

```python
df.groupby("columna")["columna_numerica"].mean()
```

**Ejemplo:**

```python
df.groupby("Tipo")["Alquiler"].mean()
```

---

## 🔹 Seleccionar columnas antes o después

```python
df.groupby("Tipo")["Alquiler"].mean()
# o
df[["Tipo", "Alquiler"]].groupby("Tipo").mean()
```

---

## 🔹 Agrupar por varias columnas

```python
df.groupby(["col1", "col2"])["col_numerica"].mean()
```

---

## 🔹 Funciones más usadas con groupby()

| Función             | Qué hace                |
| ------------------- | ----------------------- |
| `.mean()`           | Promedio                |
| `.sum()`            | Suma                    |
| `.count()`          | Cuenta valores no nulos |
| `.size()`           | Cuenta filas del grupo  |
| `.min()` / `.max()` | Valor mínimo / máximo   |
| `.median()`         | Mediana                 |
| `.std()`            | Desviación estándar     |

---

## 🔹 Aplicar varias funciones a la vez

```python
df.groupby("Tipo")["Alquiler"].agg(["mean", "min", "max"])
```

**También puedes renombrarlas:**

```python
df.groupby("Tipo")["Alquiler"].agg(
    promedio = "mean",
    minimo = "min",
    maximo = "max"
)
```

---

## 🔹 Ignorar columnas no numéricas automáticamente

```python
df.groupby("Tipo").mean(numeric_only=True)
```

---

## 🔹 Ordenar resultados por el valor del grupo

```python
df.groupby("Tipo")["Alquiler"].mean().sort_values()
```

---

## 🔹 Convertir el resultado en DataFrame limpio

```python
df.groupby("Tipo")["Alquiler"].mean().reset_index()
```

---

## 🔹 Obtener el primer o último elemento de cada grupo

```python
df.groupby("Tipo").first()
df.groupby("Tipo").last()
```

---

## 🔹 Contar elementos por grupo (los dos más usados)

```python
df.groupby("Tipo").size()            # cuenta filas
df.groupby("Tipo")["Alquiler"].count()  # cuenta valores no nulos
```

---

## 🔹 Acceder a un grupo específico

```python
df.groupby("Tipo").get_group("Casa")
```

---

## 🔹 Agrupación con condición previa

```python
df[df["Alquiler"] > 400000].groupby("Tipo")["Alquiler"].mean()
```

---

## ❤️ Consejito de oro

Siempre especifica la columna numérica cuando uses .mean(), .sum(), .std(), etc., para evitar errores con columnas de texto.

**Ejemplo:**

```python
df.groupby("Tipo")["Precio"].mean()
```
