# 🧭 Torpedo de Formato de Texto en Python 🧩

> 💡 **f-strings** = cadenas con formato (empiezan con `f"..."`)  
> Dentro de `{}` puedes poner variables, operaciones o formatos especiales.  
> Ejemplo base:
>
> ```python
> nombre = "Aldo"
> edad = 30
> print(f"Hola {nombre}, tienes {edad} años")
> # Hola Aldo, tienes 30 años
> ```

---

## 🧱 Alineación y Espaciado

|    Símbolo     |                Significado                 | Ejemplo        | Resultado |
| :------------: | :----------------------------------------: | :------------- | :-------- |
|     `:<n`      | Alinear a la **izquierda** en `n` espacios | `f"{'id':<5}"` | `id   `   |
|     `:>n`      |  Alinear a la **derecha** en `n` espacios  | `f"{'id':>5}"` | `   id`   |
|     `:^n`      |        **Centrar** en `n` espacios         | `f"{'id':^5}"` | `id `     |
| _(sin número)_ |             No ajusta el ancho             | `f"{'id'}"`    | `id`      |

💬 _El número define el ancho total del campo (rellena con espacios si sobra)._

---

## 💲 Números y Decimales

| Símbolo | Significado                       | Ejemplo            | Resultado   |
| :-----: | :-------------------------------- | :----------------- | :---------- |
|  `.nf`  | Fijar `n` decimales               | `f"{3.14159:.2f}"` | `3.14`      |
|   `,`   | Separador de miles                | `f"{1234567:,}"`   | `1,234,567` |
|   `_`   | Separador con guion bajo          | `f"{1234567:_}"`   | `1_234_567` |
|   `+`   | Mostrar signo positivo o negativo | `f"{42:+}"`        | `+42`       |
|   `0`   | Rellenar con ceros a la izquierda | `f"{7:03}"`        | `007`       |

---

## 💯 Porcentajes y Otros Formatos

|  Símbolo  | Significado                | Ejemplo         | Resultado      |
| :-------: | :------------------------- | :-------------- | :------------- |
|    `%`    | Mostrar como porcentaje    | `f"{0.85:%}"`   | `85.000000%`   |
|   `.2%`   | Porcentaje con 2 decimales | `f"{0.85:.2%}"` | `85.00%`       |
| `e` / `E` | Notación científica        | `f"{12345:e}"`  | `1.234500e+04` |
|    `b`    | Binario                    | `f"{10:b}"`     | `1010`         |
| `x` / `X` | Hexadecimal (min/may)      | `f"{255:x}"`    | `ff`           |
|    `o`    | Octal                      | `f"{10:o}"`     | `12`           |

---

## 🧮 Combinaciones útiles

| Propósito                      | Ejemplo                        | Resultado           |
| :----------------------------- | :----------------------------- | :------------------ |
| Alinear texto en columnas      | `f"{'nombre':<10}{'edad':>5}"` | `nombre       edad` |
| Mostrar dinero con 2 decimales | `f"${precio:.2f}"`             | `$123.45`           |
| Números centrados con relleno  | `f"{42:^6}"`                   | `42`                |
| Separador de miles y decimales | `f"{1234567.89:,.2f}"`         | `1,234,567.89`      |

---

## 🪄 Ejemplo Visual Completo

```python
producto = "Mouse"
precio = 4990.5
cantidad = 3

print(f"{'Producto':<10}{'Precio':>10}{'Cantidad':>10}{'Total':>10}")
print("-" * 40)
print(f"{producto:<10}{precio:>10.2f}{cantidad:>10}{precio * cantidad:>10.2f}")
```

## 📤 Salida:

## Producto Precio Cantidad Total

Mouse 4990.50 3 14971.50

## 🌟 Mini referencia rápida

| Alineación | :<10 → izquierda | :>10 → derecha | :^10 → centrado |  
| Separadores | , → miles con coma | \_ → miles con guion bajo |  
| Decimales | .2f → 2 decimales |  
| Porcentaje | .2% → 2 decimales y símbolo % |  
| Signos | + muestra positivos y negativos |  
| Ceros a la izquierda | 07 → rellena con ceros |
