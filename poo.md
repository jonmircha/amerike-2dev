# Programación Orientada a Objetos

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

La programación orientada a objetos no es solo una forma de escribir código: es una forma de modelar el problema.

Antes de escribir una clase, hay que pensar en términos de entidades, responsabilidades y relaciones:

- Qué cosas existen en el problema.
- Qué sabe cada una.
- Qué puede hacer.
- Cómo se relacionan entre sí.

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## Clases y objetos

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

Una **clase** es una plantilla que define la estructura y el comportamiento de un tipo de entidad.

Un **objeto** es una instancia concreta de esa plantilla: un ejemplar específico con sus propios datos.

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

La clase define qué atributos tendrá cada objeto y qué métodos podrá ejecutar.

El objeto es la realización de esa definición en memoria: tiene valores concretos en sus atributos y puede invocar los métodos definidos por su clase.

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

### Ejemplo cotidiano

El plano de una casa es una clase: define cuántas habitaciones habrá, dónde va la cocina, qué dimensiones tiene cada cuarto.

Una casa construida con ese plano es un objeto: existe en una dirección concreta, tiene un color de fachada específico, pertenece a alguien.

Puedes construir diez casas con el mismo plano: cada una es un objeto distinto que comparte la misma estructura.

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

### Ejemplo conceptual

```
CLASE Persona
  ATRIBUTOS
    nombre
    edad

  CONSTRUCTOR(nombre, edad)
    this.nombre = nombre
    this.edad = edad
  FIN CONSTRUCTOR

  MÉTODO saludar()
    MOSTRAR "Hola, soy ", this.nombre, " y tengo ", this.edad, " años."
  FIN MÉTODO
FIN CLASE

// Instanciación: crear objetos a partir de la clase
p1 = nueva Persona("Ana", 30)
p2 = nueva Persona("Bruno", 25)

p1.saludar()   ← Hola, soy Ana y tengo 30 años.
p2.saludar()   ← Hola, soy Bruno y tengo 25 años.
```

`p1` y `p2` son dos objetos distintos creados a partir de la misma clase. Comparten estructura pero tienen datos independientes.

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

### Ejemplos en código

#### JavaScript

```javascript
class Persona {
  constructor(nombre, edad) {
    this.nombre = nombre;
    this.edad = edad;
  }

  saludar() {
    console.log(`Hola, soy ${this.nombre} y tengo ${this.edad} años.`);
  }
}

const p1 = new Persona("Ana", 30);
const p2 = new Persona("Bruno", 25);

p1.saludar(); // Hola, soy Ana y tengo 30 años.
p2.saludar(); // Hola, soy Bruno y tengo 25 años.

console.log(p1 instanceof Persona); // true
console.log(p1 === p2); // false: son objetos distintos
```

#### Python

```python
class Persona:
    def __init__(self, nombre, edad):
        self.nombre = nombre
        self.edad = edad

    def saludar(self):
        print(f"Hola, soy {self.nombre} y tengo {self.edad} años.")

p1 = Persona("Ana", 30)
p2 = Persona("Bruno", 25)

p1.saludar()  # Hola, soy Ana y tengo 30 años.
p2.saludar()  # Hola, soy Bruno y tengo 25 años.

print(isinstance(p1, Persona))  # True
print(p1 is p2)                 # False: son objetos distintos
```

#### C#

```csharp
class Persona
{
    public string Nombre;
    public int Edad;

    public Persona(string nombre, int edad)
    {
        Nombre = nombre;
        Edad = edad;
    }

    public void Saludar()
    {
        Console.WriteLine($"Hola, soy {Nombre} y tengo {Edad} años.");
    }
}

var p1 = new Persona("Ana", 30);
var p2 = new Persona("Bruno", 25);

p1.Saludar(); // Hola, soy Ana y tengo 30 años.
p2.Saludar(); // Hola, soy Bruno y tengo 25 años.

Console.WriteLine(p1 is Persona); // True
Console.WriteLine(p1 == p2);      // False: son objetos distintos
```

#### Java

```java
public class Main {
    static class Persona {
        String nombre;
        int edad;

        Persona(String nombre, int edad) {
            this.nombre = nombre;
            this.edad = edad;
        }

        void saludar() {
            System.out.println("Hola, soy " + nombre + " y tengo " + edad + " años.");
        }
    }

    public static void main(String[] args) {
        Persona p1 = new Persona("Ana", 30);
        Persona p2 = new Persona("Bruno", 25);

        p1.saludar(); // Hola, soy Ana y tengo 30 años.
        p2.saludar(); // Hola, soy Bruno y tengo 25 años.

        System.out.println(p1 instanceof Persona); // true
        System.out.println(p1 == p2);              // false: son objetos distintos
    }
}
```

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

### Errores comunes

- Confundir la clase con el objeto es el error de partida.
- La clase no tiene datos propios: define cómo serán los datos de cada objeto.
- Cuando dices `Persona p1 = new Persona("Ana", 30)`, el objeto que vive en memoria es `p1`, no `Persona`.
- Crear una clase para todo, incluyendo conceptos que son simples valores, es otro error frecuente.
- Si un dato es un número o una cadena de texto sin comportamiento asociado, no necesita ser una clase.

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## Atributos y métodos

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## Atributos y métodos

Los **atributos** son los datos que un objeto almacena. Representan el estado de la entidad en un momento dado.

Los **métodos** son las funciones que definen su comportamiento: las acciones que puede realizar y las operaciones que puede exponer.

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

Un objeto bien diseñado tiene atributos que describen su estado y métodos que operan sobre ese estado.

Los métodos no solo realizan acciones: son la interfaz a través de la cual el mundo exterior interactúa con el objeto.

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

### El constructor

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

El **constructor** es un método especial que se ejecuta automáticamente cuando se crea un nuevo objeto.

Su propósito es inicializar los atributos de la instancia con los valores iniciales que el objeto necesita para existir en un estado válido.

No se invoca manualmente: el lenguaje lo llama en el momento de la instanciación.

Cada lenguaje tiene su propia sintaxis para definirlo, pero el comportamiento es el mismo en todos: recibe los datos necesarios para crear el objeto y los asigna a los atributos correspondientes.

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

```
CLASE Persona
  CONSTRUCTOR(nombre, edad)
    this.nombre = nombre ← inicializa atributos al crear el objeto
    this.edad = edad
  FIN CONSTRUCTOR
FIN CLASE

p = nueva Persona("Ana", 30) ← el constructor se ejecuta aquí
```

Un constructor puede tener validaciones. Si un atributo no puede tener ciertos valores, el constructor es el lugar correcto para establecer esa restricción desde el primer momento.

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

### Atributos y métodos de instancia y de clase

Los atributos y métodos pueden ser de instancia o de clase.

Los de **instancia** pertenecen a cada objeto individualmente: cada objeto tiene sus propios valores.

Los de **clase** (también llamados estáticos) pertenecen a la clase en sí y son compartidos por todas las instancias.

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

### Ejemplo cotidiano

- Una cuenta de banco tiene atributos de instancia: número de cuenta, titular, saldo.
- Esos datos son distintos para cada cuenta.
- El banco también puede tener un atributo de clase: la tasa de interés vigente.
- Es el mismo valor para todas las cuentas porque pertenece a la institución, no a una cuenta específica.

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

### Ejemplo conceptual

