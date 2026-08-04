# Iter: una interfaz común para recursos, formatos, bibliotecas y backends

> Esta publicación es una vista previa técnica. Iter todavía no está publicado en PyPI y no existe un paquete oficial instalable.

Las bibliotecas suelen resolver problemas parecidos mediante nombres, estructuras y flujos distintos.

Abrir un recurso, convertir datos, exportar un archivo o cambiar de backend puede exigir aprender una interfaz diferente cada vez. Iter nace de una idea sencilla:

## Aprende una vez. Usa cualquier biblioteca.

Iter propone una API coherente para expresar la intención del usuario y delegar la operación en un adaptador compatible.

```python
import iter

resource = iter.open("data.json")
converted = iter.convert(resource, "csv")
iter.export(converted, "data.csv")
```

La intención permanece clara:

1. abrir un recurso;
2. convertirlo;
3. exportarlo.

Iter se encarga de identificar el recurso, resolver su formato, consultar los adaptadores disponibles y coordinar la ejecución.

## Everything is a Resource

El modelo central de Iter representa archivos, datos y recursos web mediante objetos `Resource`.

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

## Arquitectura

Iter separa la representación, la resolución, la selección y la ejecución.

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

### Componentes principales

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

## Qué Iter no pretende hacer

Iter no pretende borrar todas las diferencias entre bibliotecas ni afirmar que todos los backends son idénticos.

La meta es unificar las intenciones comunes sin ocultar las diferencias importantes.

Tampoco se afirma que Iter sustituya Python o que ya sea un estándar. La primera versión todavía está en preparación.

## Estado actual

- Versión candidata: `0.3.0-rc.2`.
- Estado: corrección de errores y validación privada.
- Distribución oficial: todavía no publicada.
- Código principal: privado durante la auditoría de seguridad y licencia.
- Próximo paso: completar la validación y preparar el lanzamiento oficial.

No se publicará un paquete de demostración. La primera instalación disponible corresponderá a una distribución oficial de Iter.

## Por qué publicar esta vista previa

La intención es mostrar el diseño, recibir observaciones técnicas y explicar el problema que Iter intenta resolver antes del lanzamiento.

Toda función presentada públicamente debe corresponder a una función real y verificable.

---

**Iter — Everything is a Resource.**

Etiquetas sugeridas para DEV o Hashnode: `python`, `programming`, `opensource-discussion`, `softwarearchitecture`, `developer-tools`
