# Triggers (Dispatch) - Ejercicio 

## 1. Configura un workflow para que se ejecute manualmente usando el evento workflow_dispatch.

## 2. Define un input llamado _"message"_ que permita al usuario ingresar un mensaje personalizado.

## 3. El workflow debe ser capaz de imprimir ese mensaje.

Crearemos el workflow `ejercicio1.yaml` en la carpeta de worlflows y este fichero tendrá el siguiente contenido:

```yaml
name: "Triggers (Dispatch) - RLLM"

on:
  workflow_dispatch:
    inputs:
      message:
        description: "Por favor escriba un mensaje personalizado"
        required: true
        default: "Hola desde GitHub Actions!"

jobs:
  imprimir-mensaje:
    runs-on: labs-runner

    steps:
      - name: Mostrar mensaje ingresado
        run: echo "${{ github.event.inputs.message }}"
```

Como podemos ver, el workflow se activa manualmente con workflow_dispatch y solicita al usuario mediante un input el mensaje que desea imprimir, a este input se le asigna un valor por defecto y la descripción que se mostrará al usuario. Luego, el job `imprimir-mensaje` imprime el mensaje ingresado por el usuario en la consola.

Podemos ver el resultado del siguiente dispatch en la siguiente imagen:

