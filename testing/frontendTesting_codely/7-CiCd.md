# CI/CD

## Añadiendo testing en nuestro flow de trabajo

- [Código en Github](https://github.com/CodelyTV/javascript-testing-frontend-course)

Los tests nos brindan seguridad real cuando se **ejecutan periódicamente**, no cuando el developer se acuerda de correrlos.

Hay varias herramientas de integración continúa:

- [Github Actions](https://github.com/features/actions)
- [GitLab](https://docs.gitlab.com/ee/ci/pipelines/)
- [CircleCI](https://circleci.com/)

### How To Github Actions

- Para crear un workflow que ejecute los tests por cada push, añadiremos un `.yaml` en la carpeta `.github/workflows`:

  ```yaml
  name: test
  
  on: push
  
  jobs:E
    test:
      runs-on: ubuntu-latest
  
      steps:
        - uses: actions/checkout@v2
  
        - name: Cache node modules
          uses: actions/cache@v2
          env:
            cache-name: cache-node-modules
          with:
            path: ~/.npm
            key: ${{ runner.os }}-build-${{ env.cache-name }}-${{ hashFiles('**/package-lock.json') }}
            restore-keys: |
              ${{ runner.os }}-build-${{ env.cache-name }}-
              ${{ runner.os }}-build-
              ${{ runner.os }}-
  
        - name: Install Dependencies
          run: npm install
          working-directory: ./91-ci # solo añadir si no tenemos el proyecto en la raíz
  
        - name: Test
          run: npm test
          working-directory: ./91-ci # solo añadir si no tenemos el proyecto en la raíz
  ```

En la [documentación de Github Actions](https://docs.github.com/en/actions/reference/events-that-trigger-workflows) tenemos opciones de filtrar por rama, ejecutar el workflow al hacer una PR, ....

Podemos forzarnos a ejecutar los tests en local con [Husky](https://typicode.github.io/husky/#/), usando sus scripts *precommit*, *prepush*, ... Lo interesante sería hacerlos **antes de hacer push**:

- Para **no bloquearnos a la hora de desarrollar** y hacer commits intermedios.
- Para tener una red de seguridad **antes de subir nada que se rompa**.