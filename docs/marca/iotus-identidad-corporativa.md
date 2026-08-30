# IoTUS · Manual de identidad

Asociación estudiantil de Internet of Things de la Universidad de Sevilla.
Versión 1.0 · documento base para diseño gráfico y para el sitio web (Hugo + Blowfish).

---

## 1. Idea de marca

**IoT + US.** El nombre ya contiene la tesis: las *cosas* conectadas y *nosotros*, las personas que las conectamos. En inglés "us" es literalmente "nosotros"; en Sevilla es la Universidad. Esa doble lectura es el eje de toda la comunicación: **IoTUS no habla de dispositivos, habla de gente que hace cosas con dispositivos.**

- **Descriptor oficial:** Asociación de Internet of Things · Universidad de Sevilla
- **Lema propuesto:** *Conectamos cosas. Y a quien las hace.*
- **Alternativas:** *Del sensor al proyecto.* / *Aquí se conecta todo.*

### Personalidad

Base sobria, guiño gamberro. La regla operativa:

> La estructura es de ingeniería. El detalle es de club de estudiantes.

Traducido: tipografía y retícula disciplinadas, color contenido, y luego un punto de humor concreto y localizado (la mascota, un micro-texto, un dato de sensor). Nunca las dos cosas a la vez en el mismo elemento.

| Somos | No somos |
|---|---|
| Concretos: proyectos, placas, código | Abstractos: "soluciones de transformación digital" |
| Cercanos: tuteamos, explicamos | Institucionales: "la presente asociación" |
| Curiosos: enseñamos lo que falla | Vendedores: solo enseñamos lo que luce |

### Voz

Tuteo, frases cortas, verbos activos. Sin jerga corporativa (`sinergia`, `ecosistema`, `soluciones`). Los acrónimos técnicos se explican la primera vez: "LoRaWAN (radio de largo alcance y bajo consumo)". Bilingüe ES por defecto, EN para documentación técnica y contenido dirigido a empresas.

---

## 2. Logotipo

### Sistema

| Versión | Uso |
|---|---|
| **Principal** — nube azul + `IoTUS` amarillo + globo como "O" | Web, cartelería, presentaciones |
| **Compacto** — solo el globo dentro de la nube, sin texto | Avatar de redes, favicon, pin de solapa |
| **Monocromo** — todo en `neutral-950` o todo en blanco | Sellos, serigrafía a un color, fondos fotográficos |
| **Mascota** — la nube personaje | Nunca sustituye al logo. Ver 2.3 |

### Reglas

- **Aire mínimo:** la altura de la "I" del wordmark por los cuatro lados.
- **Tamaño mínimo:** 32 px de alto en pantalla para la versión principal; por debajo, versión compacta.
- **Fondos:** sobre blanco o `neutral-50`; sobre `neutral-950` se usa la versión con wordmark en `secondary-500`.
- **El globo es intocable.** Es el único elemento que se hereda como recurso gráfico (ver 5.1). No se sustituye por un icono de wifi, un chip ni un candado.

#### No hacer

- Cambiar el amarillo del wordmark por otro color de la paleta.
- Poner el logo sobre fotografía sin caja de color detrás.
- Añadir sombra, degradado, contorno o brillo.
- Estirar, rotar o reencuadrar la nube.
- Usar la mascota y el logo juntos en el mismo bloque visual.

### 2.3 La mascota

Nombre: **Cloudia**.

Cloudia es el guiño, y funciona porque aparece poco. Su rol:

- **Sí:** stickers y merch, página 404, mensajes de estado vacío, cabecera de posts informales, RRSS internas, camisetas de bienvenida.
- **No:** cabecera del sitio, documentos institucionales, dossier de patrocinio, correo formal a empresas, tarjetas de contacto.

Los neones de Cloudia (`#7C0DD8`, `#FF8EBA`, `#F2FE8E`) viven **solo dentro de la ilustración**. No son colores de interfaz, ni de enlaces, ni de botones, ni de fondos de sección.

