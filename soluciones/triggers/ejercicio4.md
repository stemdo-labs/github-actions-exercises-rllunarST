# Triggers - Ejercicio 4

## Configura un workflow para que se ejecute todos los días a las 12:00 UTC y que imprima "Scheduled job executed!" en la consola

Para realizar este ejercicio crearemos un nuevo fichero tipo `.yml` que tendrá el nombre `trigger_4.yaml` y tendrá la siguiente estructura:

```yaml
name: "Trigger diario - RLLM"

on:
  schedule:
    - cron: "0 12 * * *"  # Todos los días a las 12:00 UTC

jobs:
  scheduled-job:
    runs-on: ubuntu-latest

    steps:
      - name: Imprimir mensaje
        run: echo "Scheduled job executed!"
```

Este workflow se ejecutará todos los días a las 12:00 UTC y simplemente imprimirá el mensaje "Scheduled job executed!" en la consola. Schedule nos permite programar la ejecución de un workflow en función de una expresión cron. En este caso, la expresión `0 12 * * *` indica que el workflow se ejecutará todos los días a las 12:00 UTC.