```
CLASE Producto
  // Atributo de clase: compartido por todas las instancias
  ATRIBUTO_DE_CLASE IVA = 0.16

  // Atributos de instancia: propios de cada objeto
  ATRIBUTOS
    nombre
    precioBase

  CONSTRUCTOR(nombre, precioBase)
    this.nombre = nombre
    this.precioBase = precioBase
  FIN CONSTRUCTOR

  // Método de instancia
  MÉTODO precioFinal()
    RETORNAR this.precioBase + (this.precioBase \* Producto.IVA)
  FIN MÉTODO

  // Método de clase
  MÉTODO_DE_CLASE actualizarIVA(nuevoIVA)
    Producto.IVA = nuevoIVA
  FIN MÉTODO
FIN CLASE

p1 = nuevo Producto("Teclado", 500)
p2 = nuevo Producto("Mouse", 200)

MOSTRAR p1.precioFinal() ← 580
MOSTRAR p2.precioFinal() ← 232

Producto.actualizarIVA(0.08) // cambia para todas las instancias

MOSTRAR p1.precioFinal() ← 540
MOSTRAR p2.precioFinal() ← 216
```

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

### Ejemplos en código

#### JavaScript

```javascript
class Producto {
  static IVA = 0.16; // atributo de clase

  constructor(nombre, precioBase) {
    // El constructor inicializa los atributos de cada instancia
    this.nombre = nombre; // atributo de instancia
    this.precioBase = precioBase; // atributo de instancia
  }

  // Método de instancia
  precioFinal() {
    return this.precioBase + this.precioBase * Producto.IVA;
  }

  // Método de clase
  static actualizarIVA(nuevoIVA) {
    Producto.IVA = nuevoIVA;
  }
}

const p1 = new Producto("Teclado", 500);
const p2 = new Producto("Mouse", 200);

console.log(p1.precioFinal()); // 580
console.log(p2.precioFinal()); // 232

Producto.actualizarIVA(0.08);

console.log(p1.precioFinal()); // 540
console.log(p2.precioFinal()); // 216
```

#### Python

```python
class Producto:
    IVA = 0.16  # atributo de clase

    def __init__(self, nombre, precio_base):
        # __init__ es el constructor en Python
        # se ejecuta automáticamente al crear cada instancia
        self.nombre = nombre           # atributo de instancia
        self.precio_base = precio_base # atributo de instancia

    # Método de instancia
    def precio_final(self):
        return self.precio_base + self.precio_base * Producto.IVA

    # Método de clase
    @classmethod
    def actualizar_iva(cls, nuevo_iva):
        cls.IVA = nuevo_iva

p1 = Producto("Teclado", 500)
p2 = Producto("Mouse", 200)

print(p1.precio_final())  # 580.0
print(p2.precio_final())  # 232.0

Producto.actualizar_iva(0.08)

print(p1.precio_final())  # 540.0
print(p2.precio_final())  # 216.0
```

#### C#

```csharp
class Producto
{
    public static double IVA = 0.16; // atributo de clase

    public string Nombre;            // atributo de instancia
    public double PrecioBase;        // atributo de instancia

    // El constructor tiene el mismo nombre que la clase
    public Producto(string nombre, double precioBase)
    {
        Nombre = nombre;
        PrecioBase = precioBase;
    }

    // Método de instancia
    public double PrecioFinal() => PrecioBase + PrecioBase * IVA;

    // Método de clase
    public static void ActualizarIVA(double nuevoIVA) => IVA = nuevoIVA;
}

var p1 = new Producto("Teclado", 500);
var p2 = new Producto("Mouse", 200);

Console.WriteLine(p1.PrecioFinal()); // 580
Console.WriteLine(p2.PrecioFinal()); // 232

Producto.ActualizarIVA(0.08);

Console.WriteLine(p1.PrecioFinal()); // 540
Console.WriteLine(p2.PrecioFinal()); // 216
```

#### Java

```java
public class Main {
    static class Producto {
        static double IVA = 0.16; // atributo de clase

        String nombre;            // atributo de instancia
        double precioBase;        // atributo de instancia

        // El constructor tiene el mismo nombre que la clase
        Producto(String nombre, double precioBase) {
            this.nombre = nombre;
            this.precioBase = precioBase;
        }

        // Método de instancia
        double precioFinal() {
            return precioBase + precioBase * IVA;
        }

        // Método de clase
        static void actualizarIVA(double nuevoIVA) {
            IVA = nuevoIVA;
        }
    }

    public static void main(String[] args) {
        Producto p1 = new Producto("Teclado", 500);
        Producto p2 = new Producto("Mouse", 200);

        System.out.println(p1.precioFinal()); // 580.0
        System.out.println(p2.precioFinal()); // 232.0

        Producto.actualizarIVA(0.08);

        System.out.println(p1.precioFinal()); // 540.0
        System.out.println(p2.precioFinal()); // 216.0
    }
}
```

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

### Errores comunes

- Acceder directamente a los atributos de un objeto desde fuera de la clase en lugar de usar métodos es el error más frecuente.
- Hacerlo rompe el encapsulamiento: cualquier parte del programa puede modificar el estado del objeto sin pasar por la validación que el método debería aplicar.
- Usar atributos de clase cuando se necesitan atributos de instancia produce el error opuesto: todos los objetos comparten el mismo valor y modificarlo en uno lo cambia en todos.
- Ese comportamiento puede ser intencional o un bug silencioso dependiendo del contexto.
- Omitir el constructor y asignar atributos después de la instanciación es otro error frecuente.
- Un objeto debería nacer en un estado válido, no a medias.
- Si para usar el objeto es necesario llamar métodos adicionales después de `new`, el constructor está incompleto.

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## Encapsulamiento

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

El encapsulamiento es el principio de proteger el estado interno de un objeto ocultando sus atributos y exponiendo solo los métodos necesarios para interactuar con ellos.

El objetivo no es el secreto: es el control. Quien usa el objeto no necesita saber cómo está implementado por dentro. Solo necesita saber qué puede pedirle.

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

Un atributo no protegido puede ser modificado desde cualquier parte del programa, sin validación, sin aviso. Un atributo encapsulado solo puede cambiar a través de métodos que aplican las reglas de negocio correspondientes.

Los niveles de acceso más comunes son:

- **Privado:** solo accesible desde la misma clase.
- **Protegido:** accesible desde la clase y sus subclases.
- **Público:** accesible desde cualquier parte del programa.

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

### Ejemplo cotidiano

El velocímetro de un automóvil muestra la velocidad actual, pero no te permite modificarla directamente.

Para cambiar la velocidad usas el acelerador o el freno. Esos son los métodos públicos.

El mecanismo interno que calcula y almacena la velocidad es privado.

El encapsulamiento no te oculta la velocidad: te obliga a cambiarla por los canales correctos.

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

### Ejemplo conceptual

```
CLASE CuentaBancaria
  ATRIBUTOS (privados)
    saldo
    titular

  CONSTRUCTOR(titular, saldoInicial)
    this.titular = titular
    this.saldo = SI saldoInicial >= 0 ENTONCES saldoInicial SINO 0
  FIN CONSTRUCTOR

  MÉTODO depositar(monto)
    SI monto > 0 ENTONCES
      this.saldo = this.saldo + monto
    FIN SI
  FIN MÉTODO

  MÉTODO retirar(monto)
    SI monto > 0 Y monto <= this.saldo ENTONCES
      this.saldo = this.saldo - monto
      RETORNAR Verdadero
    SINO
      RETORNAR Falso
    FIN SI
  FIN MÉTODO

  MÉTODO obtenerSaldo()
    RETORNAR this.saldo
  FIN MÉTODO
FIN CLASE

cuenta = nueva CuentaBancaria("Elena", 1000)
cuenta.saldo = -5000   ← ERROR: atributo privado, no accesible desde fuera
cuenta.retirar(500)    ← correcto: pasa por validación
```

El saldo no puede ser manipulado directamente. Cada operación pasa por un método que valida la lógica de negocio.

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

### Getters y setters

Cuando se necesita exponer un atributo privado para lectura o escritura controlada, se usan métodos de acceso:

- El **getter** retorna el valor.
- El **setter** lo modifica aplicando validación.

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

