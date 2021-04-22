# **Maquetar una galería responsive sin media queries: entendiendo Flex y Grid**

- [Demo](https://codelytv.github.io/css-layouts-best-practises-course/2-1-responsive-flex/)

## Flex

- [CSS Tricks: A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- *flex-basis:* El espacio que tiene el elemento que tiene antes de repartirse el espacio libre. (mas o menos como el *min-width* dentro de flex). Por ejemplo, si un elemento tiene un *10rem*, esos *10rem* dejar de contar cómo espacio libre.

## Grid

- [CSS Tricks: A Complete Guide to Grid](https://css-tricks.com/snippets/css/complete-guide-grid/)

- `grid-template-columns: 1fr 1fr 1fr 1fr`

  - fr: **fracción** del espacio disponible

- mas corto → `grid-template-columns: repeat(4, 1fr);`

- con auto-fill nos **lo rellena con las columnas que él vea según el ancho disponible**.

  `grid-template-columns: repeat(auto-fill, 1fr)`

  problema: las columnas tienen ancho fijo, por lo que nos pueden quedar espacios sin rellenar.

- para **ancho dinamico de columnas**: `grid-template-columns: repeat(auto-fill, minmax(18rem, 1fr))`

# Buenas prácticas con Flex y Grid

- [Demo](https://codelytv.github.io/css-layouts-best-practises-course/3-1-grid-areas-order/)

### Grid areas y order

```html
<div class="block">
	<section class="title">...</section>
	<section class="content">...</section>
</div>

```

```css
.block {
	display: grid;
	grid-template-areas:
		'title    title   title title'
		'content content content content';
}

.title {
	grid-area: title;
}

.content {
	grid-area: content
}
```



Con en un **flex**, sj queremos cambiar el orden de los elementos sin cambiar el flex-direction, podemos especificar el *order* en el elemento (+/- como el indice que queremos que ocupe en la lista). A **mayor order, mayor indice**.

Ojo! Esto **sólo cambia el orden visual**, el orden de tabulación y foco no cambia, por lo que puede haber **problemas al navegar por teclado.**

## Cuando usar Flex y Grid

Ambas opciones pueden convivir, depende de lo que se quiera hacer.

### Controlar **1 dimension**:

En este caso tendrá sentido usar `flex` con `flex-direction: row` o `column` dependiendo de si queremos que sea horizontal o verticalmente. En este caso, los elementos **sólo tendrán relación entre ellos en el \*axis\* que hayamos definido**. Por ejemplo, en una  `row` **solo tendrán relación horizontalmente**, no a nivel de columnas.

### Controlar 2 **dimensiones**:

Si queremos controlar 2 dimensiones, usaremos `grid`. Así, los elementos estarán relacionados en ambos ejes, por ejemplo, **para que tengan el mismo ancho y alto**.

### ¿Prioridad de contenido o de layout?

Si nos interesa un **layout "rígido"**, la capacidad de definir columnas y filas de `grid` nos interesa, ya que el contenido se adaptará a las celdas dentro del `grid`.

Por el contrario, si nos interesa que los **elementos ocupen el espacio que necesiten según su contenido y que el layout cambie** según éste, nos interesará `flex`.