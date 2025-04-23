# Contexts - Ejercicio 2

## Configura un workflow que utilice un secreto llamado PROD_API_KEY para realizar un despliegue ficticio si se ejecuta en la rama main, y otro secreto llamado STAGING_API_KEY para cualquier otra rama

**El workflow debería:**

- Utilizar el contexto secrets para inyectar la API Key correspondiente en un comando de despliegue ficticio.
- Imprimir un mensaje indicando cuál API Key se utilizó.

Para realizar este ejercicio, puedes utilizar el siguiente código como base:

```yaml
name: "Despliegue según rama - RLLM"

on:
  workflow_dispatch:

jobs:
  despliegue:
    runs-on: ubuntu-latest

    steps:
      - name: Decidir entorno por rama
        run: |
          if [ "${{ github.ref_name }}" = "main" ]; then
            echo "Desplegando a producción con clave: ${{ secrets.PROD_API_KEY }}"
          else
            echo "Desplegando a staging con clave: ${{ secrets.STAGING_API_KEY }}"
          fi
```

Como podemos ver en el código, se utiliza el contexto `github.ref_name` para comprobar en que rama se ejecuta esteworkflow, si la rama es main se muestra el mensaje de producción, si no se muestra el mensaje de staging. Como podemos ver en la siguiente captura:

### Resultado para la rama 'main'

![Resultado en rama main](../../datos/imgs/context2_1.png)

Como podemos ver el mensaje de producción se muestra correctamente, pero el secreto no se muestra ya que este es un secreto y los secretos no se n mostrar por consola al ejecutar el workflow.

### Resultado para la rama 'soluciones-rllm'

![Resultado en rama soluciones-rllm](../../datos/imgs/context2_2.png)

Como podemos ver el mensaje de staging se muestra correctamente pero este tampoco se muestra al igual que el anterior por el mismo motivo.