# Cómo jugar a Letter Boxed

> El juego ya trae esta explicación adentro: tocá **Ayuda** (arriba a la derecha)
> y se abre "Cómo jugar" con un cuadrado de ejemplo que se dibuja solo.
> Esto es lo mismo pero en texto, con el puzzle de hoy.

## La idea

Hay un cuadrado con **12 letras**: 3 en cada lado. Tenés que **formar palabras**
usándolas, y encadenarlas hasta usar **todas** las letras.

```
        E   A   F
      ┌───────────┐
   S  │           │  I
      │           │
   C  │           │  M
      │           │
   V  │           │  N
      └───────────┘
        O   T   U
```

## Las reglas

1. **Cada palabra: 3 letras o más.**
2. **Dos letras seguidas no pueden ser del mismo lado.**
   Por ejemplo, no podés ir de `E` a `A` a `F` (los tres están arriba).
   Pero sí `E → I → O` (arriba, derecha, abajo).
3. **Las letras se pueden repetir** dentro de una palabra (mientras no sean
   dos seguidas del mismo lado).
4. **La última letra de una palabra es la primera de la siguiente.**
   Si tu primera palabra termina en `S`, la segunda tiene que empezar con `S`.
5. **Ganás cuando usaste las 12 letras.**
6. No valen nombres propios ni palabras con guion.

## Cómo se juega en la práctica

- Hacé clic (o tocá) las letras en orden para armar una palabra. Se va dibujando
  una línea entre ellas.
- **Enter** confirma la palabra. **Borrar** saca la última letra.
- Cuanto en menos palabras lo resuelvas, mejor. El objetivo de hoy es **3**.

## Ejemplo con el puzzle de hoy

Lados: **arriba E A F**, **derecha I M N**, **abajo O T U**, **izquierda S C V**.

Una solución en 2 palabras:

| Palabra | Recorrido | Por qué vale |
|---|---|---|
| **VAMOS** | V(izq) → A(arr) → M(der) → O(ab) → S(izq) | ninguna letra seguida comparte lado |
| **SUFICIENTE** | S(izq) → U(ab) → F(arr) → I(der) → C(izq) → I(der) → E(arr) → N(der) → T(ab) → E(arr) | empieza con **S** (la última de VAMOS); la `I` y la `E` se repiten pero nunca seguidas del mismo lado |

Entre las dos palabras se usan las 12 letras (V A M O S U F I C E N T) → **resuelto**.

No es la única solución: cualquier combinación de palabras del diccionario que
cumpla las reglas y cubra las 12 letras sirve.

## Si querés cambiar el puzzle o las palabras

Está todo en `index.html` → `window.gameData`. Ver `letter-boxed/TRADUCCION.md`.
