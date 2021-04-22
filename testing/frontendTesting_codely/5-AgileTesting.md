# Agilizando el proceso de testing

## Mejorar la mantenibilidad de nuestros tests con custom renderers

- [Código en Github](https://pro.codely.tv/library/testing-frontend/196940/path/step/113170813/)

Cuando trabajamos con librerías de gestión de estado, routing, i18n, ... que necesitamos en la mayoría de componentes, puede ser p**oco práctico tener que configurar lo mismo cada vez que escribimos un test**.

Para solucionar esto, crearemos un **custom renderer que inicialice y configure todo lo necesario, lo importaremos en nuestros tests y lo usaremos para renderizar nuestros componentes**.

## Agilizar la creación de datos fake con Test Object Factories (a.k.a ObjectMothers)

- [Código en GIthub](https://github.com/CodelyTV/javascript-testing-frontend-course/tree/main/72-test-object-factory)
- Post presentando el patron [ObjectMother](https://martinfowler.com/bliki/ObjectMother.html)

Utilidades para crear datos fake:

- [Fishery](https://github.com/thoughtbot/fishery): Librería para **crear objetos mock** definiendo las keys que va a tener ese objeto.
- [Faker](https://github.com/marak/Faker.js/): Librería para **crear datos fake**.

```jsx
import { Factory } from "fishery";
import { date, lorem } from "faker";

const commentFactory = Factory.define(({ sequence }) => ({
  id: sequence,
  date: date.recent().toISOString(),
  content: lorem.paragraph(),
}));
```

Podemos exportar la factory y hacer uso de métodos.

```jsx
export function generateCommentList(min = 0, max = 10) {
  const length = Math.random() * (max - min) + min;
	// le pasamos cuantos elementos queremos que construya para la lista
  return commentFactory.buildList(length); 
}

export function generateComponent(params) {
	// **sobreescribiremos las keys** que le pasemos en params
	return componentFactory.build(params);
}
```

## Snapshot testing ¿sí o no?

- [Código en Github](https://github.com/CodelyTV/javascript-testing-frontend-course/tree/main/73-snapshots)
- [Docu de Jest sobre Snapshot-Testing](https://jestjs.io/docs/snapshot-testing)

Esto parece una forma rápida de testear la presentación de nuestros componentes, pero tiene sus contras.

❌ Si decidimos hacer un **cambio en nuestro HTML, el test no pasará** y tendremos que actualizar los snapshots.

❌ Hemos visto en el curso que **testear componentes presentacionales no aporta mucho valor**, así que el caso de uso más relevante de los snapshots nos aporta poco.

❌ Tampoco podremos usar Object Factories con datos aleatorios.

❌ Los logs al fallar el test serán **poco explicativos**. En vez de decirnos tal propiedad no es la esperada nos dirá que el churro del HTML no coincide.