# Shared Kernel

### ¿Qué compartimos entre Bounded Contexts?

- Se puede compartir entre diferentes BCs o incluso dentro de un mismo BC entre diferentes módulos.

  - Cuando **dentro de un BC** dos módulos tienen lógica común, irá al *./shared* dentro del mismo BC.
  - Cuando **dos BCs diferentes** necesitan lógica común, se creará **un tercer BC (ej. \*SharedContext\*)** para que los otros dos importen lógica de ahi.

- Separando conceptos y poniendo los **comunes** en el SharedKernel, en vez de importar directamente lógica de un BC en otro, ganamos en desacoplamiento, testabilidad, ....

- <span style="color:red;">Cuidado con las abstracciones prematuras</span>.

  - El flujo recomendado sería no llevar a Shared ningún código hasta que veamos que se está utilizando en más de un lugar y además tiene sentido que así sea

- Buen sitio para guardar la 

  infraestructura compartida

  - Guardar la implementación no la instancia. <u>Cada BC debería de tener su propia instancia</u>, cada una con sus particularidades (por ej. parámetros de configuración).