---

## 3. Color

Toda la escala nace del azul del logo. `#77CAFF` tiene 1,8:1 de contraste sobre blanco: sirve como color de marca, no como color de texto. Al construir la rampa completa, el azul reconocible se queda en `primary-300` y los tonos oscuros hacen el trabajo funcional.

### Escala primaria — Azul IoTUS

| Token | Hex | RGB | Uso |
|---|---|---|---|
| `primary-50` | `#EEF7FE` | 238 247 254 | Fondos de sección |
| `primary-100` | `#DAEEFD` | 218 238 253 | Fondos de aviso |
| `primary-200` | `#B7DFFD` | 183 223 253 | Bordes suaves, tags |
| `primary-300` | `#82C9FF` | 130 201 255 | **Azul de marca (logo)**, acentos en oscuro |
| `primary-400` | `#4AB1FF` | 74 177 255 | Enlaces en modo oscuro |
| `primary-500` | `#1A9AFC` | 26 154 252 | Iconografía, gráficos |
| `primary-600` | `#0C82DC` | 12 130 220 | Hover de botón |
| `primary-700` | `#0E68AC` | 14 104 172 | **Enlaces y botones** (5,8:1 sobre blanco) |
| `primary-800` | `#0F5083` | 15 80 131 | Titulares en azul |
| `primary-900` | `#0E3C60` | 14 60 96 | Fondos oscuros de marca |
| `primary-950` | `#0A263B` | 10 38 59 | Fondo hero oscuro |

### Escala secundaria — Amarillo IoTUS

| Token | Hex | RGB | Uso |
|---|---|---|---|
| `secondary-100` | `#FEFADA` | 254 250 218 | Fondo de resaltado |
| `secondary-300` | `#FFF382` | 255 243 130 | Subrayado, marcador |
| `secondary-500` | `#FFE817` | 255 232 23 | Acento sobre fondo oscuro |
| `secondary-600` | `#EED600` | 238 214 0 | **Amarillo del logo** |
| `secondary-700` | `#B3A207` | 179 162 7 | Texto amarillo sobre blanco (mínimo viable) |
| `secondary-900` | `#655C08` | 101 92 8 | Texto sobre fondos amarillos |

*(Escala completa para Blowfish en la sección 7.)*

**Regla del amarillo:** el amarillo llama la atención, no comunica. Se usa en **un solo elemento por pantalla**: el CTA principal, o el subrayado del titular, o el badge de "Abierto a inscripciones" — nunca los tres. Sobre blanco, el amarillo es fondo con texto `neutral-950` encima, jamás texto amarillo suelto.

### Escala neutra — Gris niebla

Gris con temperatura azul (H 210°) para que conviva con el primario sin ensuciarlo.

| Token | Hex | Uso |
|---|---|---|
| `neutral-50` | `#F3F6F9` | Fondo de página |
| `neutral-200` | `#D3DAE1` | Separadores |
| `neutral-400` | `#99A4B0` | Texto deshabilitado |
| `neutral-600` | `#657483` | Metadatos, pies de foto |
| `neutral-700` | `#4E5D6C` | Texto secundario (6,8:1) |
| `neutral-900` | `#293745` | **Texto principal** (12,2:1) |
| `neutral-950` | `#17222E` | Fondo del modo oscuro |

### Proporción

70 % neutro · 20 % azul · 8 % blanco de aire · **2 % amarillo**. Si el amarillo se nota como "color de fondo" en vez de como acento, hay demasiado.

### Accesibilidad

- Texto normal: mínimo 4,5:1. Texto grande (≥24 px o ≥19 px bold): 3:1.
- Enlaces: `primary-700` sobre claro, `primary-400` sobre oscuro. Siempre subrayados en cuerpo de texto, no solo por color.
- Nada de texto sobre `primary-300` ni sobre ningún amarillo por debajo de `700`.

---

