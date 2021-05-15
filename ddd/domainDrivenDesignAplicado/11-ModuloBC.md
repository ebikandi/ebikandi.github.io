# Promoviendo un Módulo a Bounded Context

- **Primer indicador**, la funcionalidad de un módulo ha crecido tanto que vamos a **montar un equipo independiente** para gestionar esa funcionalidad.
- Al promoverlo a BC, tiene sentido remodelarlo y pueden salir nuevos módulos. Por ejemplo, al promover un módulo Notifications a BC, puede tener sentido crearle módulos de Push, Email, ...

### Consideraciones para promover un Módulo a BC

- <u>**Clientes**</u>

La promoción debería de ser transparente para los clientes (no se deberían de enterar). La comunicación se mantendrá desacoplada mediante Bus-es y eventos, por lo que no habría que adaptar los clientes a este cambio.

- <u>**Infraestructura**</u>

El nuevo BC deberá tener su propia infraestructura (Bases de datos, APIs, ....)

- <u>**Namespaces**</u>

Habrá que adaptar los namespaces y los imports.

