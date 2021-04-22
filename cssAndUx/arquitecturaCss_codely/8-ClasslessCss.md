# Arquitecturas CSS sin clases

# **Arquitecturas con utility-classes (e.g Tailwind)**

Podemos aplicar las capas mediante la directiva `@layer`.

La capa de *Settings* la encontramos en la propia configuración de Tailwind, donde añadimos nuestras variables de colores corporativos, tipografía, etc.

Podemos agrupar repeticiones de clases en clases propias, lo que en nomenclatura Tailwind se consideran components.

```scss
@layer components {
  .flex-justified {
    @apply flex flex-wrap items-center justify-between;
  }
  .flex-centered {
    @apply flex flex-wrap items-center justify-center;
  }
}
```

Tailwind **ya incluye normalize**. La **capa de estilos genéricos** la añadiremos con la utilidad `@layer base` que nos ofrece Tailwind.

```scss
@layer base {
  h1,
  h2,
  h3 {
    @apply font-light leading-tight;
  }

  h1 {
    @apply text-5xl my-12;
  }

  h2 {
    @apply text-4xl my-9;
  }
}
```

Si necesitamos **alguna opción que no esté en Tailwind** podemos añadirla en la capa *Utilities.*

```scss
@layer utilities {
  .basis-0 {
    flex-basis: 0;
  }
  .basis-1\\/2 {
    flex-basis: 50%;
  }
  .flex-grow-max {
    flex-grow: 9999;
  }
}
```

Estas **capas las podemos** **separar por archivos**, pero si no crecen mucho también **podemos incluirlas en el mismo** `index.css`**.**

```scss
styles
├── base.css
├── components.css
├── utilities.css
└── index.css
components
├── common
│       ├── Header.vue
│       └── Footer.vue
├── courses
│       ├── Hero.vue
│       └── Gallery.vue
└── ui
				├── objects
				│       ├── Container.vue
				│       └── UiList.vue
				├── atoms
				│       ├── Button.vue
				│       ├── Image.vue
				│       └── Pill.vue
				└── molecules
				        ├── Card.vue
				        └── Form.vue
tailwind.config.js
```

# **Arquitecturas CSS-in-JS con  Styled Components**

[Demo en Github](https://github.com/CodelyTV/css-architecture-course/tree/main/8-2-styled-components)

Las variables de nuestra aplicación pueden estar en nuestra carpeta de estilos, pero tendrán que ser objetos JavaScript.

```scss
{
  primary: 'rgb(255, 202, 77)',
  seondary: 'rgb(26, 147, 200)',
  primaryLight: 'rgb(255, 232, 179)',
  basePadding: '10px',
  baseMargin: '0 1em',
  baseBorder: '1px solid rgb(204, 204, 204)',
  fontFamilySans: '\\'Helvetica\\', \\'Arial\\', sans-serif',
  baseFontSize: '16px',
  lineHeight: '28.8px'
}
```

Pasando este objeto a `ThemeProvider` de Styled Components, nos permite que todos los componentes descendientes tengan acceso a las variables.

```jsx
import { ThemeProvider } from "styled-components";

const theme = require('sass-extract-loader?{"plugins": ["sass-extract-js"]}!./styles/settings/_variables.scss');

function App() {
  return (
    <ThemeProvider theme={theme}>
      <Header />
      <Hero />
      <Courses />
			<Footer />
    </ThemeProvider>
  );
}
```

Styled Components nos permite **extender los estilos** de otro componente de la siguiente manera:

```jsx
const MyComponent = styled(OtherComponent)`
  font-size: 1.5rem;
`;
```

Una opción para reutilizar código es crear **componentes de layout flexibles** que no van a añadir estilos a sí mismos, sino a su descendiente:

```jsx
export const Justify = styled.div.attrs((props) => ({
  alignItems: props.alignItems || "center",
}))`
  > * {
    display: flex;
    flex-wrap: wrap;
    align-items: ${(props) => props.alignItems};
    justify-content: space-between;
  }
`;
```

❌ Nos queda el template con muchas propiedades relacionadas con CSS, cosa que dificulta la trazabilidad de los estilos:

```jsx
<Sidebar position="first-child" minWidth="60%" sidebarWidth="25rem">
	<Container>
		{ //... }
  </Container>
</Sidebar>
```

✅ En estos casos puede ser preferible reutilizar código de otra forma: al usar JavaScript, **podemos también crear funciones que nos devuelvan el string de CSS con sus variables**. Es lo más parecido a un mixin de Sass:

```jsx
export function includeSidebar({
  gap = "1rem",
  sidebarPosition = "last-child",
  sidebarWidth = "auto",
  minWidth = "50%",
}) {
  return `
  display: flex;
  flex-wrap: wrap;
  gap: ${gap};
  > * {
    flex-basis: ${sidebarWidth};
    flex-grow: 1;
  }
  > ${":" + sidebarPosition} {
    min-width: ${minWidth};
    flex-basis: 0;
    flex-grow: 999;
  }
`;
}
```

Podemos importar y usar esta función en cualquier componente, una solución que permite que la responsabilidad del estilo siga estando en la parte de CSS, es más flexible y fácil de entender:

```jsx
const SubscribeContainer = styled(Container)`
  ${includeSidebar({
    sidebarPosition: "first-child",
    minWidth: "60%",
    sidebarWidth: "25rem",
  })}
  padding-top: ${(props) => props.theme.spacingL};
  padding-bottom: 5rem;

  > :first-child {
    padding-right: 10vw;
  }
`;
```

A nivel de estructura nos quedaría muy parecido a lo que hemos visto hasta ahora:

```
styles
├── settings
│       ├── _colors.scss
│       └── _typography.scss
├── generic
│       ├── _normalize.scss
│       └── _box-sizing.scss
├── elements
│       ├── _headings.scss
│       ├── _images.scss
│       └── _links.scss
├── utilities
│       ├── _typography.scss 
│       └── _error.scss
└── index.scss
components
├── common
│       ├── Header.js
│       └── Footer.js
├── courses
│       ├── Hero.js
│       └── Gallery.js
└── ui
				├── objects
				│       ├── Container.js
				│       └── UiList.js
				├── atoms
				│       ├── Button.js
				│       ├── Image.js
				│       └── Pill.js
				├── molecules
				│       ├── Card.js
				│       └── Form.js
				└── utils
				        └── includeSidebar.js
```