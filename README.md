# Iter

### Aprende una vez. Usa cualquier biblioteca.

Estoy construyendo **Iter**, una interfaz universal para trabajar con recursos, formatos, bibliotecas y backends desde una API coherente.

## Qué problema busca resolver

Cada biblioteca suele exigir nombres, estructuras y flujos distintos. Iter propone una capa común que conserva las capacidades importantes de cada backend y reduce el código de integración repetido.

```python
import iter

resource = iter.open("data.json")
print(resource.data)
```

## Estado actual

- **Versión:** `0.3.0-rc.2`
- **Etapa:** candidata de lanzamiento y validación privada
- **Lenguaje principal:** Python
- **Prioridades:** estabilidad, seguridad, documentación y pruebas reproducibles

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

## Próximamente

Se publicarán demostraciones, documentación y novedades del prelanzamiento de Iter. El código principal permanece privado mientras finalizan la auditoría de seguridad, la licencia y la preparación de la versión pública.

---

> Iter — una interfaz común para un ecosistema de herramientas diferentes.
