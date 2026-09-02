# Juegos diario digital 

Tome la inspiracion de hacer los juegos que se ven en el NYT en español para probar. Esta basado en el trabajo de https://github.com/luni-moon/nyt-game-source-code


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


### Wordle en español

El juego de la carpeta `wordle/` está traducido al español, con teclado con **Ñ**
y una lista de palabras editable a mano.

