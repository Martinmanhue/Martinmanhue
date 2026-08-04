# Comparte Iter

## Mensaje corto

Estoy preparando **Iter**, una API coherente para trabajar con recursos, formatos, bibliotecas y backends.

La vista previa técnica ya está publicada en GitHub. Todavía no hay instalación ni paquete oficial: solo una demostración transparente de lo que saldrá.

⭐ Buscamos a los primeros 10 desarrolladores que quieran seguir el lanzamiento:

https://github.com/Martinmanhue/Martinmanhue

## Mensaje para comunidades de programación

¿Y si abrir, convertir, exportar o buscar recursos no exigiera aprender una interfaz completamente distinta cada vez?

Iter está construyendo una capa común para conservar la intención del usuario y delegar la operación en adaptadores compatibles.

```python
import iter

resource = iter.open("data.json")
converted = iter.convert(resource, "csv")
iter.export(converted, "data.csv")
```

La vista previa es pública, pero el código principal y la instalación siguen privados mientras termina la validación.

Buscamos comentarios técnicos y a los primeros 10 seguidores del proyecto:

https://github.com/Martinmanhue/Martinmanhue

## Regla

No afirmar que Iter integra todas las bibliotecas, reemplaza Python o está terminado. Presentarlo como una Release Candidate en validación y mostrar únicamente funciones reales o previstas claramente identificadas.
