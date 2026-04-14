# Funciones y Modularidad

## Ejercicios prácticos

1. Escribe en pseudocódigo una función que convierta Celsius a Fahrenheit y otra que convierta Fahrenheit a Celsius. Invoca ambas en secuencia.
2. Escribe en pseudocódigo una función que reciba una lista de números y muestre el promedio, el máximo y el mínimo.
3. Analiza la siguiente función, identifica cuántas responsabilidades tiene y divídela:

```
FUNCIÓN registrarUsuario(nombre, correo, contrasena)
  SI nombre == "" ENTONCES
    MOSTRAR "El nombre es obligatorio"
  FIN SI
  SI correo no contiene "@" ENTONCES
    MOSTRAR "El correo no es válido"
  FIN SI
  SI longitud(contrasena) < 8 ENTONCES
    MOSTRAR "La contraseña debe tener al menos 8 caracteres"
  FIN SI
  guardar(nombre, correo, contrasena)
  MOSTRAR "Usuario registrado correctamente"
FIN FUNCIÓN
```

4. Revisa el siguiente pseudocódigo e identifica qué comentarios son útiles y cuáles son ruido. Reescríbelo con solo los comentarios que agregan valor:

```
// Declara la variable i
i = 0

// Incrementa el contador mientras i sea menor que 10
MIENTRAS i < 10 HACER
  i = i + 1   // suma 1 a i
FIN MIENTRAS

// Esta función calcula el área
FUNCIÓN calcularArea(b, h)
  // multiplica b por h
  RETORNAR b * h   // retorna el resultado
FIN FUNCIÓN
```

5. Evalúa el siguiente pseudocódigo y verifica si cumple con DRY, KISS y YAGNI. Documenta qué cambiarías y por qué.

```
FUNCIÓN calcularSubtotal(productos)
  total = 0
  PARA CADA p EN productos HACER
    total = total + p.precio * p.cantidad
  FIN PARA
  RETORNAR total
FIN FUNCIÓN

FUNCIÓN aplicarDescuento(subtotal, porcentaje)
  RETORNAR subtotal - (subtotal * porcentaje)
FIN FUNCIÓN

FUNCIÓN calcularIVA(base, porcentaje)
  RETORNAR base * porcentaje
FIN FUNCIÓN

FUNCIÓN calcularTotal(base, iva)
  RETORNAR base + iva
FIN FUNCIÓN

FUNCIÓN mostrarFactura(subtotal, descuento, iva, total)
  MOSTRAR "Subtotal:  $", subtotal
  MOSTRAR "Descuento: $", descuento
  MOSTRAR "IVA:       $", iva
  MOSTRAR "Total:     $", total
FIN FUNCIÓN
```

6. Refactoríza la siguiente función, aplicando el principio de responsabilidad única, separando validación, autenticación y presentación. Explica qué cambió y por qué el nuevo diseño es mejor.

```
FUNCIÓN login(usuario, contrasena)
  SI usuario == "" O contrasena == "" ENTONCES
    MOSTRAR "Error: campos vacíos"
    RETORNAR Falso
  FIN SI

  SI usuario == "admin" Y contrasena == "segura123" ENTONCES
    MOSTRAR "Bienvenido, ", usuario
    RETORNAR Verdadero
  SINO
    MOSTRAR "Credenciales incorrectas"
    RETORNAR Falso
  FIN SI
FIN FUNCIÓN

login("admin", "segura123")
login("admin", "")
login("usuario", "clave")
```
