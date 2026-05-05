# Tecnología de la Programación

## Tercer Examen Parcial Versión B

### Parte Teórica (40%)

Responde de manera clara, estructurada y argumentada.

1. Explica qué es la modularidad en programación. ¿Cuáles son sus tres ventajas principales? Describe cómo se organizaría en módulos un programa real de tu elección e identifica la responsabilidad de cada módulo.
2. Define qué es una estructura de datos. Explica la diferencia entre una lista, un conjunto y un diccionario, e indica con un ejemplo real cuándo usarías cada una.
3. Explica qué es una pila y qué es una cola. ¿En qué se diferencian en cuanto a su orden de acceso? Da un ejemplo de un problema real que se resuelva mejor con una pila y otro que se resuelva mejor con una cola.
4. Explica los conceptos de clase, objeto, atributo y método en la Programación Orientada a Objetos. ¿Cuál es la diferencia entre una clase y un objeto? Incluye un ejemplo en pseudocódigo.

### Parte Práctica (60%)

En cada ejercicio debes entregar:

1. Algoritmo en pseudocódigo correctamente estructurado, organizado con funciones.
2. Diagrama de flujo que represente el flujo principal del algoritmo.

#### Ejercicio 1 (30%)

**Validador de acceso modular**

Diseña un algoritmo organizado en funciones con responsabilidad única que:

- Solicite un nombre de usuario y una contraseña.
- Valide que el nombre de usuario no esté vacío (función independiente).
- Valide que la contraseña tenga al menos 8 caracteres (función independiente).
- Verifique si las credenciales son correctas comparando con valores definidos como constantes: usuario = "admin", contraseña = "segura123" (función independiente).
- Muestre el resultado: "Acceso concedido" o el motivo específico del rechazo.
- El programa principal debe coordinar las funciones en el orden correcto.

#### Ejercicio 2 (30%)

**Sistema de inventario con diccionario**

Diseña un algoritmo que utilice un diccionario para gestionar un inventario de productos y que incluya:

- Un diccionario con al menos 4 productos, donde la clave es el nombre del producto y el valor es su stock disponible.
- Una función que muestre todos los productos y su stock actual.
- Una función que identifique y muestre los productos con stock bajo (menos de 5 unidades).
- Una función que calcule y muestre el total de unidades en inventario.
- El programa principal debe llamar a cada función en orden lógico y mostrar los resultados claramente.
