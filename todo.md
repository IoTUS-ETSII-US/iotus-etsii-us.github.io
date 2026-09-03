# TODO — completar iotus-etsii-us.github.io

Servidor local: `hugo server -D` → http://localhost:1313/
(Con `-D` se ven también las páginas en `draft: true`; sin el flag, todo lo
marcado como draft desaparece del sitio — por eso casi todo lo de abajo es
bloqueante para producción.)

## 1. Contenido de ejemplo que hay que sustituir o quitar

Todo lo siguiente tiene `draft: true` y/o datos inventados. O se rellena con
contenido real y se quita el draft, o se borra antes de publicar.

- [ ] `content/proyectos/cerradura-nfc-local-asociacion/index.md` — proyecto
      de ejemplo (idea, sin avanzar). `personas` tiene "Nombre Apellido" sin
      rellenar.
- [ ] `content/proyectos/nodo-co2-etsi/index.md` — proyecto de ejemplo
      (completado). Dos `personas` con "Nombre Apellido" sin rellenar;
      `repositorio` apunta a `github.com/iotus-etsii/nodo-co2` (verificar si
      existe de verdad o es placeholder).
- [ ] `content/blog/nodo-co2-temperaturas-de-marte/index.md` — bitácora de
      ejemplo. Tiene un TODO interno: falta la foto real del pin resoldado
      (comentario HTML en el propio archivo).
- [ ] `content/eventos/taller-soldadura-novatos/index.md` — evento de
      ejemplo, `inscripcion_url` es `https://forms.example/...` (no es un
      formulario real).
- [ ] `content/eventos/hackathon-24-horas-un-sensor/index.md` — evento de
      ejemplo, `inscripcion_url` es `https://forms.example/...` (no es un
      formulario real).
- [ ] `content/docs/entorno-desarrollo/index.md` — guía de ejemplo, dice
      explícitamente "pendiente de que la junta confirme el flujo real de
      cada proyecto".

Para cada uno: o se convierte en contenido real y se quita `draft: true`, o
se elimina el bundle si no se va a usar como plantilla.

## 2. Páginas fijas — huecos marcados con "(Pendiente: ...)"

- [ ] `content/nosotros/_index.md`
  - Email de contacto, enlaces a redes sociales y ubicación exacta del
    local (línea 38).
  - El TODO de la línea 31: enlazar juntas directivas presentes y pasadas.
  - Revisar tono/erratas de la sección "Junta" y "Contacto" antes de
    publicar (texto muy informal, con typos: "nonos va el internet").
- [ ] `content/unete/_index.md`
  - Enlace al formulario de inscripción de socio.
  - Enlace(s) a Estatutos, Normativa de Funcionamiento Interno y Código de
    Conducta (mencionados en el paso 0 pero sin enlazar).
- [ ] `content/empresas/_index.md`
  - PDF descargable con modalidades de colaboración y contrapartidas.
  - Email de contacto para empresas.

## 3. Configuración — recursos y claves pendientes

- [ ] `config/_default/params.toml` línea 16 — `defaultSocialImage =
      "img/social-default.png"` **no existe** en `assets/img/` (solo están
      `cloudia.jpg`, `iotus-logo.svg`, `iotus-logo-mono.svg`). Falta crear
      esa imagen 1200×630 (logo IoTUS sobre fondo `primary-900`, sin
      Cloudia, según el comentario del propio archivo).
- [x] ~~`apiKey` de Google Calendar vacía~~ — comprobado: no hace falta.
      El calendario de `content/eventos/_index.md` usa el shortcode
      `{{< calendar-embed >}}`, que solo lee `calendar.id`/`calendar.timezone`
      y embebe el iframe público de Google Calendar; `apiKey` no se usa en
      ningún layout/partial del repo (el comentario de `params.toml` está
      desactualizado). Sí queda pendiente crear un widget de "evento
      actual/próximo" en la home si se quiere ese comportamiento, pero no
      depende de una API key con este enfoque de iframe.

## 4. Espaciado/diseño — hecho

- [x] **Causa raíz encontrada**: el CSS de Blowfish (`themes/blowfish/assets/css/compiled/main.css`)
      viene precompilado y commiteado por el build del propio tema, que solo
      escanea las plantillas *del tema*. Cualquier clase de Tailwind que solo
      se use en nuestros `layouts/` propios y que el tema no use en ningún
      sitio **no se compila y no hace nada**, en silencio.
- [x] Encontradas y arregladas 3 clases muertas en
      `layouts/partials/home/custom.html` (home a medida):
  - `gap-16` en el contenedor raíz — el espaciado entre TODAS las secciones
    de la home (hero, carrusel, "Qué hacemos", aviso de apertura) era 0.
  - `max-w-none` en la sección "Qué hacemos" — la rejilla de 5 columnas
    quedaba encogida a 68ch en vez de a todo el ancho (además chocaba con la
    regla `.prose { max-width: 68ch }` de `custom.css`, que por orden de
    carga siempre gana a los `.max-w-*` del tema).
  - `p-10` en el hero — llevaba también un `p-3` residual sin quitar; al
    faltar `p-10` en el CSS compilado, el padding real aplicado era el `p-3`
    (0.75rem), no el `p-10` (2.5rem) previsto.
  - Arreglo: `max-w-none` → `max-w-full` (clase que sí existe compilada);
    `.prose` en `custom.css` reescrito como `:where(.prose)` (especificidad
    0, para que no vuelva a ganarle a un `.max-w-*` del tema); `gap-16` y
    `p-10` añadidos a mano en `assets/css/custom.css` (con el mismo `calc(var(--spacing) * N)`
    que genera Tailwind, para que sigan la misma escala); quitado el `p-3` residual.
- [ ] **Pendiente de decisión**: si en el futuro se añaden más clases de
      Tailwind a `layouts/` propios que el tema no use en ningún sitio,
      hay que repetir este mismo chequeo (o definirlas a mano en
      `custom.css` igual que aquí) — Hugo no vuelve a compilar Tailwind
      sobre las plantillas de este repo, solo concatena el CSS ya hecho del
      tema más `custom.css`.

## 5. Otras revisiones sugeridas

- [ ] Repasar que los `repositorio` de los proyectos apunten a repos que
      existan de verdad (org `iotus-etsii` en GitHub).
- [ ] Cuando haya contenido real y sin drafts, correr `hugo` (sin `-D`) y
      revisar que el sitio generado en local (`hugo server`, sin `-D`) no
      quede con secciones vacías (Proyectos/Eventos/Blog dependen de que
      haya al menos una página sin draft).
- [ ] Revisar ortografía/tono en `content/nosotros/_index.md` y
      `content/_index.md` (hay erratas: "Pesidencia", "nonos", guion suelto
      tras "Préstamo de material").

---
*Generado revisando `content/`, `config/_default/` y `assets/img/` en la
rama `pruebas-mibu`. No incluye tareas de diseño/CSS ni nada dentro de
`themes/blowfish/` (submódulo, no se toca).*
