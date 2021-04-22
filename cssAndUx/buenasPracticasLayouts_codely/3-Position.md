# Maquetar Modales y Menús: entendiendo Position

# Modal: position relative, absolute y fixed

- [Demo](https://codelytv.github.io/css-layouts-best-practises-course/4-1-modal-position/)

### **Relative**

El `relative` **no rompe** el flow.

Todo lo que este dentro de mi, será relativo a mí. Si hay varios relative anidados, **predominará el mas anidado**.

### **Absolute**

El `absolute` **rompe** el flow. El espacio que ocupa el elemento con `absolute` no cuenta para el tamaño del elemento padre.

En base al **parent `relative` mas cercano.** Si pongo un `top: 0;` se pondrá **en el borde superior del parent `relative`**.

### **Fixed**

Posicionamiento **sobre el TopContainerElement (viewport)**.

Hay un **corner-case!** Si el **container del elemento `fixed` tiene un `transform` o `filter`,** cómo estas funciones crean un segundo container, **el posicionamiento se rompe**. El **Consejo** es poner el elemento `fixed` **lo menos anidado posible**.

**Cuidado** con las modales, porque a **pesar de que una modal se muestre y ocupe toda la pantalla, los elementos del "fondo" estarán todavía ahi**, por lo que s**e podrá navegar por teclado sobre ellas** y los screen-readers los podrán detectar. Usar librerías para **atrapar el foco, etc. dentro de la modal.**

# Menú: position sticky

- [Demo](https://codelytv.github.io/css-layouts-best-practises-course/4-2-menu-sticky/)
- El elemento **se "pega" al elemento más cercano que tenga mecanismo de scroll** (a.k.a *scroll-ancestor*), es decir, que tenga un `overflow: scroll`, `overflow:hidden`, ....Por lo que al hacer scroll en cuanto tendría que salir de la pantalla, se "pega" y sigue al scroll.
- **Cuidado** con `sticky` **anidados**, porque según cual sea su *scroll-ancestor* y que tamaño tenga puede que ***e\*l comportamiento no sea el deseado***.* El **Consejo** es poner el elemento `sticky` **lo menos anidado posible**.
- Los sticky "no ocupan" espacio.
- No va en Explorer 🤷
  - Se puede comprobar el soporte con la *media-query* `@support`