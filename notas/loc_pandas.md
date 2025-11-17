# .loc[] en Pandas (Guía Rápida)

`.loc[]` es la forma más poderosa y flexible de seleccionar, filtrar y modificar datos en un DataFrame.

---

## 🔹 Sintaxis básica

```python
df.loc[filas, columnas]
```

- **filas** → qué filas quieres (índices, listas o condiciones).
- **columnas** → qué columnas quieres.

---

## 🧠 Selección de filas

### ✔ Seleccionar una fila por índice

```python
df.loc[3]
```

---

### ✔ Seleccionar varias filas por índice

```python
df.loc[[1, 4, 7]]
```

---

### ✔ Seleccionar un rango de filas

```python
df.loc[2:6]
```

---

## 🧠 Selección de columnas

### ✔ Una sola columna

```python
df.loc[:, 'Precio']
```

---

### ✔ Varias columnas

```python
df.loc[:, ['Tipo', 'Colonia', 'Precio']]
```

---

### ✔ Todas las columnas (equivalente a df.loc[filas])

```python
df.loc[5]
```

---

## 🔥 Selección condicional

Estas son las que más vas a usar.

### ✔ Filas donde una columna cumpla una condición

```python
df.loc[df['Garages'] > 0]
```

---

### ✔ Filas donde se cumplan múltiples condiciones

```python
df.loc[(df['Precio'] > 2000000) & (df['Colonia'] == 'Centro')]
```

---

**Operadores:**

- & → AND
- | → OR
- ~ → NOT

---

## ✏️ Modificar valores con .loc[]

### ✔ Cambiar valores según una condición

```python
df.loc[df['Habitaciones'] == 1, 'Habitaciones'] = 'Una'
```

---

### ✔ Cambiar múltiples columnas a la vez

```python
df.loc[df['Garages'] == 0, ['Garages', 'Descripcion']] = [None, 'Sin garage']
```

---

## 🧩 Uso combinado (filtrar + asignar)

### ✔ Crear una columna con condición

```python
df.loc[df['Precio'] > 3000000, 'Categoria'] = 'Premium'
df.loc[df['Precio'] <= 3000000, 'Categoria'] = 'Estandar'
```

---

## 📦 Comparación rápida: .loc[] vs .iloc[]

| Método    | Selección por                        | Ejemplo                           |
| --------- | ------------------------------------ | --------------------------------- |
| `.loc[]`  | **etiquetas** (nombres, condiciones) | `df.loc[df['Colonia']=='Centro']` |
| `.iloc[]` | **posición numérica**                | `df.iloc[0:5, 2]`                 |

---

## 🛠️ Ejemplo útil en tu proyecto (caso “Garages”)

```python
datos['Descripcion'] = (
datos['Tipo'] + ' en ' + datos['Colonia'] +
' con ' + datos['Habitaciones'].astype(str) + ' habitacion(es)'
)

mask = datos['Garages'].fillna(0) > 0

# Donde hay garages

datos.loc[mask, 'Descripcion'] += (
' y ' + datos.loc[mask, 'Garages'].astype(int).astype(str) + ' garage(s).'
)

# Donde no hay garage

datos.loc[~mask, 'Descripcion'] += '.'
```

---

## 🎯 Resumen express

```python
df.loc[filtro, columna] = valor
df.loc[df['X'] > 10, ['A','B']]
df.loc[:, 'Columna']
df.loc[2:5, :]
df.loc[(cond1) & (cond2)]
```
