# DESIGN.md · Clipeya v3 · 23-nov-2026
Manda la marca de Clipeya (logo spark, naranja #FF4D1F, Big Shoulders e Instrument Sans: ya publicados en la v2). Lo que cambia es el nivel: profundidad, luz y prueba real. Una sola escuela de diseño: oscuro cálido, con el naranja usado como luz.

## Escalera de 6 tonos (variables en :root de index.html)
| Token | Código | Uso |
|---|---|---|
| --bg0 | #0E0C0B | fondo base (no es negro puro) |
| --bg1 | #161311 | tarjetas, burbujas del chat |
| --deep | #241C16 | profundidad: degradados y viñetas |
| --brand | #FF4D1F | luz: halos, partículas encendidas, botón principal. Menos del 10 % de la pantalla |
| --bone | #ECE7DE | texto y partículas del templo |
| --mut | #B7AEA2 | texto secundario |

Profundidad: degradados radiales cálidos arriba y abajo, grano fino al 6 % (SVG feTurbulence) y viñeta en la portada. Nada de fondos planos.

## Tipografía
- Titulares: Big Shoulders Bold, en mayúsculas, con clamp() (h1 de 46 a 104 px, h2 de 36 a 68 px), interlineado 0,98. Más o menos la mitad que en la v2.
- Texto: Instrument Sans 400/700, 17 px (16 px en tarjetas), interlineado 1,55, como mucho 46-50 caracteres por línea en las entradillas.
- WOFF2 propias con font-display: swap y precarga de las dos más usadas.

## Movimiento (como mucho 2 piezas estrella)
1. Templo de partículas (Three.js 0.187.0, versión exacta): en ruinas → entero según el scroll de la portada (175svh, lienzo sticky). 9.000 puntos en escritorio y 3.600 en móvil; pixelRatio de 1,5 como máximo; el render se para fuera de la vista; con reduced-motion, templo entero y quieto.
2. Gerard y Andy en píxel (16×24, a mano), con cursores que «arreglan» el templo cuando se rompe (al tocarlo, o Andy cada 6,5 s). Web Animations API, sin librería.
- Entradas: 0,8 s con cubic-bezier(.22,1,.36,1); hover de 200-250 ms; solo transform y opacity.

## Componentes
Botón principal (píldora naranja con sombra de luz) · botón fantasma (borde de 1 px) · tarjeta con clip real y rótulo «Grabación real» · persona en píxel · capa de precios (dialog) · chat (botón fijo abajo a la derecha) · interruptor Experiencia/Directa en la barra.

## Lo que se quitó respecto a la v2 (y por qué)
- Los 7 precios después del titular: Gerard y Andy dijeron que espantan; ahora solo «desde 100 €» y la tabla va en una capa.
- La pimienta de muestra y todo lo que decía «MUESTRA» o «ficticio»: Gerard dijo «no se ve nada REAL».
- El comparador antes/después: era la página inventada de la pimienta.
- Los 5 vídeos de fondo decorativos: pesaban y no enseñaban nada nuestro.
- Los titulares gigantes de relleno.

## Vuelta 3 (23-nov): tipografía nueva y templo en silueta
- **Titulares: Instrument Serif** (Google Fonts, OFL), en minúsculas y con cursiva solo en el giro del H1 («en ruinas» / «en pie»). **Texto: Instrument Sans** (la que ya había). Son 2 familias del mismo diseñador, así que casan.
  - Por qué: la v2 y la vuelta 2 usaban Big Shoulders en mayúsculas estrechas en todos los titulares, que Gerard y el PC1 ven como «la misma web». Una serif editorial grande en minúsculas es lo opuesto: se lee como estudio (el registro de cuberto, pero con serif) y da contraste con el texto en sans.
  - La skill design-taste-frontend no está instalada en el P2: la elección se justifica aquí.
- **Templo en SVG** (fuera Three.js): escalones, 6 columnas en 3 tambores + capitel, arquitrabe en 3 bloques y frontón en 2 mitades.
  - En ruinas: columnas partidas, tambores y capiteles en el suelo, el bloque central del arquitrabe torcido y el frontón caído sobre los escalones.
  - Con el scroll, cada pieza vuelve a su sitio con un arco y en orden (de abajo arriba).
  - La silueta se lee en 1 segundo, y la página pesa menos (sin la librería 3D).
- **Aire:** una idea por pantalla; cada servicio en su fila, con la grabación grande alternando de lado (4:5, como mucho 448×560). La cabecera es fija, de 72 px (64 en móvil), y todas las secciones llevan scroll-margin-top.