```
MÉTODO obtenerSaldo()       ← getter: solo lectura
  RETORNAR this.saldo
FIN MÉTODO

MÉTODO establecerSaldo(valor)  ← setter: escritura con validación
  SI valor >= 0 ENTONCES
    this.saldo = valor
  FIN SI
FIN MÉTODO
```

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

### Ejemplos en código

#### JavaScript

```javascript
class CuentaBancaria {
  #saldo;
  #titular;

  constructor(titular, saldoInicial) {
    this.#titular = titular;
    this.#saldo = saldoInicial >= 0 ? saldoInicial : 0;
  }

  depositar(monto) {
    if (monto > 0) this.#saldo += monto;
  }

  retirar(monto) {
    if (monto > 0 && monto <= this.#saldo) {
      this.#saldo -= monto;
      return true;
    }
    return false;
  }

  // Getter: solo lectura
  get saldo() {
    return this.#saldo;
  }
  get titular() {
    return this.#titular;
  }
}

const cuenta = new CuentaBancaria("Elena", 1000);
cuenta.depositar(500);
cuenta.retirar(200);

console.log(cuenta.saldo); // 1300
console.log(cuenta.titular); // Elena
// cuenta.#saldo = 9999;     // SyntaxError: campo privado inaccesible
```

#### Python

```python
class CuentaBancaria:
    def __init__(self, titular, saldo_inicial):
        self.__titular = titular
        self.__saldo = saldo_inicial if saldo_inicial >= 0 else 0

    def depositar(self, monto):
        if monto > 0:
            self.__saldo += monto

    def retirar(self, monto):
        if monto > 0 and monto <= self.__saldo:
            self.__saldo -= monto
            return True
        return False

    # Getter
    @property
    def saldo(self):
        return self.__saldo

    @property
    def titular(self):
        return self.__titular

cuenta = CuentaBancaria("Elena", 1000)
cuenta.depositar(500)
cuenta.retirar(200)

print(cuenta.saldo)   # 1300
print(cuenta.titular) # Elena
# cuenta.__saldo = 9999  # no lanza error pero no modifica el atributo privado real
```

#### C#

```csharp
class CuentaBancaria
{
    private double saldo;
    private string titular;

    public CuentaBancaria(string titular, double saldoInicial)
    {
        this.titular = titular;
        this.saldo = saldoInicial >= 0 ? saldoInicial : 0;
    }

    public void Depositar(double monto)
    {
        if (monto > 0) saldo += monto;
    }

    public bool Retirar(double monto)
    {
        if (monto > 0 && monto <= saldo)
        {
            saldo -= monto;
            return true;
        }
        return false;
    }

    // Propiedades de solo lectura (getter)
    public double Saldo => saldo;
    public string Titular => titular;
}

var cuenta = new CuentaBancaria("Elena", 1000);
cuenta.Depositar(500);
cuenta.Retirar(200);

Console.WriteLine(cuenta.Saldo);   // 1300
Console.WriteLine(cuenta.Titular); // Elena
// cuenta.saldo = 9999;  // Error: 'saldo' es privado
```

#### Java

```java
public class Main {
    static class CuentaBancaria {
        private double saldo;
        private String titular;

        public CuentaBancaria(String titular, double saldoInicial) {
            this.titular = titular;
            this.saldo = saldoInicial >= 0 ? saldoInicial : 0;
        }

        public void depositar(double monto) {
            if (monto > 0) saldo += monto;
        }

        public boolean retirar(double monto) {
            if (monto > 0 && monto <= saldo) {
                saldo -= monto;
                return true;
            }
            return false;
        }

        // Getters
        public double getSaldo()    { return saldo; }
        public String getTitular()  { return titular; }
    }

    public static void main(String[] args) {
        CuentaBancaria cuenta = new CuentaBancaria("Elena", 1000);
        cuenta.depositar(500);
        cuenta.retirar(200);

        System.out.println(cuenta.getSaldo());   // 1300.0
        System.out.println(cuenta.getTitular()); // Elena
        // cuenta.saldo = 9999;  // Error: 'saldo' tiene acceso private
    }
}
```

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

### Errores comunes

- Definir todos los atributos como públicos y luego agregar getters y setters para cada uno anula el propósito del encapsulamiento.
- Un setter sin validación es equivalente a un atributo público: no protege nada.
- Otro error es crear setters para atributos que no deberían cambiar desde fuera.
- Si el titular de una cuenta nunca cambia después de crearse, no debe tener setter.
- El encapsulamiento también significa decidir qué no se expone.

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## Herencia

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

La herencia permite que una clase adquiera los atributos y métodos de otra.

- La clase que hereda se llama **subclase** o clase hija.
- La clase de la que hereda se llama **superclase** o clase padre.
- La subclase puede usar todo lo definido en la superclase y además agregar sus propios atributos y métodos o redefinir los heredados.

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

La herencia modela una relación de tipo **es-un**:

- Un `Auto` es un `Vehiculo`.
- Un `Perro` es un `Animal`.

Si esa relación no se sostiene en lenguaje natural, probablemente la herencia no es el mecanismo correcto.

El constructor de la subclase generalmente llama al constructor de la superclase para inicializar los atributos heredados antes de agregar los propios.

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

### Ejemplo cotidiano

Un empleado de tiempo completo es un empleado.

Comparte con todos los empleados atributos como nombre, id y salario base, y métodos como calcular pago.

Pero además tiene atributos propios: beneficios de salud, días de vacaciones pagadas.

La herencia permite definir `Empleado` una sola vez y extenderlo con `EmpleadoTiempoCompleto` sin duplicar el código común.

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

### Ejemplo conceptual

```
CLASE Animal
  ATRIBUTOS
    nombre
    sonido

  CONSTRUCTOR(nombre, sonido)
    this.nombre = nombre
    this.sonido = sonido
  FIN CONSTRUCTOR

  MÉTODO hablar()
    MOSTRAR this.nombre, " dice: ", this.sonido
  FIN MÉTODO
FIN CLASE

CLASE Perro HEREDA Animal
  ATRIBUTOS
    raza

  CONSTRUCTOR(nombre, raza)
    SUPER(nombre, "Guau")
    this.raza = raza
  FIN CONSTRUCTOR

  MÉTODO describir()
    MOSTRAR this.nombre, " es un ", this.raza
  FIN MÉTODO
FIN CLASE

p = nuevo Perro("Rex", "Labrador")
p.hablar()    ← Rex dice: Guau     (método heredado)
p.describir() ← Rex es un Labrador (método propio)
```

### Ejemplos en código

#### JavaScript

```javascript
class Animal {
  constructor(nombre, sonido) {
    this.nombre = nombre;
    this.sonido = sonido;
  }

  hablar() {
    console.log(`${this.nombre} dice: ${this.sonido}`);
  }
}

class Perro extends Animal {
  constructor(nombre, raza) {
    super(nombre, "Guau"); // llama al constructor de Animal
    this.raza = raza;
  }

  describir() {
    console.log(`${this.nombre} es un ${this.raza}`);
  }
}

const p = new Perro("Rex", "Labrador");
p.hablar(); // Rex dice: Guau
p.describir(); // Rex es un Labrador
console.log(p instanceof Animal); // true
console.log(p instanceof Perro); // true
```

#### Python

```python
class Animal:
    def __init__(self, nombre, sonido):
        self.nombre = nombre
        self.sonido = sonido

    def hablar(self):
        print(f"{self.nombre} dice: {self.sonido}")

class Perro(Animal):
    def __init__(self, nombre, raza):
        super().__init__(nombre, "Guau")  # llama al constructor de Animal
        self.raza = raza

    def describir(self):
        print(f"{self.nombre} es un {self.raza}")

p = Perro("Rex", "Labrador")
p.hablar()    # Rex dice: Guau
p.describir() # Rex es un Labrador
print(isinstance(p, Animal))  # True
print(isinstance(p, Perro))   # True
```

#### C#

