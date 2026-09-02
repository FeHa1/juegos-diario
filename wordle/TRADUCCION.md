# Wordle en español — notas de la traducción

## Qué se cambió

| Archivo | Cambio |
|---|---|
| `index.html` | idioma `es`, título/metadatos, y carga `palabras.js` antes del juego |
| `palabras.js` | **nuevo** — las listas de palabras en español (editable a mano) |
| `main.b84b7aa7.js` | lógica + todos los textos visibles traducidos; además reformateado a texto legible |

> Todos los `.js`, `.css` y `.html` del repo se reformatearon (de 1 línea a texto
> indentado) para poder leerlos. En los `index.html`, los datos de cada puzzle
> (`window.gameData`) quedaron como JSON legible, editable a mano. El código de
> programa dentro de los `<script>` se dejó tal cual (reformatearlo lo rompía).
> Única excepción: `mini-crossword/games-assets/fonts-*.js`, que es solo datos de
> fuentes en base64.

## `palabras.js` — las palabras

Es lo único que hace falta tocar para cambiar el vocabulario.

- `WORDLE_ES_SOLUCIONES` — respuestas diarias **en orden**. `[0]` es hoy, `[1]` mañana…
  Son ~2000, tomadas de una lista de frecuencia del español (las más comunes primero).
- `WORDLE_ES_ACEPTADAS` — ~8800 palabras más que se aceptan como intento válido.

Reglas para cada palabra: **5 letras exactas**, solo `a`–`z` y `ñ`, **sin tildes**
(se escribe `cafe`, `arbol`, `nino`/`niño`). Entre comillas, separadas por comas.

Origen de las listas: diccionario abierto
[`an-array-of-spanish-words`](https://github.com/words/an-array-of-spanish-words)
+ frecuencias de
[`hermitdave/FrequencyWords`](https://github.com/hermitdave/FrequencyWords).

> Nota: como se ordenan por frecuencia, entre las primeras hay varias formas
> verbales (`estoy`, `vamos`, `tengo`). Si preferís que las respuestas sean más
> "de diccionario", reordená o recortá `WORDLE_ES_SOLUCIONES` a mano.

## Textos del juego (`main.b84b7aa7.js`)

El archivo se **reformateó** para que sea legible (~2100 líneas, indentado, una
instrucción por línea). Sigue siendo código de programa con nombres de variables
cortos (`Ma`, `Ga`, `Va`…), pero ahora se puede navegar y buscar. Los textos
visibles están en español como texto entre comillas; buscá el que quieras cambiar
y reemplazalo. Ejemplos:

- Elogios al ganar: `["Genial","Magnífico","Impresionante","Espléndido","Muy bien","Uf"]`
- Avisos: `"No está en la lista"`, `"Faltan letras"`
- Modales: `"Cómo jugar"`, `"Estadísticas"`, `"Ajustes"`, etc.

Después de editar: guardá y recargá la página. Si algo queda con un error de
sintaxis el juego no carga; en ese caso deshacé el cambio.

## Ñ y acentos

- El teclado en pantalla tiene una tecla **Ñ** (al final de la fila del medio).
- Al escribir con teclado físico, las vocales con tilde se convierten sola
  (`á`→`a`, `é`→`e`…). La `ñ` se escribe con la tecla `ñ`.
- Las palabras se guardan y se muestran **sin tilde**.

## La palabra del día

Se calcula por fecha: `SOLUCIONES[ (días desde el 2 de septiembre de 2026) % total ]`.
Esa fecha de arranque está en `main.b84b7aa7.js` como `Ga=new Date(2026,8,2,0,0,0,0)`
(mes 8 = septiembre, cuenta desde 0).

## Marca ADN SUR (diario ficticio)

Se reemplazó todo lo visible que decía "NYT" / "New York Times" por **ADN SUR**:

- Logo del menú de navegación → `images/adnsur-logo.png` (sobre un recuadro blanco).
- Ícono de la app / accesos directos → `images/adnsur-icon.png` y `images/adnsur-mask.svg`.
- Menú: "Más juegos de ADN SUR", "ADN SUR", "ADN SUR Cocina", "ADN SUR Recomienda".
- Pie de Ajustes: "© 2026 ADN SUR".
- Títulos de la app (`apple-mobile-web-app-title`, `application-name`) → "ADNSUR - Wordle".
- Se quitó el script de cookies que se cargaba desde `nytimes.com`.

Las imágenes originales sin recortar están en
`images/adnsur-logo-original.jpeg` y `images/adnsur-icon-original.jpeg`.
Para cambiar el logo, reemplazá `images/adnsur-logo.png` (ideal ~4:1, fondo claro)
y `images/adnsur-icon.png` (cuadrada).

**Quedan dos enlaces externos** que en el código apuntan a sitios de NYT (no se ven
como texto, solo al pasar el mouse): el "Twitter" de Comunidad (cambiado a `@adnsur`)
y "Preguntas frecuentes" (sigue apuntando a la ayuda de nytimes.com). Los nombres
de fuentes en el CSS (`nyt-franklin`, etc.) son identificadores internos, no se ven,
y esas fuentes ni siquiera cargan.

Los íconos del propio Wordle (`images/wordle-icon-32.png`, `-192.png`) son del juego,
no de la marca: se conservan (solo se les sacó "NYT" del nombre del archivo).

## Volver al Wordle original en inglés

`git checkout minimised -- wordle/` (descarta todos estos cambios en la carpeta),
o directamente volvé a la rama `minimised`.
