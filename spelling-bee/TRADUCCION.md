# Deletreo (Spelling Bee) en español — notas

Formar la mayor cantidad de palabras posible con 7 letras dispuestas en un panal.
Cada palabra tiene que:

- tener **4 letras o más**,
- usar **sí o sí la letra del centro**,
- usar solo letras del panal (se pueden repetir).

Hay al menos un **pangrama**: una palabra que usa las 7 letras (vale 7 puntos extra).

## El juego es sin tildes ni ñ

Las letras del panal son siempre `a`–`z` (como en el original en inglés). Para que
funcione, el diccionario se normalizó: se sacaron las tildes (`á`→`a`, etc.) y se
descartaron las palabras con `ñ`. O sea: se escribe **"limon", "arbol", "accion"**,
sin tilde. Tampoco entra la `s` como letra del panal (igual que en el NYT, para que
no gane el juego cualquier plural).

## Qué se cambió

| Archivo | Cambio |
|---|---|
| `index.html` | se quitó el encabezado / pie / publicidad de NYT, se repuntaron los assets a las copias locales (`./game-assets/…`), se neutralizaron las llamadas de red a NYT (login, analytics, cookies, suscripción) y se tradujeron los metadatos + el **puzzle** dentro de `window.gameData` |
| `game-assets/v2/spelling-bee.<hash>.js` | interfaz traducida (botones, panal, modales, mensajes de ánimo, nombres de los rangos) y **sin muro de pago** (siempre gratis, todos los rangos disponibles) |
| `game-assets/adnsur-*` | logo e ícono de ADN SUR (copiados de `wordle/images/`) |

## El puzzle (editable a mano)

Está todo en `index.html`, dentro de `window.gameData`:

- `centerLetter` — la letra obligatoria (va en el centro del panal).
- `outerLetters` — las otras 6 letras.
- `validLetters` — las 7 juntas (centro + exteriores).
- `pangrams` — la(s) palabra(s) que usan las 7 letras.
- `answers` — **todas** las palabras que el juego acepta (minúsculas, sin tilde,
  ≥ 4 letras, solo con esas 7 letras y con la del centro). Incluí también los
  pangramas acá.
- `displayDate` / `displayWeekday` / `printDate` — la fecha que se muestra.
- `id` — un número cualquiera, distinto por puzzle (si repetís un `id` el juego
  cree que es el mismo día y no borra el progreso guardado).

El bloque `today` es el puzzle de hoy; `yesterday` es el que se ve en "Respuestas
de ayer".

### Puzzle actual

- **Hoy:** centro `O`, letras `B E H I L O R`, pangrama **horrible** (34 palabras).
- **Ayer:** centro `G`, letras `A E G J L N U`, pangrama **lenguaje** (31 palabras).

### Para armar un puzzle nuevo

1. Elegí 7 letras distintas (sin `s`) que tengan al menos un pangrama.
2. Sacá la lista de palabras válidas de un diccionario de español.
3. Cargá `centerLetter`, `outerLetters`, `validLetters`, `pangrams`, `answers`.

Los puzzles de esta versión se generaron con un script
(`scratchpad/gen2.js` en la sesión de Claude) cruzando dos listas abiertas:

- Validez: [`an-array-of-spanish-words`](https://github.com/words/an-array-of-spanish-words)
  (la misma que usa Letter Boxed).
- Frecuencia (para quedarse con palabras conocidas):
  [`hermitdave/FrequencyWords`](https://github.com/hermitdave/FrequencyWords)
  (`es_50k.txt`, subtítulos).

Si alguna palabra de `answers` no te gusta, borrala del array. Si querés otra,
pedímelo.

## Textos del juego

En `game-assets/v2/spelling-bee.<hash>.js` (texto legible). Buscá la frase y
reemplazala. Los rangos, por ejemplo, están en un array:

```
["Principiante", 0], ["Buen comienzo", 2], ["Vas subiendo", 5], ["Bien", 8],
["Sólido", 15], ["Muy bien", 25], ["Genial", 40], ["Increíble", 50], ["Genio", 70]
```

(el rango máximo, "Abeja Reina", aparece aparte). Si cambiás un nombre de rango,
cambialo **en todos lados** del archivo, porque el código compara ese texto.

## Detalles menores

- El botón **"Pistas de hoy"** de la barra ya no lleva a ningún lado (era una
  página de NYT). Si molesta se puede sacar del `.js`.
- Las llamadas para traer el puzzle "de verdad" desde nytimes.com fallan (a
  propósito) y el juego usa el que está embebido en `index.html`. En la consola
  quedan algunos errores de red inofensivos (`bad req`, `unable to get remote
  progress`), igual que en los otros juegos.
- El progreso se guarda en `localStorage` del navegador (clave `sb-today`).

## Cómo ejecutarlo

Necesita servidor local (carga varios archivos):

```
python3 -m http.server 8000
```

y abrir `http://localhost:8000/spelling-bee/`.
