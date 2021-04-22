# 5 errores comunes trabajando con CSS Layouts

- **Alterar innecesariamente el flow** con position fixed.
- **z-index** al tuntun.
- Cuidado con los **tamaños fijos**.
- Abusar de **media-queries**. Hoy en día hay opciones escalables (e.j Grid).
- **Flex Vs Grid**. Se pueden usar los dos dependiendo de la necesidad.

# Cuando usar cada tipo de unidad: mas allá del pixel

1. **rem:** unidad **relativa al root element** (el html). Por defecto, 16px; Muy **util como unidad por defecto/global**. Escala según las preferencias del usuario en el browser.

2. **em:** relativa al **tamaño de fuente del parent**. Util para aplicar a margins/paddings que queremos que **escalen dependiendo del tamaño del fuente**.

3. **ch: ancho del 0**. Para escalar ancho de textos que queremos que **cada linea tenga X caracteres**.

4. **%:** **Relativo al parent.** Para que los elementos **children cambien de proporción al elemento que lo contiene**.

5. **vh** y **vw:** Alto y ancho del viewport. Util para que un elemento anidado **coja la medida del viewport y no el del parent.**

   Por defecto, en **css el width/height de un elemento es proporcional al contenido**. Por lo que poniendo sólo al child el *width:100%*, no cogería el ancho completo si no se lo pusiesemos al #parent también. Sin embargo, **con el 100vw, nos cogerá todo el ancho** automaticamente.

```html
<div id="parent">
	<div id="child"/>
</div>
```

```css
#parent{
	width:100%
}

#child{
	width:100%
}
#child{
	width:100vw;
}
```

