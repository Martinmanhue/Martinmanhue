# Iter — Vista previa técnica

> Esta es una demostración de lo que ofrecerá Iter cuando se publique. Todavía no es un paquete instalable, una beta descargable ni una publicación en PyPI.

## Aprende una vez. Usa cualquier biblioteca.

Las bibliotecas suelen resolver problemas parecidos mediante nombres, estructuras y flujos diferentes. Iter propone una interfaz común para expresar la intención del usuario y delegar la operación en un adaptador compatible.

## Crear, guardar y abrir un recurso

```python
from pathlib import Path
import tempfile

import iter


with tempfile.TemporaryDirectory() as folder:
    destination = Path(folder) / "project.json"

    resource = iter.create(
        "data",
        name=destination.name,
        source=destination,
        data={
            "project": "Iter",
            "status": "preview",
        },
        format="json",
    )

    iter.save(resource, parents=True)

    reopened = iter.open(destination)
    print(reopened.data)
```

Salida prevista:

```text
{'project': 'Iter', 'status': 'preview'}
```

## Transformar y exportar

```python
resource = iter.open("data.json")
converted = iter.convert(resource, "csv")
exported = iter.export(converted, "data.csv")
```

La intención permanece clara:

1. abrir un recurso;
2. convertirlo;
3. exportarlo.

Iter se encarga de resolver el formato, consultar los adaptadores compatibles y coordinar la operación.

## Consultar las capacidades disponibles

```python
print(iter.about())
print(iter.statistics())

for adapter in iter.adapters():
    print(
        adapter.name,
        adapter.backend,
        adapter.capabilities,
    )
```

## Arquitectura

```text
Usuario
  │
  ▼
API pública
  │
  ▼
Resolver ──► Registry ──► Adapter
  │                         │
  └────────── Engine ◄──────┘
              │
              ▼
           Resource
```

- `Resource`: representación universal del recurso.
- `Resolver`: identificación de formatos, tipos y backends.
- `Registry`: registro y selección de adaptadores.
- `Adapter`: ejecución de operaciones concretas.
- `Engine`: coordinación del sistema.

## Funciones previstas para la primera versión pública

| Área | Operaciones previstas |
|---|---|
| Entrada y salida | `open`, `create`, `save`, `close` |
| Resolución | `resolve` |
| Búsqueda | `find`, `search` |
| Transformación | `convert`, `export` |
| Internet | `download`, `upload` |
| Gestión | `copy`, `move`, `rename`, `delete` |
| Colecciones | `list`, `count`, `filter` |
| Adaptadores | `adapters`, `register_adapter`, `unregister_adapter` |
| Backend | `use`, `reset_backend`, `current_backend` |
| Diagnóstico | `statistics`, `about`, `iter doctor` |

## Qué no se publica todavía

- un paquete de demostración;
- el código fuente privado completo;
- Iter Server;
- Iter Storage;
- credenciales, tokens o datos personales;
- herramientas internas de administración;
- funciones que aún no hayan sido verificadas.

## Estado actual

- Versión candidata: `0.3.0-rc.2`
- Estado: corrección de errores y validación privada
- Distribución oficial: todavía no publicada
- Siguiente etapa: completar las pruebas, preparar el lanzamiento y publicar la instalación oficial

Esta página se actualizará solamente con funciones reales y verificadas.

---

**Iter — Everything is a Resource.**
