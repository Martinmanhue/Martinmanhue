# Iter

### Aprende una vez. Usa cualquier biblioteca.

**Iter** es una interfaz universal para trabajar con recursos, formatos, bibliotecas y backends mediante una API coherente.

## Qué problema busca resolver

Cada biblioteca suele utilizar nombres, estructuras y flujos diferentes. Iter propone una capa común que conserva las capacidades importantes de cada backend y reduce el código de integración repetido.

```python
import iter

resource = iter.open("data.json")
print(resource.data)
```

## Estado actual

- **Versión:** `0.3.0-rc.2`
- **Etapa:** candidata de lanzamiento en validación privada
- **Lenguaje principal:** Python
- **Prioridades:** estabilidad, seguridad, documentación y pruebas reproducibles
- **Repositorio principal:** privado mientras termina la auditoría pública
- **PyPI:** todavía no existe un paquete oficial publicado por Iter Project

> No instales paquetes con nombres parecidos pensando que pertenecen a Iter Project. La publicación oficial se anunciará únicamente desde este perfil y los canales oficiales del proyecto.

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

## Canales técnicos previstos

La comunicación inicial de Iter se concentrará en:

- GitHub;
- GitHub Releases;
- documentación técnica;
- TestPyPI para validar el proceso de distribución;
- PyPI cuando la versión pública esté preparada y autorizada.

## Próximamente

Se publicarán demostraciones reproducibles, documentación técnica y avances comprobables. El código principal permanecerá privado hasta terminar la auditoría de seguridad, la revisión de la licencia y la preparación de la distribución pública.

---

> Iter — una interfaz común para un ecosistema de herramientas diferentes.
