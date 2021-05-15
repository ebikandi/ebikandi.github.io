# Value Objects: Modelando nuestro dominio

## Refactorizando ValueObjects

Una clase con diferentes validaciones. Eg, *password*, que valide que tenga*:*

- Mínimo 5 caracteres.
- Mayusculas y minúsculas.
- Letras y números.
- ...

Esto puede llevar a la anidación masiva:

```tsx
if(5chars) {
	if(LowerAndUpperCase){
		if(Alphanumeric){
			password = value;
		} else {
			throw new Error("Not Alphanumeric");
		}
	} else {
		throw new Error("Not LowerAndUpperCase");
	}
} else {
	throw new Error("Not 5 chars");
}
```

Para <u>evitar esa anidación</u>, una herramienta son las <u>cláusulas de guarda</u>:

```tsx
// Acercamos la excepción a la condición
if(!5chars){
	throw new Error("Not 5 chars");
}
if(!LowerAndUpperCase){
	throw new Error("Not LowerAndUpperCase");
}
if(!Alphanumeric){
	throw new Error("Not Alphanumeric");
}
password = value;
```

Cada cláusula de guarda se puede extraer a un método:

```tsx
// Revela la intención a primera vista
ensureMinLength(value){
	if(!5chars){
	throw new Error("Not 5 chars");
	}
}
```

Todas las cláusulas de guarda, validaciones, ... de una misma entidad se pueden <u>encapsular dentro de una clase (*ValueObject*) y llamar en el constructor</u> para detectar posibles fallos lo antes posibles.

➕ DRY

➕ Semántica

➕ Lógica cerca del dominio

```tsx
class StudentPassword {
  value: string;

  constructor(value) {
    this.ensureMinLength(value);
    this.ensureLowerAndUpperCase(value);
    this.ensureAlphaNumeric(value);
    this.value = value;
  }

  private ensureMinLength(value){
    if(value.length < 5){
      throw new Error("Not min length")
    }
  }
  ...
}

// La entidad tipara sus atributos usando los ValueObjects
class Student {
  login(name: StudentName, psw: StudentPassord){
    ...
  }
}
```

## ¿Dónde poner validaciones?

- Varias opciones:
  - Controller, useCase, ValueObjects, Entidad, Servicio de Dominio, .....
- <u>Opción más sencilla</u>: Doble  validación (duplicar lógica en el front).
- <u>No devolver nada</u> en vez de lanzar una excepción.
- <u>Servicio compartido</u>. En el caso de que la validación cambie dependiendo de desde dónde se le llama, no nos valdría.