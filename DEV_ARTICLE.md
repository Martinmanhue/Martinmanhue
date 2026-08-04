# Iter: programar desde la intención, no desde la configuración

> Esta publicación es una vista previa técnica. Iter todavía no está publicado en PyPI y no existe un paquete oficial instalable.

Abrir un recurso, convertir datos, exportar un archivo o cambiar de backend suele exigir aprender una interfaz diferente cada vez.

Iter nace de una idea sencilla:

## Aprende una vez. Usa cualquier biblioteca.

La experiencia de usuario no debería comenzar con imports, rutas temporales ni configuración auxiliar. Debería comenzar con la intención.

```iter
data = iter open "data.json"
csv = iter convert data to "csv"
iter export csv as "data.csv"
```

La intención permanece clara:

1. abrir un recurso;
2. convertirlo;
3. exportarlo.

Iter debe encargarse de identificar el recurso, resolver el formato, consultar los adaptadores disponibles y coordinar la ejecución.

## Crear y guardar sin código auxiliar

```iter
project = iter create "data" {
    project: "Iter"
    status: "preview"
}

iter save project as "project.json"
reopened = iter open "project.json"
show reopened.data
```

Salida prevista:

```text
{project: "Iter", status: "preview"}
```

## Usar una biblioteca mediante una intención común

```iter
iter use "pandas"
data = iter open "sales.csv"
summary = iter analyze data
show summary
```

El usuario expresa qué quiere hacer. Iter resuelve qué backend o adaptador puede realizar la operación.

## Everything is a Resource

El modelo central de Iter representa archivos, datos y recursos web mediante objetos `Resource`, pero esa arquitectura no debería obligar al usuario a escribir detalles internos cada vez.

## Arquitectura

```text
Usuario
  │
  ▼
Lenguaje y API de Iter
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

## Qué busca eliminar de la experiencia pública

- imports repetitivos;
- configuración auxiliar innecesaria;
- APIs completamente distintas para intenciones equivalentes;
- selección manual de cada detalle del backend;
- código de integración repetido.

## Operaciones previstas para la primera versión

| Área | Operaciones |
|---|---|
| Entrada y salida | `open`, `create`, `save`, `close` |
| Resolución | `resolve` |
| Búsqueda | `find`, `search` |
| Transformación | `convert`, `export` |
| Internet | `download`, `upload` |
| Gestión | `copy`, `move`, `rename`, `delete` |
| Colecciones | `list`, `count`, `filter` |
| Backend | `use`, `reset`, `current` |
| Diagnóstico | `about`, `capabilities`, `adapters`, `doctor` |

## Lo que Iter no pretende hacer

Iter no pretende afirmar que todos los backends sean idénticos ni que todas las bibliotecas estén integradas desde el primer día.

La meta es unificar las intenciones comunes sin ocultar las diferencias importantes.

## Estado actual

- Versión candidata: `0.3.0-rc.2`.
- Estado: corrección de errores y validación privada.
- Distribución oficial: todavía no publicada.
- Código principal: privado durante la auditoría.
- Próximo paso: verificar que la sintaxis pública mostrada sea realmente ejecutable.

La forma final puede ajustarse antes del lanzamiento. No se presentará como disponible ninguna instrucción que todavía no funcione de forma verificable.

---

**Iter — Everything is a Resource.**

Etiquetas sugeridas: `programming`, `softwarearchitecture`, `developer-tools`, `languages`, `python`
