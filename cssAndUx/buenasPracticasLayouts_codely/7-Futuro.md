

# Futuro de los layouts

<span style="color:tomato;">**Poco soporte todavía (2021/4/20)**</span>

## Display

La propiedad `display` nos cambia como se comporta **el elemento hacia \*fuera\*** (con `inline`, `block`, ...) o **como se comportan sus \*hijos\*** (con `flex` y `grid`).

Para combinar ambas funcionalidades, antes se podían usar dos valores, por ejemplo

`display: inline flex;` pero esta opción será deprecada por valores compuestas,

`display: inline-flex`.

- [mas info](https://developer.mozilla.org/en-US/docs/Web/CSS/display)

## Writing mode

Para cambiar dirección del texto. Si al cambiar la dirección de vertical a horizontal, que sentido es width y que height? O margin left o right?

Para solucionar esto, se meterá el `block-size: 150px;` que nos **limitará el ancho del bloque  independiente de su orientación**.

Para solucionarlo con los margins, se introducirán `margin-start` y `margin-end` .

Muy util para multi-idiomas y lectura vertical.

- [mas info](https://developer.mozilla.org/en-US/docs/Web/CSS/writing-mode)

## Subgrid

Para grids **anidados**, para que el **hijo herede las columnas del elemento padre**.

- [mas info](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout/Subgrid)

## Container queries

- [Container queries en CSS Tricks](https://css-tricks.com/container-query-discussion/)