## 4. Tipografía

Pareja deliberada: **Space Grotesk** para titulares (geométrica, con rarezas en la `a`, la `g` y la `t` que le dan carácter técnico sin caer en la fuente "de startup") y **IBM Plex Sans** para texto (humanista, diseñada por IBM para documentación de ingeniería, acentos españoles impecables). **IBM Plex Mono** cierra el sistema para datos y metadatos, y es donde vive buena parte de la personalidad.

Las tres son open source y están en Google Fonts.

| Rol | Familia | Pesos | Uso |
|---|---|---|---|
| Display | Space Grotesk | 500, 700 | H1–H3, cifras grandes, wordmarks de sección |
| Texto | IBM Plex Sans | 400, 500, 600 | Cuerpo, H4–H6, navegación, botones |
| Utilidad | IBM Plex Mono | 400, 500 | Fechas, tags, código, etiquetas superiores, datos de sensor |

**Fallback:** `system-ui, -apple-system, "Segoe UI", sans-serif`.

### Escala (base 16 px, ratio 1,25)

| Nivel | Tamaño | Interlineado | Tracking | Familia |
|---|---|---|---|---|
| H1 | 48 / 40 px móvil | 1,05 | −0,02em | Space Grotesk 700 |
| H2 | 33 px | 1,15 | −0,015em | Space Grotesk 700 |
| H3 | 26 px | 1,25 | −0,01em | Space Grotesk 500 |
| H4 | 21 px | 1,35 | 0 | IBM Plex Sans 600 |
| Cuerpo | 17 px | 1,65 | 0 | IBM Plex Sans 400 |
| Cuerpo pequeño | 15 px | 1,6 | 0 | IBM Plex Sans 400 |
| Etiqueta | 13 px | 1,4 | +0,08em, mayúsculas | IBM Plex Mono 500 |
| Código | 15 px | 1,6 | 0 | IBM Plex Mono 400 |

### Reglas

- Los titulares llevan tracking negativo. Es lo que hace que Space Grotesk se vea intencionada y no por defecto.
- Ancho de línea máximo: 68 caracteres en cuerpo de texto.
- Nunca mayúsculas en titulares. Las mayúsculas son exclusivas de las etiquetas mono de 13 px — ese contraste de escala es parte de la identidad.
- Números de datos siempre en mono con `font-variant-numeric: tabular-nums`.

---

## 5. Estética

### 5.1 Elemento firma: la retícula del globo

El globo del logo (meridianos y paralelos) es el recurso gráfico que se hereda a todo lo demás:

- **Fondo de hero:** la retícula esférica a `primary-100`, muy grande, saliéndose por una esquina, con la sección encima.
- **Separador de secciones:** una fila de meridianos, 1 px, `neutral-200`.
- **Viñetas de lista:** un pequeño globo en vez de un punto.
- **Estado de carga:** el globo girando sobre su eje vertical.
- **Patrón de merch:** la retícula repetida a baja opacidad en el reverso de camisetas y en la portada del dossier.

Nunca se rellena. Siempre es línea.

### 5.2 Etiquetas de telemetría

Los metadatos se maquetan como una lectura de sensor: mono, mayúsculas, separados por `·`, en `neutral-600`.

```
PROYECTO · LORAWAN · ETSI · 12 NODOS
TALLER · 14 MAR · AULA G1.32 · 24 PLAZAS
```

Es la personalidad "sobria pero con guiño": no es un chiste, pero suena a que lo escribe alguien que monta sensores. Aparece en tarjetas de proyecto, cabeceras de post y pies de imagen. Es el recurso que hace reconocible una página de IoTUS aunque le quites el logo.

### 5.3 Formas y sistema

