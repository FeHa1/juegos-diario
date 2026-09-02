# Juegos diario digital 

Tome la inspiracion de hacer los juegos que se ven en el NYT en español para probar. Esta basado en el trabajo de https://github.com/luni-moon/nyt-game-source-code


## Cómo ejecutarlo

**Opción rápida (Wordle):** doble clic en `wordle/index.html` y se abre en el navegador.

**Opción recomendada (servidor local):** desde esta carpeta, en una terminal:

```
python3 -m http.server 8000
```

y abrí `http://localhost:8000/wordle/` (o `/vertex/`) en el navegador.
(Wordle también funciona con doble clic; Vertex y los demás necesitan el servidor.)

Para cortar el servidor: `Ctrl + C` en la terminal.


### Estado de la traducción

| Juego | Estado | Notas |
|---|---|---|
| **Wordle** (`wordle/`) | ✅ traducido | teclado con Ñ + lista de palabras editable (`wordle/palabras.js`). Ver `wordle/TRADUCCION.md` |
| **Vertex** (`vertex/`) | ✅ traducido | interfaz + títulos de puzzles. Ver `vertex/TRADUCCION.md`. Necesita servidor local |
| Spelling Bee, Letter Boxed, Tiles, Mini Crucigrama | ⏳ pendiente | |

Todo se hace sin decir "NYT" / "New York Times": la marca es el diario ficticio
**ADN SUR**.

