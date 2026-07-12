# Cómo publicar un ensayo

Los ensayos se escriben en **Markdown** (`.md`). No hace falta instalar nada ni tocar HTML.
Toda la lista del sitio (el panel de "Ensayos" en la home y la página `ensayos.html`) se
arma sola a partir del manifiesto `ensayos/index.json`.

## Publicar uno nuevo — 2 pasos

**1) Crea el archivo del ensayo** en esta carpeta, con un nombre en minúsculas y guiones (ese
nombre es el *slug*, la parte que aparece en la URL). Por ejemplo:

```
ensayos/la-erosion-gana-siempre.md
```

Escribe el cuerpo en Markdown. **No pongas el título dentro del .md** — el título va en el
manifiesto (paso 2). Ejemplo de contenido:

```markdown
Primer párrafo, la idea central sin rodeos.

## Un subtítulo

Más texto. Puedes usar **negritas**, *cursivas*, [enlaces](https://roca.ventures),
listas y citas:

> Una cita que respira.
```

**2) Agrega una línea al manifiesto** `ensayos/index.json`. Copia un bloque y ponlo
**arriba del todo** (el orden del archivo es el orden en que se muestran, del más nuevo al
más viejo):

```json
{
  "slug": "la-erosion-gana-siempre",
  "titulo": "La erosión gana siempre",
  "fecha": "2026",
  "resumen": "Una frase que aparece bajo el título en la lista."
}
```

> El `slug` debe ser **idéntico** al nombre del archivo `.md` (sin la extensión).

Guarda, y publica con el flujo de siempre:

```bash
cd ~/roca.ventures
rm -f .git/index.lock
git add -A
git commit -m "Nuevo ensayo: la erosion gana siempre"
git push origin main
```

En ~1–2 min aparece en el sitio, con su propia URL:
`roca.ventures/articulo.html?e=la-erosion-gana-siempre`

## Editar o borrar

- **Editar:** cambia el `.md` (y el `titulo`/`resumen` en el manifiesto si hace falta), y haz push.
- **Borrar:** quita su bloque del `index.json`. Puedes dejar o eliminar el `.md`; si alguien
  entra al link directo y ya no está en el manifiesto, verá "Ensayo no encontrado".

## Formato admitido (Markdown)

Encabezados `##` y `###`, párrafos, **negrita**, *cursiva*, `código`, listas con `-` o `1.`,
enlaces `[texto](url)`, citas con `>`, líneas divisorias `---`, e imágenes
`![alt](images/archivo.png)`. El estilo (tipografías, colores) se aplica solo.

## Nota sobre previsualización local

El lector carga el `.md` con `fetch`, que en los navegadores **no funciona abriendo el archivo
con doble clic** (`file://`). Para ver el sitio en tu máquina antes de publicar, levanta un
servidor local desde la carpeta del repo:

```bash
cd ~/roca.ventures
python3 -m http.server 8080
```

y abre `http://localhost:8080`. En el sitio publicado (GitHub Pages) funciona sin nada de esto.
