# Variables y Outputs - Ejercicio 3

## Configura un workflow siguiendo estos pasos:

- Define un step que genere un número aleatorio del 1 al 100.

- En el segundo step, utiliza un condicional para ejecutar comandos solo si el número es mayor a 50.

Para realizar este ejercicio crearemos un nuevo workflow que guarde en una variables el numero aleatorio generado, para generar este numero aleatorio debemos usar el comando `RANDOM` de bash, el cual genera un número aleatorio lo limitamos con 100 y le sumamos uno debido a que generara un numero del 0-99 y no del 1-100. Luego hacemos la comprobación, el resultado final del workflow es el siguiente:

```yaml
name: "Variable con condicional - RLLM"

on:
  workflow_dispatch:

jobs:
  numero-aleatorio:
    runs-on: labs-runner

    steps:
      - name: Generando número aleatorio
        run: |
          NUMR=$((RANDOM % 100 + 1))
          echo "Número generado: $NUMR"

          if [ "$NUMR" -gt 50 ]; then
            echo "El numero aleatorio $NUMR es mayor que 50"
          else
            echo "El numero aleatorio $NUMR es menor que 50"
          fi
```

Ahora si guardamos nuestro workflow y lo ejecutamos veremos el siguiente resultado:


