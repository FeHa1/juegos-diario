![Hits](https://hits.link/hits?url=https%3A%2F%2Fgithub.com%2FLukas-Batema%2Fnyt-game-source-code)

# Wordle en español

El juego de la carpeta `wordle/` está traducido al español, con teclado con **Ñ**
y una lista de palabras editable a mano.

## Cómo ejecutarlo

**Opción rápida (Wordle):** doble clic en `wordle/index.html` y se abre en el navegador.

**Opción recomendada (servidor local):** desde esta carpeta, en una terminal:

```
python3 -m http.server 8000
```

y abrí `http://localhost:8000/wordle/` en el navegador.
(Los otros juegos van a necesitar este servidor cuando se traduzcan; por eso conviene
acostumbrarse a esta forma.)

Para cortar el servidor: `Ctrl + C` en la terminal.

## Dónde editar las palabras

Todas las palabras están en **`wordle/palabras.js`**, un archivo de texto con
instrucciones adentro. Hay dos listas:

- `WORDLE_ES_SOLUCIONES`: las respuestas de cada día, **en orden**. La primera de
  la lista es la palabra de hoy, la segunda la de mañana, etc.
- `WORDLE_ES_ACEPTADAS`: palabras que el juego acepta como intento válido pero que
  nunca son la respuesta.

Reglas: 5 letras exactas, solo `a-z` y `ñ`, sin tildes (`cafe`, no `café`).
Después de editar, guardá y recargá la página.

Si querés cambiar textos del juego (mensajes, botones), están en
`wordle/main.b84b7aa7.js`. Ver `wordle/TRADUCCION.md`.

---


