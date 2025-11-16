# CÓMO EVITAR `SettingWithCopyWarning` EN PANDAS

## 🔥 ¿Qué es este warning?

Aparece cuando Pandas **no sabe** si estás modificando:

- el DataFrame original (view), o
- una copia independiente.

Esto puede causar errores silenciosos.

---

## ❌ NO hacer (modificar una vista)

```python
df2 = df[df["Aprobado"] == True]
df2["Nota"] = 8.0   # ❌ Warning
```

---

## ✅ Solución 1 — Usar .copy() (lo mejor)

```python
df2 = df[df["Aprobado"] == True].copy()
df2["Nota"] = 8.0   # ✔ Sin warning
```

---

## ❌ NO hacer asignaciones encadenadas

```python
df[df["Aprobado"] == True]["Nota"] = 8.0   # ❌ Muy peligroso
```

---

## ❌ NO usar inplace=True sobre columnas

```python
df["Nota"].replace(7.0, 8.0, inplace=True)  # ❌ Puede romper todo
```

---

## ✅ Solución 2 — Reemplazar sobre el DataFrame completo

```python
df.replace({"Nota": {7.0: 8.0}}, inplace=True)  # ✔ Seguro
```

---

## ❌ NO modificar un slice sin .loc

```python
df2 = df[df["Edad"] > 20]
df2["Nota"] = 10    # ❌ Warning
```

---

## ✅ Solución 3 — Usar .loc siempre que sea posible

```python
df.loc[df["Edad"] > 20, "Nota"] = 10   # ✔ Seguro
```

---

## 🔥 Regla de oro

Cada vez que filtres un DataFrame y planees modificarlo, haz:

```python
df2 = df[filtro].copy()
```

| Problema                                  | Solución correcta                   |
| ----------------------------------------- | ----------------------------------- |
| Modificar vista de un DF                  | Usar `.copy()`                      |
| Asignación encadenada                     | Separar pasos o usar `.loc`         |
| Reemplazos con `inplace=True` en columnas | Evitar; usar asignación sin inplace |
| Filtro → cambio                           | `df.loc[filtro, "col"] = valor`     |
