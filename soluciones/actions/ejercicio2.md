# Actions - Ejercicio 2

## Crear una custom action usando composite actions que imprime el nombre del autor del último commit en los logs del workflow

Composite nos permite realizar multiples pasos en un shell dentro de nuestro fichero de actions sin necesidad de escribir un script fuera de la action. En este caso lo utilizamos para poder consumir el ultimo commit y mostrarlo en los logs del workflow. De forma agradable

```yaml
name: "Action - Mostrar autor del último commit - RLLM"
description: "Este action imprime el nombre del autor del último commit"
runs:
  using: "composite"
  steps:
    - name: Mostrando autor
      run: |
        echo "El autor del último commit es:"
        git log -1 --pretty=format:'%an'
```

Ahora con este action hecho debemos crear nuestro workflow que funcionará practicamente igual que el del ejercicio pasado solo que en este caso usará nuestro action personalizado.

```yaml
name: "Mostrar autor del ultimo commit - RLLM"

on:
  workflow_dispatch:

jobs:
  mostrar-autor:
    runs-on: labs-runner

    steps:
      - name: Checkout del repositorio
        uses: actions/checkout@v4

      - name: Usando action personalizado
        uses: ./.github/actions/action_2
```

Ahora comprobaremos su funcionamiento desde la pestaña de actions de nuestro repositorio. Al ejecutar el workflow, deberíamos ver en los logs el nombre del autor del último commit.

