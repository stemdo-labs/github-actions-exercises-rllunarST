# Jobs y Steps - Ejercicio 2

## 1. Configura dos jobs en un único workflow: "build" y "deploy"
- En el job deploy imprime un mensaje por la consola.
- El job deploy debe depender del éxito del job build.
- Si el job "build" falla, el job "deploy" **no debe ejecutarse.**

Para este ejercicio crearemos otro nuevo workflow de tipo `.yaml` este fichero se llamará `jobs_2.yaml` y el contenido del workflow será el siguiente:

```yaml
name: "Jobs y Steps - RLLM"

on:
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Primer paso (Compilar)
        run: |
          echo "Compilando proyecto..."
          # Puedes simular un error con: exit 1

  deploy:
    needs: build
    runs-on: ubuntu-latest
    steps:
      - name: Despliegue
        run: echo "El despliegue se realizó correctamente! La build fue exitosa!"
```

Como podemos ver podemos hacer que en un workflow haya diferentes jobs y que cada job para realizarse dependa de otro, en este caso el job `deploy` depende del job `build`. Si el job `build` falla, el job `deploy` no se ejecutará. Esto es útil para asegurarnos de que el despliegue se realice si la compilación fue exitosa.

Ahora probaremos el funcionamiento del workflow como podemos ver en la siguiente imagen:

