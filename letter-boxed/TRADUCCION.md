# Letter Boxed en español — notas

Formar palabras con 12 letras repartidas en los 4 lados de un cuadrado. Dos letras
seguidas no pueden ser del mismo lado, y la última letra de una palabra es la
primera de la siguiente.

## Qué se cambió

| Archivo | Cambio |
|---|---|
| `index.html` | se quitó el encabezado/pie/publicidad de NYT, se repuntaron los assets a las copias locales, y se puso el **puzzle en español** dentro de `window.gameData` |
| `game-assets/v2/letter-boxed.<hash>.js` | interfaz traducida + se sacó el muro de pago (siempre gratis) |
| `game-assets/v2/fonts/` | **nuevo** — las tipografías del juego (antes daban 404) |
| `game-assets/adnsur-*` | logo e ícono de ADN SUR |

## El puzzle (editable a mano)

Todo está en `index.html`, en `window.gameData`:

- `sides` — los 4 lados, 3 letras cada uno (12 en total, sin repetir). Hoy:
  `["EAF","IMN","OTU","SCV"]`.
- `ourSolution` — una solución de ejemplo: `["VAMOS","SUFICIENTE"]`.
- `dictionary` — **todas** las palabras que el juego acepta (mayúsculas, ≥3 letras,
  solo con esas 12 letras y sin dos letras seguidas del mismo lado). Son ~8700.
- `par` — objetivo de cantidad de palabras (3).
- `yesterdaysSolution` / `yesterdaysSides` — el "puzzle de ayer" que se muestra.

Para armar un puzzle nuevo hay que elegir 12 letras que tengan solución y regenerar
el diccionario — no es trivial a mano. Si querés otro, pedímelo.

Origen del diccionario: lista abierta
[`an-array-of-spanish-words`](https://github.com/words/an-array-of-spanish-words).
Es permisivo (incluye muchas conjugaciones); si alguna palabra no te gusta,
borrala del array `dictionary`.

## Textos del juego

En `game-assets/v2/letter-boxed.<hash>.js` (texto legible): "Ayuda", "Reiniciar",
"Jugar", "Cómo jugar", "No es una palabra", "¡Genio!", etc. Buscá la frase y
reemplazala.

## Cómo ejecutarlo

Necesita servidor local:

```
python3 -m http.server 8000
```

y abrir `http://localhost:8000/letter-boxed/`.
