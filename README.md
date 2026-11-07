# Extensiones de Mangayomi

Repositorio personal de extensiones para [Mangayomi](https://github.com/kodjodevf/mangayomi).

## Cómo agregarlo en Mangayomi

1. Abre **Explorar → Extensiones** (pestaña Anime).
2. Toca el icono de repositorios y agrega esta URL:

   ```
   https://raw.githubusercontent.com/race-mountain-rock/mangayomi-extensions/main/anime_index.json
   ```

3. Instala o actualiza **TioAnime** (versión 0.1.13).

## Extensiones

| Fuente   | Idioma | Versión | Notas |
|----------|--------|---------|-------|
| TioAnime | es     | 0.1.13  | Arreglada (ver abajo) |

### TioAnime 0.1.13: qué se arregló

- **`TypeError: cannot read property of null` al abrir un anime o un episodio.** TioAnime agregó
  un script de publicidad al final de cada página, y la extensión leía siempre el último
  `<script>` para sacar la lista de episodios y de videos. Ahora busca `var episodes` y
  `var videos` directamente en el HTML.
- **Error en búsquedas de una sola página.** Si una búsqueda no tenía botón de página
  siguiente, la extensión fallaba. Ahora detecta la página siguiente por el enlace
  `rel="next"` (y lo ignora cuando apunta a `#`, como en la última página).
- La lista de episodios usa los números reales que publica la página, en vez de contar desde 1.
- Las búsquedas codifican bien caracteres especiales.
- Se envía `Referer: https://tioanime.com/` en las peticiones.

## Créditos

Basado en la extensión TioAnime de
[m2k3a/mangayomi-extensions](https://github.com/m2k3a/mangayomi-extensions), bajo licencia
Apache 2.0 (ver `LICENSE`).
