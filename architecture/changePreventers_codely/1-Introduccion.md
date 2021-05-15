# Introducción

## ¿Que son los Code Smells de tipo Change Preventers?

Los **Code Smells** son aquellas cosas de nuestro código que <u>nos hacen detectar que algo en nuestro puede estar mal.</u>

- Los **Change Preventers** son aquellos <u>relacionados con la dificultad para cambiar nuestro código</u> en cualquier momento. 

Pongamos como ejemplo un getter que le pasemos un *courseId* y nos devuelva la información del curso en un json.

![image-20210505084446163](assets/1-Introduccion/image-20210505084446163.png)

Vemos que hay puntos sobre diferente logica de negocio, eso ya nos da una pista sobre el tufillo:

- Lógica de duración
- Lógica de puntos

El **principal problema** reside en que cada cajita impregna todas las de abajo (se ve que las cajitas estan dentro):

-  La serialización de retorno impregna el parseo, que a su vez impregna  la lógica de nogocio.
- La solución sería **aislar cada cajita** y sacar las de dentro, para no que no impregne a ningun otra. (*Single Responsibiliy Principle*)

![image-20210505085804543](assets/1-Introduccion/image-20210505085804543.png)

Otra vuelta de tuerca, <u>viendo que el parseo de CSV viene junto con el cálculo de duración y de puntos</u>, podría ser **usar Ports & Adapters**, metiendo un repositorio, y así <u>aislar la los detalles de implementación</u>, para no importe si obtenes los datos de un CSV, JSON, o lo que sea.

![image-20210505092710558](assets/1-Introduccion/image-20210505092710558.png)

## ¿Por qué no se entiende la S de SOLID?

❌ Uncle Bob en su [post definió el SRP](https://blog.cleancoder.com/uncle-bob/2014/05/08/SingleReponsibilityPrinciple.html) como que un "módulo" sólo debería tener una **razón para cambiar**. Esta definción ademas de ser muy **difusa**, podría llevarnos a pensar que "bueno, tendré un módulo de escritura y otro de lectura. Así si la lógica de" persistencia cambia, sólo tendré que cambiar el modulo de escritura".  Esto nos puede llevar a hacer código mirando los detalles de impolementación, o incluso cualquier otro aspecto (porque sabemos que las apps complejas que tenemos hoy en día tienen varios aspectos).

:white_check_mark: Sin embargo, remontandonos unos años, [Dijktstra definio el "separation of concerns"](https://www.cs.utexas.edu/users/EWD/ewd04xx/EWD447.PDF) lo que nos lleva **a una aproximación mas lógica** derivada del dominio. Es decir, **juntar en un módulo todo lo relacionado a un concepto**. Por ejemplo, <u>tener un *OrderRepository* para todos los casos de uso relacionados con la entidad *Order*,</u> y ademas <u>cada método del repositorio "wrappea" un solo caso de uso que es independiente del resto</u>. Esto nos lleva a una aproximación para poder modelar nuestro negocio basandonos en DDD.