```csharp
class Animal
{
    public string Nombre;
    public string Sonido;

    public Animal(string nombre, string sonido)
    {
        Nombre = nombre;
        Sonido = sonido;
    }

    public void Hablar()
    {
        Console.WriteLine($"{Nombre} dice: {Sonido}");
    }
}

class Perro : Animal
{
    public string Raza;

    public Perro(string nombre, string raza)
        : base(nombre, "Guau") // llama al constructor de Animal
    {
        Raza = raza;
    }

    public void Describir()
    {
        Console.WriteLine($"{Nombre} es un {Raza}");
    }
}

var p = new Perro("Rex", "Labrador");
p.Hablar();    // Rex dice: Guau
p.Describir(); // Rex es un Labrador
Console.WriteLine(p is Animal); // True
Console.WriteLine(p is Perro);  // True
```

#### Java

```java
public class Main {
    static class Animal {
        String nombre;
        String sonido;

        Animal(String nombre, String sonido) {
            this.nombre = nombre;
            this.sonido = sonido;
        }

        void hablar() {
            System.out.println(nombre + " dice: " + sonido);
        }
    }

    static class Perro extends Animal {
        String raza;

        Perro(String nombre, String raza) {
            super(nombre, "Guau"); // llama al constructor de Animal
            this.raza = raza;
        }

        void describir() {
            System.out.println(nombre + " es un " + raza);
        }
    }

    public static void main(String[] args) {
        Perro p = new Perro("Rex", "Labrador");
        p.hablar();    // Rex dice: Guau
        p.describir(); // Rex es un Labrador
        System.out.println(p instanceof Animal); // true
        System.out.println(p instanceof Perro);  // true
    }
}
```

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

### Errores comunes

- Usar herencia para reutilizar código cuando no existe una relación real de tipo es-un es el error más común y más costoso.
- Si `Camion` hereda de `Motor` porque necesita sus métodos, el diseño está mal: un camión no es un motor.
- Crear jerarquías de herencia muy profundas es otro error frecuente.
- Cuando una clase hereda de otra que hereda de otra que hereda de otra, rastrear el comportamiento se vuelve complejo.
- Como regla práctica, más de dos o tres niveles de herencia es señal de que el diseño necesita revisión.

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## Polimorfismo

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

El polimorfismo permite que objetos de distintas clases respondan al mismo mensaje de formas diferentes.

El mismo método, llamado sobre objetos de tipos distintos, produce comportamientos distintos según la implementación de cada clase.

Hay dos formas principales:

1. El **polimorfismo de sobreescritura** ocurre cuando una subclase redefine un método heredado para cambiar su comportamiento
2. El **polimorfismo de sobrecarga** ocurre cuando una misma clase define múltiples versiones del mismo método con distintos parámetros.

No todos los lenguajes soportan ambas formas de la misma manera.

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

### Ejemplo cotidiano

Un sistema de pagos puede procesar tarjeta de crédito, transferencia bancaria o efectivo.

Los tres son formas de pago. El sistema llama al método `procesar()` sin importar cuál es: cada implementación hace lo correcto para su tipo.

El sistema no necesita saber si está procesando una tarjeta o una transferencia; solo sabe que está procesando un pago.

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

### Ejemplo conceptual

```
CLASE Forma
  MÉTODO calcularArea()
    RETORNAR 0   // implementación por defecto
  FIN MÉTODO
FIN CLASE

CLASE Rectangulo HEREDA Forma
  CONSTRUCTOR(base, altura)
    this.base = base
    this.altura = altura
  FIN CONSTRUCTOR

  MÉTODO calcularArea()   // sobreescritura
    RETORNAR this.base * this.altura
  FIN MÉTODO
FIN CLASE

CLASE Circulo HEREDA Forma
  CONSTRUCTOR(radio)
    this.radio = radio
  FIN CONSTRUCTOR

  MÉTODO calcularArea()   // sobreescritura
    RETORNAR 3.14159 * this.radio * this.radio
  FIN MÉTODO
FIN CLASE

formas = [nueva Forma(), nuevo Rectangulo(4, 5), nuevo Circulo(3)]

PARA CADA forma EN formas HACER
  MOSTRAR forma.calcularArea()   // cada objeto responde según su tipo
FIN PARA
// 0, 20, 28.27...
```

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

### Ejemplos en código

#### JavaScript

```javascript
class Forma {
  calcularArea() {
    return 0;
  }
  describir() {
    return `Área: ${this.calcularArea()}`;
  }
}

class Rectangulo extends Forma {
  constructor(base, altura) {
    super();
    this.base = base;
    this.altura = altura;
  }

  calcularArea() {
    return this.base * this.altura;
  } // sobreescritura
}

class Circulo extends Forma {
  constructor(radio) {
    super();
    this.radio = radio;
  }

  calcularArea() {
    return 3.14159 * this.radio ** 2;
  } // sobreescritura
}

class Triangulo extends Forma {
  constructor(base, altura) {
    super();
    this.base = base;
    this.altura = altura;
  }

  calcularArea() {
    return (this.base * this.altura) / 2;
  } // sobreescritura
}

// Polimorfismo: mismo mensaje, distintos comportamientos
const formas = [new Rectangulo(4, 5), new Circulo(3), new Triangulo(6, 4)];

for (const forma of formas) {
  console.log(forma.describir()); // cada objeto responde según su tipo
}
// Área: 20
// Área: 28.27431...
// Área: 12
```

#### Python

```python
class Forma:
    def calcular_area(self):
        return 0

    def describir(self):
        return f"Área: {self.calcular_area()}"

class Rectangulo(Forma):
    def __init__(self, base, altura):
        self.base = base
        self.altura = altura

    def calcular_area(self):  # sobreescritura
        return self.base * self.altura

class Circulo(Forma):
    def __init__(self, radio):
        self.radio = radio

    def calcular_area(self):  # sobreescritura
        return 3.14159 * self.radio ** 2

class Triangulo(Forma):
    def __init__(self, base, altura):
        self.base = base
        self.altura = altura

    def calcular_area(self):  # sobreescritura
        return (self.base * self.altura) / 2

# Polimorfismo: mismo mensaje, distintos comportamientos
formas = [Rectangulo(4, 5), Circulo(3), Triangulo(6, 4)]

for forma in formas:
    print(forma.describir())  # cada objeto responde según su tipo
# Área: 20
# Área: 28.27431...
# Área: 12.0
```

#### C#

```csharp
class Forma
{
    public virtual double CalcularArea() => 0;
    public string Describir() => $"Área: {CalcularArea()}";
}

class Rectangulo : Forma
{
    double base_, altura;
    public Rectangulo(double base_, double altura)
    {
        this.base_ = base_;
        this.altura = altura;
    }
    public override double CalcularArea() => base_ * altura; // sobreescritura
}

class Circulo : Forma
{
    double radio;
    public Circulo(double radio) { this.radio = radio; }
    public override double CalcularArea() => 3.14159 * radio * radio; // sobreescritura
}

class Triangulo : Forma
{
    double base_, altura;
    public Triangulo(double base_, double altura)
    {
        this.base_ = base_;
        this.altura = altura;
    }
    public override double CalcularArea() => (base_ * altura) / 2; // sobreescritura
}

// Polimorfismo: mismo mensaje, distintos comportamientos
Forma[] formas = { new Rectangulo(4, 5), new Circulo(3), new Triangulo(6, 4) };

foreach (var forma in formas)
{
    Console.WriteLine(forma.Describir()); // cada objeto responde según su tipo
}
// Área: 20
// Área: 28.27431...
// Área: 12
```

#### Java