- **Radios:** 8 px en tarjetas y botones, 4 px en tags, 999 px solo en el badge de estado. La nube del logo es la única curva orgánica del sistema.
- **Bordes:** 1 px `neutral-200`. Sin sombras salvo en menús flotantes.
- **Retícula:** 12 columnas, gutter 24 px, ancho máximo de contenido 1120 px, medida de lectura 720 px.
- **Espaciado:** múltiplos de 8 px (8/16/24/40/64/96).
- **Iconos:** Tabler o Lucide, contorno 1,5 px, en `neutral-700` o `primary-700`. No mezclar sets.
- **Fotografía:** manos, placas, cables, protoboards, gente montando cosas. Fotos reales de la asociación por encima de stock siempre. Sin filtros de color.
- **Ilustración:** solo Cloudia y solo en los contextos de 2.3.
- **Movimiento:** entradas de 200 ms con `ease-out`, desplazamiento máximo de 8 px. Un único momento animado por página (el globo del hero). Respetar `prefers-reduced-motion`.

---

## 6. Aplicaciones

### Web (prioridad: captación de estudiantes + comunidad interna)

Arquitectura mínima:

```
/                    Hero + qué hacemos + próximos eventos + proyectos destacados
/proyectos/          Fichas con etiqueta de telemetría, stack y personas
/eventos/            Talleres, charlas, hackathons. Pasados y futuros
/blog/               Bitácoras técnicas de los proyectos
/unete/              CTA principal del sitio. Cómo entrar, qué se necesita, cuándo
/nosotros/           Junta, historia, contacto
/empresas/           Dossier de patrocinio, colaboraciones, descarga en PDF
/docs/               Guías internas, plantillas, cómo montar el entorno
```

El hero no es un lema abstracto: es **lo último que ha hecho la asociación**, con su etiqueta de telemetría. La captación funciona enseñando trabajo, no prometiendo comunidad.

### Redes

- Avatar: logo compacto sobre `primary-900`.
- Plantilla de post: `neutral-50` de fondo, etiqueta mono arriba, titular en Space Grotesk, retícula del globo detrás al 8 %.
- Cloudia protagoniza las historias y los avisos informales, no los anuncios oficiales.

### Presentaciones

Portada `primary-950` con wordmark en `secondary-600`. Interiores en blanco. Un dato grande por diapositiva, en Space Grotesk 700, con su etiqueta mono debajo.

### Merch

Camiseta negra con el globo en línea a un color y la etiqueta mono en la manga. Stickers: Cloudia. Es exactamente el reparto de roles del punto 2.3.

---

## 7. Implementación en Hugo + Blowfish

### 7.1 Esquema de color

Blowfish define tres paletas — `neutral`, `primary` y `secondary` — de diez tonos cada una, y por cómo Tailwind calcula la opacidad los valores se declaran como componentes RGB separados, no como hex.

Crear `assets/css/schemes/iotus.css`:

```css
:root {
  --color-neutral: 243 246 249;
  --color-neutral-50: 243 246 249;
  --color-neutral-100: 231 236 240;
  --color-neutral-200: 211 218 225;
  --color-neutral-300: 183 193 203;
  --color-neutral-400: 153 164 176;
  --color-neutral-500: 125 139 153;
  --color-neutral-600: 101 116 131;
  --color-neutral-700: 78 93 108;
  --color-neutral-800: 58 73 87;
  --color-neutral-900: 41 55 69;
  --color-neutral-950: 23 34 46;

  --color-primary-50: 238 247 254;
  --color-primary-100: 218 238 253;
  --color-primary-200: 183 223 253;
  --color-primary-300: 130 201 255;
  --color-primary-400: 74 177 255;
  --color-primary-500: 26 154 252;
  --color-primary-600: 12 130 220;
  --color-primary-700: 14 104 172;
  --color-primary-800: 15 80 131;
  --color-primary-900: 14 60 96;
  --color-primary-950: 10 38 59;

  --color-secondary-50: 254 253 238;
  --color-secondary-100: 254 250 218;
  --color-secondary-200: 255 248 181;
  --color-secondary-300: 255 243 130;
  --color-secondary-400: 255 237 74;
  --color-secondary-500: 255 232 23;
  --color-secondary-600: 226 204 6;
  --color-secondary-700: 179 162 7;
  --color-secondary-800: 137 124 9;
  --color-secondary-900: 101 92 8;
  --color-secondary-950: 62 56 7;
}
```

