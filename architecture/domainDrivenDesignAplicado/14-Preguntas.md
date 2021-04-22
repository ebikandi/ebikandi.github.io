# Preguntas frecuentes

# Cómo convencer al equipo para aplicar DDD

- Tiene que haber una **necesidad real**.

- Poner el objetivo a largo plazo.

- Ningún miembro del equipo se puede quedar atrás.

- Lo importante es aportar valor a la empresa.

- Lo primero es 

  identificar el dolor.

  - ¿Qué parte es la que duele y lo que hay que mejorar sí o sí?
  - Ligarlo a **objetivos de negocio** y alejarnos del hype, modas, ...

- Ver qué soluciones tecnológicas o que prácticas nos sirven para poner remedio a esas necesidades.

- Antes de empezar, **tener claras las bases** (SOLID, testing, arquitectura hexagonal, ...)

- ¿Qué **beneficios** nos ofrece el cambio?

- Tener **consenso e implicación entre todo el equipo**, ya que el principio es muy duro.

# ¿Buses síncronos o asíncronos?

En una petición asíncrona, el server no nos devolverá el resultado de la query, si no qué nos dirá "ok, ya he recibido la query, la procesaré cuando pueda".

Para la UI puede ser un reto, porque no sabremos cuando tendremos el resultado. Se puede hacer polling periódico, pero podríamos "freír" el servido. Con una comunicación bidireccional/full-duplex podría librarnos de esto.

Es importante **considerar en qué casos nos aporta más beneficios que complicaciones.**

# ¿Integración en framework?

Poner en la balanza que Pros y Contras nos ofrece. Puede ser **util para** **infraestructura**.

Por otro lado, la capa de **Aplicación nos conviene que sea "pura"** y sin acoplamientos a herramientas externas.

Añadir una interfaz a **Dominio** para poner una barrera y separar estos elementos de la Infraestructura.

Se podrían usar en las **validaciones de los ValueObjects**, pero fuera de éste no debe verse un import externo.

# ¿Qué lógica poner sobre los agregados?

Como es elemento conceptual que **agrupa** aquellos modelos de dominio alrededor de un mismo concepto, por lo que t**oda la lógica de Dominio relacionada con ese concepto** debería ir dentro.

Si se da el caso en que **la lógica que encapsulamos en una clase se relaciona más con los atributos de otra clase**, lo que debemos hacer es **mover la lógica** a esa otra clase

Dentro de los **Value Objects** también encontraremos **lógica relacionada con las validaciones**, pero **en el momento en que esa lógica involucre a varios Value Objects, la moveremos al Propio agregado**.

Si la lógica **implica entrada/salida de datos**, **necesite un colaborador,** **etc.** **no podremos tenerla en el agregado** y la tendremos que **mover a un caso de uso.**

# Agregados con 8 campos… Lazy Loading?

**No!** Esto haría que nuestro agregado supiese de infraestructura y además perdemos el control de cuando se hace la carga de datos.

### 1 Agregado ↔ 1 request