```java
public class Main {
    static class Forma {
        double calcularArea() { return 0; }
        String describir()   { return "Área: " + calcularArea(); }
    }

    static class Rectangulo extends Forma {
        double base, altura;
        Rectangulo(double base, double altura) {
            this.base = base; this.altura = altura;
        }
        @Override
        double calcularArea() { return base * altura; } // sobreescritura
    }

    static class Circulo extends Forma {
        double radio;
        Circulo(double radio) { this.radio = radio; }
        @Override
        double calcularArea() { return 3.14159 * radio * radio; } // sobreescritura
    }

    static class Triangulo extends Forma {
        double base, altura;
        Triangulo(double base, double altura) {
            this.base = base; this.altura = altura;
        }
        @Override
        double calcularArea() { return (base * altura) / 2; } // sobreescritura
    }

    public static void main(String[] args) {
        // Polimorfismo: mismo mensaje, distintos comportamientos
        Forma[] formas = { new Rectangulo(4, 5), new Circulo(3), new Triangulo(6, 4) };

        for (Forma forma : formas) {
            System.out.println(forma.describir()); // cada objeto responde según su tipo
        }
        // Área: 20.0
        // Área: 28.27431...
        // Área: 12.0
    }
}
```

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

### Errores comunes

- Verificar el tipo del objeto con `instanceof` o equivalentes dentro de un bucle para decidir qué método llamar anula el polimorfismo.
- Si el código hace `si es Rectangulo calcula así, si es Circulo calcula asá`, el problema es de diseño: cada clase debería sobreescribir el método y el código externo no debería saber el tipo concreto.
- Olvidar la palabra clave `virtual` en C# o `@Override` en Java cuando se sobreescribe un método puede producir comportamientos inesperados.
- En C#, sin `virtual` en la superclase el método no puede ser sobreescrito de forma polimórfica.
- En Java, `@Override` es una anotación de verificación: si el método no existe en la superclase, el compilador avisa del error.

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## Abstracción

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

La abstracción es el principio de exponer solo lo esencial y ocultar los detalles de implementación.

Una clase abstracta define una interfaz: declara qué métodos deben existir sin implementarlos.

Las subclases concretas son las que proporcionan la implementación.

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

- Una clase abstracta no puede instanciarse directamente.
- Existe para ser heredada.
- Su propósito es establecer un contrato: cualquier clase que herede de ella debe implementar los métodos abstractos declarados.

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

### Ejemplo cotidiano

El concepto de "medio de pago" es abstracto:

- No existe un medio de pago genérico en el mundo real.
- Lo que existe son tarjetas de crédito, transferencias, efectivo, criptomonedas.
- Cada uno implementa las operaciones de pago a su manera, pero todos deben poder procesar una transacción y emitir un comprobante.
- Esas dos operaciones son el contrato abstracto.

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

### Ejemplo conceptual

```
CLASE ABSTRACTA MedioDePago
  MÉTODO ABSTRACTO procesar(monto)   // sin implementación
  MÉTODO ABSTRACTO comprobante()     // sin implementación

  MÉTODO pagar(monto)                // método concreto que usa los abstractos
    MOSTRAR "Iniciando pago de $", monto
    procesar(monto)
    comprobante()
    MOSTRAR "Pago completado."
  FIN MÉTODO
FIN CLASE

CLASE TarjetaCredito HEREDA MedioDePago
  MÉTODO procesar(monto)
    MOSTRAR "Cargando $", monto, " a la tarjeta."
  FIN MÉTODO

  MÉTODO comprobante()
    MOSTRAR "Comprobante de tarjeta emitido."
  FIN MÉTODO
FIN CLASE

// nuevo MedioDePago()  ← ERROR: clase abstracta no instanciable
pago = nuevo TarjetaCredito()
pago.pagar(350)
```

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

### Ejemplos en código

#### JavaScript

```javascript
// JavaScript no tiene clases abstractas nativas.
// Se simula lanzando error en los métodos que deben ser implementados.
class MedioDePago {
  procesar(monto) {
    throw new Error("procesar() debe ser implementado por la subclase");
  }

  comprobante() {
    throw new Error("comprobante() debe ser implementado por la subclase");
  }

  // Método concreto que usa los abstractos
  pagar(monto) {
    console.log(`Iniciando pago de $${monto}`);
    this.procesar(monto);
    this.comprobante();
    console.log("Pago completado.");
  }
}

class TarjetaCredito extends MedioDePago {
  procesar(monto) {
    console.log(`Cargando $${monto} a la tarjeta.`);
  }

  comprobante() {
    console.log("Comprobante de tarjeta emitido.");
  }
}

class Transferencia extends MedioDePago {
  procesar(monto) {
    console.log(`Transfiriendo $${monto} a la cuenta destino.`);
  }

  comprobante() {
    console.log("Comprobante de transferencia emitido.");
  }
}

// new MedioDePago().pagar(100); // Error: procesar() debe ser implementado
const t = new TarjetaCredito();
t.pagar(350);

const tr = new Transferencia();
tr.pagar(800);
```

#### Python

```python
from abc import ABC, abstractmethod

class MedioDePago(ABC):
    @abstractmethod
    def procesar(self, monto):
        pass  # sin implementación

    @abstractmethod
    def comprobante(self):
        pass  # sin implementación

    # Método concreto que usa los abstractos
    def pagar(self, monto):
        print(f"Iniciando pago de ${monto}")
        self.procesar(monto)
        self.comprobante()
        print("Pago completado.")

class TarjetaCredito(MedioDePago):
    def procesar(self, monto):
        print(f"Cargando ${monto} a la tarjeta.")

    def comprobante(self):
        print("Comprobante de tarjeta emitido.")

class Transferencia(MedioDePago):
    def procesar(self, monto):
        print(f"Transfiriendo ${monto} a la cuenta destino.")

    def comprobante(self):
        print("Comprobante de transferencia emitido.")

# MedioDePago()  # TypeError: clase abstracta no instanciable
t = TarjetaCredito()
t.pagar(350)

tr = Transferencia()
tr.pagar(800)
```

#### C#

```csharp
abstract class MedioDePago
{
    public abstract void Procesar(double monto);  // sin implementación
    public abstract void Comprobante();           // sin implementación

    // Método concreto que usa los abstractos
    public void Pagar(double monto)
    {
        Console.WriteLine($"Iniciando pago de ${monto}");
        Procesar(monto);
        Comprobante();
        Console.WriteLine("Pago completado.");
    }
}

class TarjetaCredito : MedioDePago
{
    public override void Procesar(double monto)
    {
        Console.WriteLine($"Cargando ${monto} a la tarjeta.");
    }

    public override void Comprobante()
    {
        Console.WriteLine("Comprobante de tarjeta emitido.");
    }
}

class Transferencia : MedioDePago
{
    public override void Procesar(double monto)
    {
        Console.WriteLine($"Transfiriendo ${monto} a la cuenta destino.");
    }

    public override void Comprobante()
    {
        Console.WriteLine("Comprobante de transferencia emitido.");
    }
}

// new MedioDePago();  // Error: no se puede crear una instancia de una clase abstracta
var t = new TarjetaCredito();
t.Pagar(350);

var tr = new Transferencia();
tr.Pagar(800);
```

#### Java

```java
public class Main {
    abstract static class MedioDePago {
        abstract void procesar(double monto);  // sin implementación
        abstract void comprobante();           // sin implementación

        // Método concreto que usa los abstractos
        void pagar(double monto) {
            System.out.println("Iniciando pago de $" + monto);
            procesar(monto);
            comprobante();
            System.out.println("Pago completado.");
        }
    }

    static class TarjetaCredito extends MedioDePago {
        @Override
        void procesar(double monto) {
            System.out.println("Cargando $" + monto + " a la tarjeta.");
        }

        @Override
        void comprobante() {
            System.out.println("Comprobante de tarjeta emitido.");
        }
    }

    static class Transferencia extends MedioDePago {
        @Override
        void procesar(double monto) {
            System.out.println("Transfiriendo $" + monto + " a la cuenta destino.");
        }

        @Override
        void comprobante() {
            System.out.println("Comprobante de transferencia emitido.");
        }
    }

    public static void main(String[] args) {
        // new MedioDePago();  // Error: clase abstracta no instanciable
        MedioDePago t = new TarjetaCredito();
        t.pagar(350);

        MedioDePago tr = new Transferencia();
        tr.pagar(800);
    }
}
```

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

