# Iter — Vista previa técnica

> Esta página muestra la experiencia de usuario prevista para Iter. Todavía no es una distribución instalable ni una publicación en PyPI.

## Aprende una vez. Usa cualquier biblioteca.

Iter no debería obligar al usuario a comenzar cada ejemplo con `import`, configurar rutas temporales ni escribir código auxiliar que no forma parte de su intención.

La experiencia pública debe centrarse en lo que el usuario quiere hacer.

## Abrir, convertir y exportar

```iter
data = iter open "data.json"
csv = iter convert data to "csv"
iter export csv as "data.csv"
```

Tres intenciones claras:

1. abrir un recurso;
2. convertirlo;
3. exportarlo.

Iter se encarga de identificar el recurso, resolver su formato, seleccionar un adaptador compatible y coordinar la operación.

## Crear, guardar y volver a abrir

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

## Usar una biblioteca o backend

```iter
iter use "pandas"
data = iter open "sales.csv"
summary = iter analyze data
show summary
```

El usuario expresa la intención. Iter resuelve cómo ejecutarla mediante el backend o adaptador disponible.

## Consultar las capacidades

```iter
show iter about
show iter capabilities
show iter adapters
```

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

- `Resource`: representación universal del recurso.
- `Resolver`: identificación de formatos, tipos y backends.
- `Registry`: registro y selección de adaptadores.
- `Adapter`: ejecución de operaciones concretas.
- `Engine`: coordinación del sistema.

## Qué busca eliminar de la experiencia del usuario

- imports repetitivos;
- configuración auxiliar innecesaria;
- nombres completamente distintos para la misma intención;
- selección manual de cada detalle del backend;
- código de integración repetido.

## Operaciones previstas para la primera publicación

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

## Estado actual

- Versión candidata: `0.3.0-rc.2`
- Estado: corrección de errores y validación privada
- Código principal: privado
- Distribución oficial: todavía no publicada
- Objetivo: que los ejemplos públicos sean ejecutables con la experiencia sencilla de Iter

La forma final de la sintaxis se validará antes del lanzamiento. No se anunciará como disponible ninguna instrucción que todavía no funcione de manera verificable.

## Qué no se publica todavía

- el código fuente privado completo;
- Iter Server;
- Iter Storage;
- credenciales, tokens o datos personales;
- herramientas internas de administración;
- funciones sin pruebas verificables;
- ningún paquete demostrativo.

---

**Iter — Everything is a Resource.**
