# Variables y Outputs - Ejercicio 1

## Configura un workflow con un solo job que haga las siguientes tareas

- En el primer step, define dos variables de entorno.
- En el segundo step, usa estas variables para ejecutar un comando o script.

En este ejercicio creamos un workflow definiendo 2 variables de entorno y luego las usamos ejecutando un echo en el workflow el contenido del este fichero es el siguiente:

```yaml
name: "Usando Variables - RLLM"

on:
  workflow_dispatch:

jobs:
  variables-job:
    runs-on: ubuntu-latest

    steps:
      - name: Definiendo variables de entorno
        shell: bash
        run: echo "NOMBRE=Roy" >> $GITHUB_ENV
        run: echo "CURSO=GitHub Actions por Stemdo" >> $GITHUB_ENV

      - name: Usando las variables de entorno
        run: |
          echo "Hola, me llamo $NOMBRE y estoy aprendiendo $CURSO"
```

Como podemos ver con un echo definimos las variables de entorno y luego las usamos en el segundo step. En este caso, el comando `echo` imprime un saludo que incluye el nombre y el curso. El resultado de la ejecución del workflow es el siguiente:



