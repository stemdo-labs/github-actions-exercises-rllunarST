# Workflows reusables - Ejercicio 2

## Configura un workflow reutilizable que primero valide si el nombre de la rama con la que se ejecuta empieza con "feature/". Solo si la validación es exitosa, se ejecutará la tarea principal

Para realizar este ejercicio crearemos un workflow reutilizable que valide si el nombre de la rama con la que se ejecuta empieza con "feature/". Si la validación es exitosa, se ejecutará la tarea principal. En caso contrario, se mostrará un mensaje de error y no se ejecutará la tarea principal. Este es el contenido del workflow:

```yaml
name: "Validando rama (Reusable) - RLLM"

on:
  workflow_call:

jobs:
  validar_y_ejecutar:
    runs-on: labs-runner
    steps:
      - name: Validando si la rama empieza con 'feature/'
        id: validar
        run: |
          echo "La rama actual es: $GITHUB_REF_NAME"
          if [[ "${{ github.ref_name }}" != feature/* ]]; then
            echo "Esta rama no es correcta, la rama permitida es 'feature/*'."
            exit 1
          fi

      - name: Ejecutando tarea principal
        if: success()
        run: echo "Rama correcta. Ejecutando tarea principal"
```

Ahora crearemos el workflow que ejecutará el workflow reutilizable, este tendrá el siguiente contenido:

```yaml
name: "Usar workflow que valida rama - RLLM"

on:
  workflow_dispatch:

jobs:
  llamar_a_reutilizable:
    uses: ./.github/workflows/reusable_2_1.yaml
```

