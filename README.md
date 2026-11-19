# Extensiones de Mangayomi

Repositorio personal de extensiones para [Mangayomi](https://github.com/kodjodevf/mangayomi).

## Cómo agregarlo en Mangayomi

1. Abre **Explorar → Extensiones** (pestaña Anime).
2. Toca el icono de repositorios y agrega esta URL:

   ```
   https://raw.githubusercontent.com/race-mountain-rock/mangayomi-extensions/main/anime_index.json
   ```

3. Instala las extensiones que quieras.

## Extensiones

| Fuente   | Idioma | Versión | Servidores de video        | Notas |
|----------|--------|---------|----------------------------|-------|
| TioAnime | es     | 0.1.13  | Voe, YourUpload, Okru      | Arreglada (ver abajo) |
| TVAnime  | es     | 0.1.0   | Voe, MP4Upload (Sub y Dub) | Nueva; oculta los títulos hentai del directorio |
| AnimeAV1 | es     | 0.1.0   | HLS, Voe, MP4Upload (Sub y Dub) | Nueva |

Servidores como Mega, Byse o UPNShare aparecen en los sitios pero no se pueden reproducir
desde la extensión, así que se omiten.

### TVAnime 0.1.0

- Populares (mejor valorados), recientes (agregados recientemente), búsqueda y filtros por
  tipo, género, estado y orden.
- Lista completa de episodios, aunque el sitio los muestre en páginas de 50 (One Piece: 1180).
- El directorio del sitio mezcla anime con hentai; los títulos con géneros explícitos se
  ocultan de los listados.

### AnimeAV1 0.1.0

- Populares, últimos episodios, búsqueda y filtros por tipo, género, estado y orden.
- El servidor **HLS** es el reproductor propio de AnimeAV1 (`player.zilla-networks.com`).
- El catálogo del sitio solo llega a 50 páginas (1000 títulos); para encontrar algo más
  antiguo usa la búsqueda o los filtros.

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

La extensión TioAnime y la librería de extractores (`mangayomi-js-helpers`) que usan las tres
extensiones vienen de [m2k3a/mangayomi-extensions](https://github.com/m2k3a/mangayomi-extensions),
bajo licencia Apache 2.0 (ver `LICENSE`).
