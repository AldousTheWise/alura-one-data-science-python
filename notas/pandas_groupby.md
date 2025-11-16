## 🔹 ¿Qué es `groupby()`?

Sirve para **agrupar** filas por una o más columnas y aplicar funciones estadísticas (mean, sum, count, max, min, etc.).  
Sigue el patrón: **Split → Apply → Combine**.

---

## 🔹 Sintaxis básica

```python
df.groupby("columna")
df.groupby("columna").mean()      # requiere una función para mostrar resultados
```

---

## 🔹 Promedio por grupo

```python
df.groupby("columna")["columna_numerica"].mean()
```

**Ejemplo:**

```python
df.groupby("Tipo")["Alquiler"].mean()
```

---

### 🔹 Seleccionar columnas antes o después

```python
df.groupby("Tipo")["Alquiler"].mean()
df[["Tipo", "Alquiler"]].groupby("Tipo").mean()
```

---

### 🔹 Agrupar por varias columnas

```python
df.groupby(["col1", "col2"])["col_numerica"].mean()
```

---

### 🔹 Funciones más comunes

```python
.mean()     # promedio
.sum()      # suma
.count()    # valores no nulos
.size()     # filas del grupo
.min()      # mínimo
.max()      # máximo
.median()   # mediana
.std()      # desviación estándar
```

---

### 🔹 Aplicar varias funciones

```python
df.groupby("Tipo")["Alquiler"].agg(["mean", "min", "max"])
```

**Con nombres:**

```python
df.groupby("Tipo")["Alquiler"].agg(
    promedio="mean",
    minimo="min",
    maximo="max"
)
```

---

### 🔹 Ignorar columnas no numéricas

```python
df.groupby("Tipo").mean(numeric_only=True)
```

---

### 🔹 Ordenar resultados

```python
df.groupby("Tipo")["Alquiler"].mean().sort_values()
```

---

### 🔹 Convertir a DataFrame limpio

```python
df.groupby("Tipo")["Alquiler"].mean().reset_index()
```

---

### 🔹 Primer o último valor de cada grupo

```python
df.groupby("Tipo").first()
df.groupby("Tipo").last()
```

---

### 🔹 Contar elementos por grupo

```python
df.groupby("Tipo").size()
df.groupby("Tipo")["Alquiler"].count()
```

---

### 🔹 Acceder a un grupo específico

```python
df.groupby("Tipo").get_group("Casa")
```

---

### 🔹 Agrupar después de una condición

```python
df[df["Alquiler"] > 400000]
  .groupby("Tipo")["Alquiler"]
  .mean()
```

---

### ⭐ Consejo final

Al usar `.mean()`, `.sum()`, `.std()` y similares, siempre especifica **la columna numérica** para evitar errores con texto.

\*\*\* Ejemplo:

```python
df.groupby("Tipo")["Precio"].mean()
```
