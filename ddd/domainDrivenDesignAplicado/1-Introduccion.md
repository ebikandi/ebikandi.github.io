# Introducción



- **Model Driven Design:** Modelar el negocio en el código (lenguaje ubicuo).

- **Entity ≠ ValueObject**

  - **Entity**: Entidades de dominio. <u>Contienen *id*</u>. No saben de <u>lógica</u> (para eso usar repositorios). Eg:

    ```tsx
    user: {
    	**id:** ...,
    	name: ...
    	}
    ```

  - **ValueObject:**  Valores <u>identificables</u> por el propio valor. Eg:

    ```tsx
    color = "red" | "blue" | ...
    ```

- **Agregado:** Concepto que *wrappea* varias entidades. <u>*Order*, que tiene dentro *OrderLine*</u> (*Order* sería el agregado).

  - Construir mediante factorías.
  - *Wrapper* = *AggregatedRoot*

- **DomainEvent:** Notificar algo que ha pasado relativo al dominio (*OrderCreated*, *OrderRemoved*, ...).

- **BoundedContext (BC):** Sub-dominios que tengan <u>sentido</u> dentro de su contexto. Sirven para definir <u>boundaries entre conceptos/contextos</u>. Por ejemplo, no pasa nada por tener <u>dos ficheros con el mismo nombre en *BC*s distintos.</u>

  ```tsx
  BuyingAssistant/OrderLine.ts ≠  Reception/OrderLine.ts
  ```

  - La <u>infra. es independiente entre BCs</u>. Cada uno tiene sus instancias.

- **ContextMap:** Mapear conceptos del dominio.

- **Big Ball of Mud (BBM)**: Monolitazo a refactorizar.

- **Anticorruption Layer:** Mecanismo que definimos como separación entre el BBM y lo nuevo.

- **Separate Ways:** Separar BCs para que cada uno se pueda implementar de la mejor forma.

- **Shared Kernel:** Lógica a compartir entre contextos.