### Errores comunes

- Implementar métodos abstractos con un cuerpo vacío en lugar de lanzar un error en lenguajes que no tienen clases abstractas nativas es un error silencioso: el objeto "funciona" pero no hace nada donde debería.
- En JavaScript, lanzar un error explícito en el método de la clase base obliga al desarrollador a implementarlo.
- Intentar instanciar directamente una clase abstracta es un error de diseño que la mayoría de los lenguajes detecta en tiempo de compilación.
- En Python se detecta en tiempo de ejecución cuando se usa el módulo `abc`.

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## Composición vs herencia

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

La composición es una alternativa a la herencia para reutilizar comportamiento.

En lugar de que una clase herede de otra, la clase contiene una instancia de otra como atributo y delega en ella parte de su comportamiento.

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

La regla para elegir entre ambas es directa:

- **Herencia** cuando la relación entre clases es de tipo es-un: `Auto` es un `Vehiculo`, `Perro` es un `Animal`.
- **Composición** cuando la relación es de tipo tiene-un: `Auto` tiene un `Motor`, `Persona` tiene una `Dirección`.

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

- La composición es más flexible que la herencia.
- Con herencia, la subclase está acoplada a los detalles de la superclase.
- Si la superclase cambia, todas sus subclases se ven afectadas.
- Con composición, la clase solo depende de la interfaz del componente, no de su implementación interna.

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

### Ejemplo cotidiano

- Un teléfono tiene una cámara, un GPS y un altavoz.
- No es una cámara, no es un GPS, no es un altavoz.
- Los contiene y los usa.
- Si la cámara mejora, el teléfono aprovecha la mejora sin necesitar rediseñarse.
- Esa independencia es la ventaja de la composición.

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

### Ejemplo conceptual

```
// Herencia: problemática cuando la relación no es real
CLASE Motor
  MÉTODO encender()
    MOSTRAR "Motor encendido"
  FIN MÉTODO
FIN CLASE

// Incorrecto: Camion NO es un Motor
CLASE Camion HEREDA Motor  ← relación forzada
FIN CLASE

// Composición: correcto
CLASE Camion
  ATRIBUTOS
    motor = nuevo Motor()   // Camion TIENE un Motor

  MÉTODO arrancar()
    this.motor.encender()
    MOSTRAR "Camión en marcha"
  FIN MÉTODO
FIN CLASE
```

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

### Comparación en código

#### JavaScript

```javascript
// Componentes independientes
class Motor {
  encender() {
    console.log("Motor encendido.");
  }
  apagar() {
    console.log("Motor apagado.");
  }
}

class SistemaAudio {
  reproducir(pista) {
    console.log(`Reproduciendo: ${pista}`);
  }
  silenciar() {
    console.log("Audio silenciado.");
  }
}

class GPS {
  navegar(destino) {
    console.log(`Navegando hacia: ${destino}`);
  }
}

// Composición: Auto TIENE un Motor, un SistemaAudio y un GPS
class Auto {
  constructor(marca) {
    this.marca = marca;
    this.motor = new Motor(); // composición
    this.audio = new SistemaAudio(); // composición
    this.gps = new GPS(); // composición
  }

  arrancar() {
    this.motor.encender();
  }
  apagar() {
    this.motor.apagar();
  }
  reproducir(pista) {
    this.audio.reproducir(pista);
  }
  navegar(destino) {
    this.gps.navegar(destino);
  }
}

const auto = new Auto("Toyota");
auto.arrancar();
auto.reproducir("Playlist de viaje");
auto.navegar("Aeropuerto");
auto.apagar();
```

#### Python

```python
class Motor:
    def encender(self): print("Motor encendido.")
    def apagar(self):   print("Motor apagado.")

class SistemaAudio:
    def reproducir(self, pista): print(f"Reproduciendo: {pista}")
    def silenciar(self):         print("Audio silenciado.")

class GPS:
    def navegar(self, destino): print(f"Navegando hacia: {destino}")

# Composición: Auto TIENE un Motor, un SistemaAudio y un GPS
class Auto:
    def __init__(self, marca):
        self.marca = marca
        self.motor = Motor()           # composición
        self.audio = SistemaAudio()    # composición
        self.gps = GPS()               # composición

    def arrancar(self):             self.motor.encender()
    def apagar(self):               self.motor.apagar()
    def reproducir(self, pista):    self.audio.reproducir(pista)
    def navegar(self, destino):     self.gps.navegar(destino)

auto = Auto("Toyota")
auto.arrancar()
auto.reproducir("Playlist de viaje")
auto.navegar("Aeropuerto")
auto.apagar()
```

#### C#

```csharp
class Motor
{
    public void Encender() => Console.WriteLine("Motor encendido.");
    public void Apagar()   => Console.WriteLine("Motor apagado.");
}

class SistemaAudio
{
    public void Reproducir(string pista) => Console.WriteLine($"Reproduciendo: {pista}");
    public void Silenciar()              => Console.WriteLine("Audio silenciado.");
}

class GPS
{
    public void Navegar(string destino) => Console.WriteLine($"Navegando hacia: {destino}");
}

// Composición: Auto TIENE un Motor, un SistemaAudio y un GPS
class Auto
{
    private string marca;
    private Motor motor;
    private SistemaAudio audio;
    private GPS gps;

    public Auto(string marca)
    {
        this.marca = marca;
        motor = new Motor();           // composición
        audio = new SistemaAudio();    // composición
        gps   = new GPS();             // composición
    }

    public void Arrancar()              => motor.Encender();
    public void Apagar()                => motor.Apagar();
    public void Reproducir(string pista) => audio.Reproducir(pista);
    public void Navegar(string destino)  => gps.Navegar(destino);
}

var auto = new Auto("Toyota");
auto.Arrancar();
auto.Reproducir("Playlist de viaje");
auto.Navegar("Aeropuerto");
auto.Apagar();
```

#### Java

```java
public class Main {
    static class Motor {
        void encender() { System.out.println("Motor encendido."); }
        void apagar()   { System.out.println("Motor apagado."); }
    }

    static class SistemaAudio {
        void reproducir(String pista) { System.out.println("Reproduciendo: " + pista); }
        void silenciar()              { System.out.println("Audio silenciado."); }
    }

    static class GPS {
        void navegar(String destino) { System.out.println("Navegando hacia: " + destino); }
    }

    // Composición: Auto TIENE un Motor, un SistemaAudio y un GPS
    static class Auto {
        private String marca;
        private Motor motor;
        private SistemaAudio audio;
        private GPS gps;

        Auto(String marca) {
            this.marca = marca;
            this.motor = new Motor();           // composición
            this.audio = new SistemaAudio();    // composición
            this.gps   = new GPS();             // composición
        }

        void arrancar()              { motor.encender(); }
        void apagar()                { motor.apagar(); }
        void reproducir(String pista) { audio.reproducir(pista); }
        void navegar(String destino)  { gps.navegar(destino); }
    }

    public static void main(String[] args) {
        Auto auto = new Auto("Toyota");
        auto.arrancar();
        auto.reproducir("Playlist de viaje");
        auto.navegar("Aeropuerto");
        auto.apagar();
    }
}
```

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

### Errores comunes

