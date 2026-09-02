# iotus-etsii-us.github.io

Sitio web de **IoTUS**, la asociación de estudiantes de IoT de la ETSI (Universidad de
Sevilla). Generado con [Hugo](https://gohugo.io/) usando el tema
[Blowfish](https://blowfish.page/) como submódulo, y desplegado automáticamente en GitHub
Pages al hacer push a `main`.

- **URL de producción**: https://iotus-etsii-us.github.io/
- **Tema**: `themes/blowfish` (submódulo git — no lo edites directamente, ver más abajo)
- **Idioma**: español (`es`), único idioma configurado

## Índice

- [Estructura del repositorio](#estructura-del-repositorio)
- [Poner el sitio en marcha en local](#poner-el-sitio-en-marcha-en-local)
- [Añadir contenido](#añadir-contenido)
  - [Un proyecto nuevo](#un-proyecto-nuevo)
  - [Un evento nuevo](#un-evento-nuevo)
  - [Una entrada de blog](#una-entrada-de-blog)
  - [Una guía en Docs](#una-guía-en-docs)
- [Modificar páginas fijas](#modificar-páginas-fijas-nosotros-únete-empresas-inicio)
- [Modificar el menú de navegación](#modificar-el-menú-de-navegación)
- [Configuración general del sitio](#configuración-general-del-sitio)
- [Shortcodes disponibles](#shortcodes-disponibles)
- [Despliegue](#despliegue)
- [Convenciones](#convenciones)

## Estructura del repositorio

```
.
├── archetypes/              # Plantillas de front matter para `hugo new`
│   ├── evento.md             # Plantilla para content/eventos/<slug>/index.md
│   └── proyecto.md           # Plantilla para content/proyectos/<slug>/index.md
│
├── assets/
│   ├── css/
│   │   ├── custom.css         # CSS propio, se añade encima del tema
│   │   └── schemes/iotus.css  # Paleta de color personalizada ("colorScheme = iotus")
│   └── img/                   # Logos e imágenes usadas por el layout (no las de contenido)
│
├── config/_default/
│   ├── hugo.toml              # Configuración raíz: baseURL, secciones, paginación...
│   ├── languages.es.toml      # Metadatos del idioma español (título, logo, descripción)
│   ├── menus.es.toml          # Entradas del menú principal y del footer
│   └── params.toml            # Overrides de los parámetros por defecto del tema Blowfish
│
├── content/                   # TODO el contenido editorial del sitio (ver detalle abajo)
│
├── docs/
│   └── marca/                 # Documentación interna de identidad corporativa (no se publica)
│
├── i18n/es.yaml                # Traducciones de cadenas de la interfaz
│
├── layouts/                   # Overrides de plantillas del tema (solo lo que se personaliza)
│   ├── 404.html
│   ├── eventos/single.html
│   ├── proyectos/single.html
│   ├── partials/               # home/custom.html, telemetry-label.html, etc.
│   └── shortcodes/              # calendar-embed, telemetry-label
│
├── static/fonts/               # Tipografías servidas tal cual
│
├── themes/blowfish/            # Submódulo git del tema — no editar aquí
│
└── .github/workflows/hugo.yml  # Build + deploy a GitHub Pages en cada push a main
```

### `content/` en detalle

Cada carpeta de `content/` es una **sección**. El fichero `_index.md` de una carpeta
controla la página de listado de esa sección; cada subcarpeta con su propio `index.md` es
una página individual (page bundle, puede llevar imágenes junto al `.md`).

```
content/
├── _index.md                          # Portada (/) — usa el shortcode feature-grid
├── nosotros/_index.md                 # Página "Nosotros" (junta, contacto...)
├── unete/_index.md                    # Página "Únete"
├── empresas/_index.md                 # Página "Empresas" (patrocinio)
│
├── proyectos/                         # Sección listada (mainSection)
│   ├── _index.md                      # Listado de proyectos
│   ├── colmena-conectada/index.md
│   ├── cerradura-nfc-local-asociacion/index.md
│   └── nodo-co2-etsi/index.md
│
├── eventos/                           # Sección listada (mainSection)
│   ├── _index.md                      # Listado + calendario embebido
│   ├── taller-soldadura-novatos/index.md
│   └── hackathon-24-horas-un-sensor/index.md
│
├── blog/                              # Sección listada (mainSection)
│   ├── _index.md
│   └── nodo-co2-temperaturas-de-marte/index.md
│
└── docs/                              # Guías internas para socios
    ├── _index.md
    └── entorno-desarrollo/index.md
```

`proyectos`, `eventos` y `blog` son las **secciones principales** (`mainSections` en
`hugo.toml`): sus páginas usan tarjeta con resumen (`cardView`) y alimentan el listado.
`nosotros`, `unete`, `empresas` y `docs` son páginas/secciones sueltas, sin listado tipo
tarjetas.

## Poner el sitio en marcha en local

Requiere [Hugo Extended](https://gohugo.io/installation/) (la versión usada en producción
está fijada en `.github/workflows/hugo.yml`, variable `HUGO_VERSION`).

```bash
# Clona con el submódulo del tema incluido
git clone --recurse-submodules https://github.com/IoTUS-ETSII-US/iotus-etsii-us.github.io.git
cd iotus-etsii-us.github.io

# Si ya lo tenías clonado sin submódulos:
git submodule update --init --recursive

# Servidor local con recarga en caliente (incluye borradores)
hugo server -D
```

Abre `http://localhost:1313/`. La opción `-D` (`buildDrafts`) es necesaria porque casi
todo el contenido de ejemplo tiene `draft: true` — quítala para ver exactamente lo que
saldría en producción.

## Añadir contenido

Todo el contenido nuevo se crea con `hugo new`, que aplica la plantilla de
`archetypes/` correspondiente y rellena la fecha automáticamente.

### Un proyecto nuevo

```bash
hugo new proyectos/nombre-del-proyecto/index.md
```

Edita el front matter según `archetypes/proyecto.md`:

| Campo | Para qué sirve |
|---|---|
| `title`, `date`, `summary` | Título, fecha y resumen que aparece en la tarjeta del listado |
| `estado` | `idea` \| `en-curso` \| `completado` — ciclo de vida del proyecto |
| `categoria` | Tecnología/dominio principal (p.ej. `"LoRaWAN"`) — sale en la etiqueta de telemetría |
| `ubicacion` | Contexto/lugar del proyecto (p.ej. `"ETSI"`) |
| `metrica_valor` / `metrica_unidad` | Número destacado en la etiqueta, p.ej. `12` nodos |
| `stack` | Lista de hardware+software usado, se muestra en el cuerpo |
| `personas` | Lista de `{nombre, rol}` de quienes participaron |
| `repositorio` | URL del repo de GitHub/GitLab (opcional) |
| `destacado` | `true` para que aparezca en "proyectos destacados" de la home |

La etiqueta de telemetría que se ve en la tarjeta se compone como
`"PROYECTO · <categoria> · <ubicacion> · <metrica_valor> <metrica_unidad>"`.

Recuerda quitar `draft: true` cuando el proyecto esté listo para publicarse.

### Un evento nuevo

```bash
hugo new eventos/nombre-del-evento/index.md
```

Campos relevantes de `archetypes/evento.md`:

| Campo | Para qué sirve |
|---|---|
| `date` | Fecha y hora del evento — de aquí se deriva si aparece como pasado o futuro |
| `lugar` | p.ej. `"Aula 1.3, ETSI"` |
| `tipo` | `"Taller"`, `"Charla"`, `"Hackathon"`... — segmento de la etiqueta de telemetría |
| `plazas` | `0` = sin límite/no especificado |
| `inscripcion_url` | Enlace al formulario de inscripción |
| `inscripcion_estado` | `abierta` \| `cerrada` \| `agotado` \| `no-requiere` |
| `modalidad` | `presencial` \| `online` \| `hibrido` |

`buildFuture = true` está activado en `hugo.toml` precisamente para que los eventos con
fecha futura se publiquen (se anuncian antes de que ocurran) en vez de quedar excluidos
del build.

### Una entrada de blog

```bash
hugo new blog/titulo-de-la-entrada/index.md
```

No tiene archetype propio: usa el front matter mínimo (`title`, `date`, `summary`,
`showAuthor: false`, heredado por `cascade` desde `blog/_index.md`). El shortcode
`{{< telemetry-label >}}` se usa dentro del cuerpo para etiquetar bitácoras relacionadas
con un proyecto concreto (ver [Shortcodes](#shortcodes-disponibles)).

### Una guía en Docs

```bash
hugo new docs/titulo-de-la-guia/index.md
```

Sección pensada para guías internas de socios (entorno de desarrollo, plantillas...).
Hereda `showDate: false`, `showAuthor: false` y `showTableOfContents: true` por
`cascade` desde `docs/_index.md`.

## Modificar páginas fijas (Nosotros, Únete, Empresas, Inicio)

Estas páginas no usan archetype: son un único `_index.md` que se edita directamente en
Markdown normal.

- [`content/nosotros/_index.md`](content/nosotros/_index.md) — qué hace la asociación, junta directiva, contacto.
- [`content/unete/_index.md`](content/unete/_index.md) — requisitos y proceso para hacerse socio.
- [`content/empresas/_index.md`](content/empresas/_index.md) — propuesta de colaboración para empresas.
- [`content/_index.md`](content/_index.md) — portada, usa el shortcode `feature-grid` para las tarjetas de "qué hacemos".

Los bloques `*(Pendiente: ...)*` marcan contenido a la espera de que la junta confirme
datos (enlaces, emails, fotos...) — sustitúyelos cuando exista la información real, no
hace falta avisar de que se ha "quitado un pendiente".

## Modificar el menú de navegación

El menú principal (header) y el del footer se definen en
[`config/_default/menus.es.toml`](config/_default/menus.es.toml). Cada entrada es un
bloque `[[main]]` o `[[footer]]` con:

```toml
[[main]]
  name = "Texto visible"
  pageRef = "seccion-o-ruta"   # referencia a una sección/página de content/
  weight = 35                   # orden dentro del menú (menor = más a la izquierda/arriba)
```

Para añadir una página al menú, crea la entrada con el `pageRef` apuntando a la ruta de
`content/` correspondiente y un `weight` entre los existentes para colocarla donde toque.

## Configuración general del sitio

| Fichero | Qué controla |
|---|---|
| [`config/_default/hugo.toml`](config/_default/hugo.toml) | `baseURL` (solo local, el workflow la sobreescribe), secciones principales, paginación, drafts/future, sitemap |
| [`config/_default/languages.es.toml`](config/_default/languages.es.toml) | Título del sitio, logo, descripción, formato de fecha |
| [`config/_default/params.toml`](config/_default/params.toml) | Overrides del tema Blowfish: esquema de color, buscador, calendario de eventos, layout del header/homepage, etc. Solo lista lo que difiere de los valores por defecto del tema (`themes/blowfish/config/_default/params.toml`) |
| [`i18n/es.yaml`](i18n/es.yaml) | Traducciones de textos fijos de la interfaz (botones, etiquetas...) |
| [`assets/css/custom.css`](assets/css/custom.css) y [`assets/css/schemes/iotus.css`](assets/css/schemes/iotus.css) | Estilos propios encima del tema, y la paleta de color `iotus` referenciada como `colorScheme` en `params.toml` |

**No edites nada dentro de `themes/blowfish/`**: es un submódulo git que apunta al
repositorio oficial del tema. Cualquier personalización va en `layouts/`, `assets/`,
`i18n/` o `config/` de este repo, que Hugo superpone automáticamente sobre el tema.

## Shortcodes disponibles

Definidos en [`layouts/shortcodes/`](layouts/shortcodes/):

- `{{< calendar-embed >}}` — inserta el widget de Google Calendar del local/aula. Usa
  `params.calendar.id` y `params.calendar.apiKey` de `params.toml`.
- `{{< telemetry-label "Segmento1" "Segmento2" ... >}}` — genera la etiqueta tipo
  "PROYECTO · LoRaWAN · ETSI · 12 nodos" que se ve en tarjetas y bitácoras.

El tema Blowfish aporta además `feature-grid`/`feature` (usado en la portada) y `lead`
(párrafo destacado al inicio de una página) entre otros — ver la documentación del tema
en [`themes/blowfish/README.es.md`](themes/blowfish/README.es.md) para el listado completo.

## Despliegue

El despliegue es automático: cualquier push a `main` dispara
[`.github/workflows/hugo.yml`](.github/workflows/hugo.yml), que compila el sitio con Hugo
(`--gc --minify`) y lo publica en GitHub Pages. No hace falta ningún paso manual — no se
sube nunca la carpeta `public/` a mano.

## Convenciones

- Commits en español, mensaje corto y en imperativo ("añade sensor de humedad", no
  "añadido").
- Ramas por feature, PR antes de tocar `main`.
- Nunca subir credenciales (claves de API, tokens MQTT...) al repositorio — usar
  variables de entorno o, en el caso de `params.toml`, dejarlas vacías con un comentario
  `TODO` hasta que se gestionen como secreto.
