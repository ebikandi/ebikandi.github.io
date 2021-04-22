# Modulariza los estilos de tu aplicación

# Crea tus primeros Objetos y Atomos

[Código en Github](https://github.com/CodelyTV/css-architecture-course/tree/main/6-1-objects-and-atoms)

- Los **objetos** son clases que creamos para ayudarnos a **dar** **estructura** a nuestra aplicación (listas, etc.), pero seguramente no corresponden directamente a algo que nos haya pasado el departamento de diseño. No tienen *theming*.
- Los **átomos** sí que tienen propiedades visuales.

Cuando vemos clases de átomo y objeto en nuestro html, no tenemos forma de saber de qué tipo de clase se trata. Eso puede dificultar encontrar el archivo para ver o modificar la clase si es necesario, y también nos dificulta la comprensión de qué hace cada clase. En aplicaciones grandes, nos puede interesar prefijar las clases según su tipo, para así ver rápidamente que tipo de clase es:

```css
objects:    o-
atoms:      a-
molecules:  m-
organisms:  g-
utilities:  u-
            is-
            has-
```

Esto puede crear clases largas y difíciles de leer, especialmente combinado con BEM, así que hay que valorar si vale la pena o no en función del tipo de aplicación y el equipo que tengamos.

# Clases con significado: Moléculas

[Código en Github](https://github.com/CodelyTV/css-architecture-course/tree/main/6-2-molecules)

Las moléculas son una **conjunción de átomos**.

**Cuidado con las abstracciones prematuras.** Puede darse el caso que ciertos elementos de la molécula no se usen en ningún otro sitio, por lo que podemos definirlos como partes de ella, en lugar de tener una clase de átomo.

En general **debe evitarse definir propiedades cómo tamaños y márgenes** en los estilos de una molécula, **ya que siempre se va a utilizar dentro de un organismo**, que es el que deberá dar la estructura que defina los tamaños.

# Componentes independientes: Organismos

[Código en Github](https://github.com/CodelyTV/css-architecture-course/tree/main/6-3-organisms)

**Conjunción de moléculas**. Las **clases más concretas y menos reutilizables** de nuestra app. Componentes independientes que se pueden usar en mas de una página pero que no se repiten dentro la misma. Aquí tambien cuidado con las abstracciones prematuras. **Es mejor tener dos organismos parecidos qué parametrizar en balde y generar abstracciones prematuras.**

**Cuidado con los selectores anidados**. Hay casos, como en el organismo courses, que nos va a interesar **no acoplar demasiado** al contenido:

- Ahora tenemos un grid de cards, pero se podría dar el caso que en un futuro, cambiáramos la molécula card por otra. Esto, combinado a que lo queremos estilar **no tiene relación directa** con card, hace que **la mejor opción sea crear una nueva clase,** `.courses__item`.
- En cambio, si realmente quisiéramos **sobreescribir alguna propiedad de card** (quitar el border-radius, por ejemplo), tendría sentido usar el selector `.courses .card`.

# Utilities

En esta **capa final** pondremos los utility-classes, y como queremos que **sobreescriban** cualquier estilo, es licito usar `!important`.