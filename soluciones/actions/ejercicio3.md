# Actions - Ejercicio 3

## Crear un workflow que suba un archivo existente en el repositorio como un artefacto, y luego lo descargue y muestre su contenido en una tarea posterior

Primeramente crearemos nuestro workflow que usará el action de subir y bajar artefactos. 

```yaml
name: Subida y Bajada de Artefactos - RLLM

on:
  workflow_dispatch:

jobs:
  upload-artifact:
    runs-on: labs-runner
    steps:
      - name: Hacemos checkout del repositorio
        uses: actions/checkout@v3

      - name: Subimos el artefacto
        uses: actions/upload-artifact@v4
        with:
          name: archivo-subido
          path: archivoWorkflowRLLM.txt

  download-artifact:
    needs: upload-artifact
    runs-on: ubuntu-latest
    steps:
      - name: Descargando el artefacto
        uses: actions/download-artifact@v4
        with:
          name: archivo-subido

      - name: Mostrar contenido del archivo
        run: cat archivo-subido/archivoWorkflowRLLM.txt
```

En este caso, el primer job sube el artefacto y el segundo job lo descarga y muestra su contenido.

Podemos ver el resultado de la ejecución de los jobs a continuación