Y en `config/_default/params.toml`: `colorScheme = "iotus"`.

Alternativa: el autor del tema publica **Fugu**, que genera las tres rampas a partir de tres hex (`node index.js generate 293745 0E68AC EED600`). Útil para comparar, pero las rampas de arriba ya están calibradas para contraste.

### 7.2 Tipografía

En `layouts/partials/extend-head.html`:

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@500;700&family=IBM+Plex+Sans:wght@400;500;600&family=IBM+Plex+Mono:wght@400;500&display=swap" rel="stylesheet">
```

En `assets/css/custom.css`:

```css
:root {
  --font-display: "Space Grotesk", system-ui, sans-serif;
  --font-body: "IBM Plex Sans", system-ui, sans-serif;
  --font-mono: "IBM Plex Mono", ui-monospace, monospace;
}
body { font-family: var(--font-body); font-size: 17px; line-height: 1.65; }
h1, h2, h3 { font-family: var(--font-display); letter-spacing: -0.015em; }
h1 { letter-spacing: -0.02em; }
code, kbd, pre { font-family: var(--font-mono); }

.telemetria {
  font-family: var(--font-mono);
  font-size: 13px;
  font-weight: 500;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  color: rgb(var(--color-neutral-600));
}
```

Si el proyecto se despliega sin conexión a Google Fonts (o por privacidad), autoalojar las fuentes en `static/fonts/` con `@font-face` y `font-display: swap`.

### 7.3 Notas de tema

- No tocar nunca `themes/blowfish/`. Todo va en las carpetas del proyecto: Hugo da precedencia a los archivos propios sobre los del tema, y así el tema se puede actualizar sin perder el trabajo.
- Blowfish trae shortcodes de galería, timeline, tarjetas de GitHub y CTA que encajan con la arquitectura de la sección 6.
- Modo oscuro: fondo `neutral-950`, texto `neutral-100`, enlaces `primary-400`, amarillo `secondary-500` — es donde mejor funciona el amarillo, aprovéchalo en la home oscura.
- Favicon: versión compacta del logo, 32 y 180 px, más `site.webmanifest` con `theme-color: #0E3C60`.

---

## 8. Encargo para Claude Code (modo plan)

Pegar como contexto junto a este documento:

> Sitio web de IoTUS, asociación de Internet of Things de la Universidad de Sevilla. Hugo + tema Blowfish instalado como submódulo git. Objetivo principal: captar estudiantes nuevos y servir a la comunidad interna; secundario, visibilidad ante ETSI y empresas. Bilingüe ES/EN con ES por defecto.
>
> Aplicar la identidad del manual adjunto: esquema de color `iotus`, tipografías Space Grotesk / IBM Plex Sans / IBM Plex Mono, retícula del globo como recurso gráfico, etiquetas de telemetría en mono para todos los metadatos. La mascota (Cloudia) solo en 404 y estados vacíos.
>
> Antes de escribir código: propón la estructura de `content/`, el archetype de proyecto y de evento con sus campos de front matter, y qué partials de Blowfish hay que sobreescribir. Nada de editar `themes/blowfish/`.

---

## 9. Pendiente de decidir

1. ~~Nombre de la mascota~~ → Cloudia.
2. Versiones vectoriales del logo (SVG) en principal, compacta y monocroma — ahora mismo solo existe el PNG.
3. Si el descriptor lleva "ETSI" o solo "Universidad de Sevilla".
4. Compatibilidad con la normativa de imagen institucional de la US para asociaciones (suele exigir un tratamiento concreto del escudo en materiales oficiales; conviene confirmarlo con el Vicerrectorado de Estudiantes antes de imprimir nada).
