# Multi-Column: Efecto masonry CSS-only

- [Demo](https://codelytv.github.io/css-layouts-best-practises-course/5-2-multi-column-masonry/)

Se puede hacer gracias a la especificación [column](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Columns)

```css
.container{
	display: grid;
	grid-template-colums: repeat(auto-fill, minmax(18rem, 1fr));
	column-width: 18rem; /*en el container, definir el ancho de columna*/
}

.child {
	/* propiedades break para controlar donde se rompen las columnas */
 /* brea-before, break-after, break-inside */
	 break-inside : avoid; /* dentro del child, no me hagas break */  
}
```