- Usar herencia para reutilizar un método conveniente aunque no exista una relación es-un es el error que la composición resuelve.
- Si `ReportePDF` hereda de `GeneradorDeArchivos` solo para aprovechar el método `guardar()`, el diseño es incorrecto.
- La solución es que `ReportePDF` contenga una instancia de `GeneradorDeArchivos`.
- El error opuesto también existe: usar composición cuando la herencia es clara y natural.
- Si `Gato` y `Perro` comparten decenas de atributos y comportamientos de `Animal`, duplicar esa lógica en dos clases separadas a través de composición es innecesariamente complejo.

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## Ejercicios prácticos

1. Escribe en pseudocódigo una clase `Contador` que mantenga un valor interno inicializado en cero, con métodos `incrementar()`, `decrementar()`, `reiniciar()` y `obtenerValor()`. El valor nunca debe ser negativo: si `decrementar()` lo llevaría por debajo de cero, se queda en cero. Crea dos instancias independientes y demuestra que sus valores no se afectan mutuamente.
2. Escribe en pseudocódigo una clase `Inventario` con un atributo de clase `totalProductos` que cuente cuántas instancias han sido creadas. Cada vez que se crea un nuevo producto (con nombre y stock), el contador de clase debe incrementarse. Agrega un método de clase `obtenerTotal()` que retorne el conteo. Crea cuatro instancias y verifica que el contador refleja el total correcto.
3. Escribe en pseudocódigo una clase `Semaforo` con un atributo privado `estado` que solo puede tomar los valores `"rojo"`, `"amarillo"` o `"verde"`. El constructor inicializa el estado en `"rojo"`. Agrega un método `cambiar()` que avance al siguiente estado en ese orden cíclico, y un getter `obtenerEstado()`.
4. Escribe en pseudocódigo una jerarquía con clase `Empleado` (nombre, salario base, método `calcularPago()` que retorna el salario base) y subclase `EmpleadoConBono` que herede de `Empleado` y agregue un atributo `bono`. Su método `calcularPago()` debe retornar el salario base más el bono. Crea una instancia de cada clase y muestra el pago calculado.
5. Escribe en pseudocódigo una clase `Descuento` con un método `calcular(precio)` que retorne 0. Crea subclases `DescuentoPorcentaje` (retorna precio × porcentaje) y `DescuentoFijo` (retorna el monto fijo si es menor que el precio, sino retorna el precio). Aplica ambos tipos de descuento al mismo precio y muestra los resultados.
6. Escribe en pseudocódigo una clase abstracta `Figura` con un método abstracto `calcularArea()` y un método concreto `mostrarArea()` que llame a `calcularArea()` e imprima el resultado. Implementa dos subclases concretas: `Cuadrado` (lado) y `Rectangulo` (base y altura).
7. Escribe en pseudocódigo un ejemplo con dos clases independientes: `Impresora` (con método `imprimir(texto)`) y `Escaner` (con método `escanear()`). Luego crea una clase `ImpresoraMultifuncion` que use composición para integrar ambas capacidades sin heredar de ninguna de las dos.

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## Principios SOLID

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

### S — Single Responsibility Principle (Principio de responsabilidad única)

- Una clase debe tener una sola razón para cambiar.
- Si una clase hace múltiples cosas, cada cosa es una razón potencial de cambio.
- Cuando esas razones son independientes, el cambio en una puede romper la otra.

```
// Viola SRP: una sola clase hace demasiado
CLASE Reporte
  MÉTODO generarDatos()   ...
  MÉTODO formatearHTML()  ...
  MÉTODO enviarEmail()    ...
FIN CLASE

// Aplica SRP: cada clase tiene una responsabilidad
CLASE GeneradorReporte   → produce los datos
CLASE FormateadorHTML    → convierte datos a HTML
CLASE EnviadorEmail      → envía el correo
```

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

### O — Open/Closed Principle (Principio abierto/cerrado)

- Una clase debe estar abierta para extensión pero cerrada para modificación.
- Agregar nuevo comportamiento no debería requerir modificar el código existente.
- La herencia y la abstracción son los mecanismos principales para lograrlo.

```
// Viola OCP: agregar un nuevo tipo de descuento requiere modificar la función
FUNCIÓN calcularDescuento(tipo, precio)
  SI tipo == "porcentaje" ENTONCES ...
  SI tipo == "fijo" ENTONCES ...
  SI tipo == "nuevo" ENTONCES ...   ← modificación necesaria
FIN FUNCIÓN

// Aplica OCP: cada tipo de descuento es una clase independiente
CLASE ABSTRACTA Descuento
  MÉTODO ABSTRACTO calcular(precio)
FIN CLASE

CLASE DescuentoPorcentaje HEREDA Descuento  → extensión sin modificar
CLASE DescuentoFijo HEREDA Descuento        → extensión sin modificar
CLASE DescuentoNuevo HEREDA Descuento       → extensión sin modificar
```

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

### L — Liskov Substitution Principle (Principio de sustitución de Liskov)

- Los objetos de una subclase deben poder reemplazar a los de la superclase sin alterar el comportamiento correcto del programa.
- Si una subclase no puede cumplir el contrato de la superclase, la jerarquía de herencia está mal diseñada.

```
// Viola LSP: Cuadrado hereda de Rectangulo pero no puede redefinir setBase y setAltura
// de forma que ambos funcionen independientemente, como exige Rectangulo.
CLASE Rectangulo
  MÉTODO setBase(b)   this.base = b
  MÉTODO setAltura(h) this.altura = h
FIN CLASE

CLASE Cuadrado HEREDA Rectangulo   // Un cuadrado no es un rectángulo en este modelo
  MÉTODO setBase(b)   this.base = b; this.altura = b   // rompe el contrato
  MÉTODO setAltura(h) this.base = h; this.altura = h   // rompe el contrato
FIN CLASE

// Aplica LSP: Cuadrado y Rectangulo son subclases independientes de Figura
CLASE ABSTRACTA Figura
  MÉTODO ABSTRACTO calcularArea()
FIN CLASE

CLASE Rectangulo HEREDA Figura   // cada una tiene su propio contrato
CLASE Cuadrado HEREDA Figura     // sin interferencia entre sí
```

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

### I — Interface Segregation Principle (Principio de segregación de interfaces)

- Una clase no debería verse obligada a implementar métodos que no usa.
- Las interfaces deben ser específicas, no generales. - En lenguajes sin interfaces formales (JavaScript, Python), este principio aplica al diseño de las clases abstractas.

```
// Viola ISP: una interfaz con demasiados métodos obliga a implementar lo que no se usa
INTERFAZ Trabajador
  MÉTODO trabajar()
  MÉTODO comer()
  MÉTODO dormir()
FIN INTERFAZ

// Un robot implementa Trabajador pero no come ni duerme: métodos vacíos sin sentido

// Aplica ISP: interfaces específicas
INTERFAZ Trabajable  → MÉTODO trabajar()
INTERFAZ Humano      → MÉTODO comer(), MÉTODO dormir()

CLASE Robot IMPLEMENTA Trabajable        // solo lo que usa
CLASE Persona IMPLEMENTA Trabajable, Humano  // todo lo que le aplica
```

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

### D — Dependency Inversion Principle (Principio de inversión de dependencias)

- Los módulos de alto nivel no deben depender de los de bajo nivel.
- Ambos deben depender de abstracciones.
- Las clases concretas deben depender de interfaces, no al revés.

```
// Viola DIP: la clase de alto nivel depende de una implementación concreta
CLASE Notificador
  ATRIBUTOS
    email = nuevo EmailService()   // acoplado a EmailService

  MÉTODO notificar(msg)
    this.email.enviar(msg)
FIN CLASE

// Aplica DIP: Notificador depende de una abstracción, no de EmailService directamente
CLASE ABSTRACTA ServicioMensaje
  MÉTODO ABSTRACTO enviar(msg)
FIN CLASE

CLASE EmailService HEREDA ServicioMensaje   // implementación concreta
CLASE SMSService HEREDA ServicioMensaje     // otra implementación concreta

CLASE Notificador
  CONSTRUCTOR(servicio)             // recibe cualquier ServicioMensaje
    this.servicio = servicio

  MÉTODO notificar(msg)
    this.servicio.enviar(msg)       // depende de la abstracción
FIN CLASE
```

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

