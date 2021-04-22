# ¿Por qué el testing en frontend esta roto?

# Testear como lo haría un usuario

Hay que testear desde lo que "vería/haría" un usuario, no un valor en el código. **Un test que mire el atributo que tiene un tag, no aporta valor.**

```
❌ expect(MessageComponent.attributes().msg).toEqual("toggled message");

✅ expect(screen.getByText("toggled message")).toBeInTheDocument();
```

# Testear la realidad

Si testeamos componentes de manera aislada, perdemos partes de funcionalidad que pueden ser críticas. Por ejemplo, si usamos *shallowMount* para montar el componente, todos los componentes hijos van a ser reemplazados por un tag vacío como `<message-stub></message-stub>`. Esto hace que nuestros tests sean incompletos.

# Testing Library

- [testing-library.com](https://testing-library.com/)

No podremos acceder a la instancia de nuestro componente para llamar directamente a una función o acceder a una propiedad, en lugar de eso buscaremos los elementos con queries (*getByRole, getByText,* ...).

Lo usaríamos con Jest como base.

# Las bases de testing-library

- [Código en Github](https://github.com/CodelyTV/javascript-testing-frontend-course/tree/main/12-first-test).
- Lo que necesitamos mockear, lo **mockearemos con jest**.
- Podemos usar el objeto `**screen` para hacer queries**.
- **Ojo!** Hay muchos ejemplos con `**fireEvent` para triggear eventos** en inputs.

❌ Pero este código empieza a tocar target.value... y lo que hemos dicho es que no testeariamos **detalles de implementación**, ya que el usuario no sabe esto.

```jsx
fireEvent.change(titleInput, {
  target: { value: "My awesome post" },
});
```

✅ Usar **[userEvent](https://testing-library.com/docs/ecosystem-user-event/)** es mucho mejor porque simula mejor la interacción que puede tener el usuario con el componente..

```jsx
userEvent.type(title, "My awesome post");
```

Vemos que aunque Testing Library nos ayude a testear como lo haría un usuario, no tenemos una garantía 100% que nos lo garantize. Por lo que **como desarrolladores tenemos que preocuparnos por el enfoque de nuestros** tests más allá de la librería que utilicemos.