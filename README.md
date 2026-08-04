# Iter

### Aprende una vez. Usa cualquier biblioteca.

**Iter** es una interfaz universal para trabajar con recursos, formatos, bibliotecas y backends mediante una API coherente.

## Qué problema busca resolver

Cada biblioteca suele utilizar nombres, estructuras y flujos diferentes. Iter propone una capa común que conserva las capacidades importantes de cada backend y reduce el código de integración repetido.

## Vista previa técnica

Esta es una demostración de cómo se utilizará Iter cuando se publique. Todavía no es un paquete instalable.

```python
import iter

resource = iter.open("data.json")
converted = iter.convert(resource, "csv")
iter.export(converted, "data.csv")
```

Iter identifica el recurso, resuelve su formato, selecciona un adaptador compatible y coordina la operación mediante una API común.

## Estado actual

- **Versión:** `0.3.0-rc.2`
- **Etapa:** candidata de lanzamiento en validación privada
- **Lenguaje principal:** Python
- **Prioridades:** corregir los errores restantes, completar las pruebas y preparar la publicación oficial
- **Repositorio principal:** privado mientras termina la auditoría pública
- **PyPI:** todavía no existe un paquete oficial publicado por Iter Project

> No instales paquetes con nombres parecidos pensando que pertenecen a Iter Project. La publicación oficial se anunciará únicamente desde este perfil y los canales técnicos oficiales.

## Arquitectura

- `Resource`: representación universal de archivos, datos y recursos web
- `Adapter`: integración de operaciones y backends
- `Registry`: registro y selección de adaptadores
- `Resolver`: detección de formatos, tipos y compatibilidad
- `Engine`: coordinación de las operaciones

## Principios

- Everything is a Resource.
- Probar antes de anunciar progreso.
- Privacidad y permisos por diseño.
- Interfaces simples sin ocultar diferencias importantes.
- Lanzamientos pequeños, útiles y verificables.

## Comunicación inicial

Por ahora, Iter se presentará únicamente mediante:

- GitHub;
- documentación técnica;
- ejemplos de código;
- demostraciones grabadas o capturas reproducibles;
- GitHub Releases cuando la versión esté preparada.

No se publicará un paquete de demostración. La primera instalación disponible corresponderá a una distribución oficial de Iter.

## Próximamente

Se mostrarán ejemplos reales de `open`, `create`, `save`, `convert`, `export`, resolución de formatos y selección de adaptadores. El código principal permanecerá privado hasta terminar la auditoría de seguridad, la revisión de la licencia y la preparación de la distribución pública.

---

> Iter — una interfaz común para un ecosistema de herramientas diferentes.