### Ejemplo integrado en código

El siguiente ejemplo aplica los cinco principios en un sistema de procesamiento de pedidos.

#### JavaScript

```javascript
// S: cada clase tiene una responsabilidad
class CalculadorPedido {
  calcularTotal(items) {
    return items.reduce((acc, item) => acc + item.precio * item.cantidad, 0);
  }
}

// O: nueva forma de descuento sin modificar código existente
class DescuentoPorcentaje {
  calcular(total, valor) {
    return total - total * valor;
  }
}

class DescuentoFijo {
  calcular(total, valor) {
    return total - valor;
  }
}

// D: Procesador depende de la abstracción, no de implementaciones concretas
class ProcesadorPedido {
  constructor(calculador, descuento) {
    this.calculador = calculador;
    this.descuento = descuento;
  }

  procesar(items, valorDescuento) {
    const subtotal = this.calculador.calcularTotal(items);
    const total = this.descuento.calcular(subtotal, valorDescuento);
    console.log(`Subtotal: $${subtotal}`);
    console.log(`Total con descuento: $${total}`);
    return total;
  }
}

const items = [
  { precio: 500, cantidad: 2 },
  { precio: 300, cantidad: 1 },
];

const procesador = new ProcesadorPedido(
  new CalculadorPedido(),
  new DescuentoPorcentaje(),
);

procesador.procesar(items, 0.1);
// Subtotal: $1300
// Total con descuento: $1170
```

#### Python

```python
# S: cada clase tiene una responsabilidad
class CalculadorPedido:
    def calcular_total(self, items):
        return sum(item["precio"] * item["cantidad"] for item in items)

# O: nueva forma de descuento sin modificar código existente
class DescuentoPorcentaje:
    def calcular(self, total, valor):
        return total - total * valor

class DescuentoFijo:
    def calcular(self, total, valor):
        return total - valor

# D: Procesador depende de abstracciones, no de implementaciones concretas
class ProcesadorPedido:
    def __init__(self, calculador, descuento):
        self.calculador = calculador
        self.descuento  = descuento

    def procesar(self, items, valor_descuento):
        subtotal = self.calculador.calcular_total(items)
        total    = self.descuento.calcular(subtotal, valor_descuento)
        print(f"Subtotal: ${subtotal}")
        print(f"Total con descuento: ${total}")
        return total

items = [
    {"precio": 500, "cantidad": 2},
    {"precio": 300, "cantidad": 1}
]

procesador = ProcesadorPedido(
    CalculadorPedido(),
    DescuentoPorcentaje()
)

procesador.procesar(items, 0.10)
# Subtotal: $1300
# Total con descuento: $1170.0
```

#### C#

```csharp
using System;
using System.Collections.Generic;
using System.Linq;

// S: cada clase tiene una responsabilidad
class CalculadorPedido
{
    public double CalcularTotal(List<(double precio, int cantidad)> items)
        => items.Sum(i => i.precio * i.cantidad);
}

// O: nueva forma de descuento sin modificar código existente
interface IDescuento
{
    double Calcular(double total, double valor);
}

class DescuentoPorcentaje : IDescuento
{
    public double Calcular(double total, double valor) => total - total * valor;
}

class DescuentoFijo : IDescuento
{
    public double Calcular(double total, double valor) => total - valor;
}

// D: Procesador depende de la interfaz IDescuento, no de implementaciones concretas
class ProcesadorPedido
{
    private CalculadorPedido calculador;
    private IDescuento descuento;

    public ProcesadorPedido(CalculadorPedido calculador, IDescuento descuento)
    {
        this.calculador = calculador;
        this.descuento  = descuento;
    }

    public double Procesar(List<(double precio, int cantidad)> items, double valorDescuento)
    {
        double subtotal = calculador.CalcularTotal(items);
        double total    = descuento.Calcular(subtotal, valorDescuento);
        Console.WriteLine($"Subtotal: ${subtotal}");
        Console.WriteLine($"Total con descuento: ${total}");
        return total;
    }
}

var items = new List<(double precio, int cantidad)>
{
    (500, 2), (300, 1)
};

var procesador = new ProcesadorPedido(
    new CalculadorPedido(),
    new DescuentoPorcentaje()
);

procesador.Procesar(items, 0.10);
// Subtotal: $1300
// Total con descuento: $1170
```

#### Java

```java
import java.util.*;

public class Main {
    // S: cada clase tiene una responsabilidad
    static class CalculadorPedido {
        double calcularTotal(List<int[]> items) {
            return items.stream().mapToDouble(i -> i[0] * i[1]).sum();
        }
    }

    // O: nueva forma de descuento sin modificar código existente
    interface Descuento {
        double calcular(double total, double valor);
    }

    static class DescuentoPorcentaje implements Descuento {
        public double calcular(double total, double valor) { return total - total * valor; }
    }

    static class DescuentoFijo implements Descuento {
        public double calcular(double total, double valor) { return total - valor; }
    }

    // D: Procesador depende de la interfaz Descuento, no de implementaciones concretas
    static class ProcesadorPedido {
        private CalculadorPedido calculador;
        private Descuento descuento;

        ProcesadorPedido(CalculadorPedido calculador, Descuento descuento) {
            this.calculador = calculador;
            this.descuento  = descuento;
        }

        double procesar(List<int[]> items, double valorDescuento) {
            double subtotal = calculador.calcularTotal(items);
            double total    = descuento.calcular(subtotal, valorDescuento);
            System.out.println("Subtotal: $" + subtotal);
            System.out.println("Total con descuento: $" + total);
            return total;
        }
    }

    public static void main(String[] args) {
        List<int[]> items = Arrays.asList(
            new int[]{500, 2},
            new int[]{300, 1}
        );

        ProcesadorPedido procesador = new ProcesadorPedido(
            new CalculadorPedido(),
            new DescuentoPorcentaje()
        );

        procesador.procesar(items, 0.10);
        // Subtotal: $1300.0
        // Total con descuento: $1170.0
    }
}
```

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

### Errores comunes

- Tratar SOLID como una lista de reglas que deben cumplirse siempre y en todos los casos es el error más frecuente.
- Son criterios de diseño, no mandamientos.
- Aplicar todos los principios a un script de 20 líneas produce complejidad innecesaria.
- Su valor aparece cuando el sistema crece y las decisiones de diseño tienen consecuencias reales.
- Aplicar SRP de forma obsesiva y dividir hasta que cada clase tiene un único método también es un error.
- La granularidad correcta depende del tamaño y la complejidad del problema.

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

### Ejercicios prácticos

1. La siguiente clase viola SRP. Identifica cuántas responsabilidades tiene, divídela aplicando el principio y escribe el resultado en pseudocódigo.

```
CLASE GestorUsuario
  MÉTODO validarEmail(email)
    RETORNAR email contiene "@"
  FIN MÉTODO

  MÉTODO guardarEnBaseDeDatos(usuario)
    MOSTRAR "Guardando usuario en BD..."
  FIN MÉTODO

  MÉTODO enviarEmailBienvenida(email)
    MOSTRAR "Enviando email a ", email
  FIN MÉTODO
FIN CLASE
```

2. Escribe en pseudocódigo un sistema que aplique OCP y DIP. Define una clase abstracta o interfaz `Impuesto` con un método `calcular(precio)`. Implementa dos subclases: `IVA` (16%) y `ISR` (30%). Crea una clase `CalculadorFactura` que reciba cualquier tipo de `Impuesto` como dependencia y calcule el precio final. Demuestra que se puede cambiar el tipo de impuesto sin modificar `CalculadorFactura`.

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
