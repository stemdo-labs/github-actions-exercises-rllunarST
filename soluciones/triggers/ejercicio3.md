# Triggers - Ejercicio 3

## Configura un workflow para que se ejecute cuando se cree una nueva Issue

Para realizar este ejercicio creare un nuevo fichero tipo `.yml` que tendrá el nombre `trigger_3.yaml` y tendrá la siguiente estructura:

```yaml
name: "Creando un nuevo Issue - RLLMe"

on:
  issues:
    types: [opened]

jobs:
  issue-created:
    runs-on: labs-runner

    steps:
      - name: Imprimir mensaje
        run: echo "Has creado un nuevo issue en el repositorio"
```

Ahora si creamos un nuevo issue en el repositorio, se ejecutará el workflow que acabamos de crear. En este caso, el workflow simplemente imprimirá un mensaje en la consola indicando que se ha creado un nuevo issue.

