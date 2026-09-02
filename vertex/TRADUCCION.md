# Vertex en español — notas

Vertex es unir puntos para formar triángulos y revelar un dibujo. No usa palabras,
así que la traducción es solo de interfaz + los títulos de los puzzles.

## Qué se cambió

| Archivo | Cambio |
|---|---|
| `index.html` | reescrito: se quitó el encabezado/pie/publicidad de NYT, se repuntaron los assets a las copias locales (`./game-assets/…`), se desactivaron las llamadas de red a NYT (login, analytics, cookies), y se tradujeron metadatos + el `window.gameData` (temas y fechas de los puzzles) |
| `game-assets/v2/vertex.<hash>.js` | textos de interfaz traducidos ("Ayuda", "Reiniciar", "Jugar", "Cómo jugar", mensajes de ánimo, etc.) |
| `game-assets/adnsur-*.{png,svg}` | logo e ícono de ADN SUR (copiados de `wordle/images/`) |

## Dónde editar

- **Títulos de los puzzles y fechas** → `index.html`, dentro de `window.gameData`
  (buscá `"theme":` y `"displayDate":`). El tema es la pista sobre el dibujo oculto.
- **Textos del juego** (botones, modal de ayuda, mensajes al terminar) →
  `game-assets/v2/vertex.<hash>.js` (está en texto legible; buscá la frase y
  reemplazala).
- **Menú lateral (☰)** → `index.html`, buscá `Juegos de ADN SUR`.

## Cómo ejecutarlo

Necesita servidor local (carga varios archivos):

```
python3 -m http.server 8000
```

y abrir `http://localhost:8000/vertex/`.

## Detalle menor

En `game-assets/v2/foundation.<hash>.js` (el framework compartido) quedan algunos
textos y un `mailto:` de NYT que **no se ven** en el juego (modal de privacidad que
no se activa, enlace de feedback de reserva). El puzzle del día viene embebido en
`index.html`; las llamadas para traer el puzzle de "hoy" fallan y el juego usa ese.
