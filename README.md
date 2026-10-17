# 🎵 Bingo Musical

Bingo musical para jugar en familia. La **TV** pone trocitos de canciones y lleva el marcador. Cada jugador escanea un **QR** con su móvil, escribe su nombre y recibe su **cartón**.

Es una web estática (un solo `index.html`). No necesita servidor propio, base de datos ni cuentas.

## Cómo se juega

1. Abre la web en la TV (o en un portátil conectado a la TV) y pulsa **«Esta pantalla es la TV»**.
2. En **«Preparar la partida»**, elige las canciones:
   - **Buscar canciones**: busca en el catálogo de iTunes (por ejemplo «Disney», «Frozen»…) y añade las que quieras. Suenan los avances oficiales de 30 segundos.
   - **Tus propios archivos**: MP3/M4A desde el dispositivo de la TV. Se reproducen en local y no se suben a ningún sitio.
   - **Títulos a mano**: si prefieres poner la música desde otro sitio (Spotify, cantadas…).
3. Cada jugador escanea el QR, escribe su nombre y recibe su cartón (3×3, o 4×4 con 24 canciones o más).
4. Pulsa **«Siguiente canción»**. Suena un trocito, y los jugadores marcan la canción en el móvil si la tienen.
5. Desde el móvil se canta **«¡Línea!»** (una fila completa) o **«¡Bingo!»** (cartón entero). La TV lo comprueba sola y anuncia al ganador.

El marcador de la TV muestra en directo cuántos aciertos lleva cada jugador. También avisa si alguien ha marcado canciones que todavía no han sonado.

## Cómo funciona por dentro

- La TV hace de «servidor» de la partida. Los móviles se conectan directamente a ella mediante [PeerJS](https://peerjs.com/) (WebRTC), que usa el servidor público gratuito de PeerJS solo para encontrarse.
- El QR lleva a `?sala=CÓDIGO`, y cada sala tiene un código de 5 letras.
- La TV guarda la partida en el navegador (`localStorage`). Si se recarga, recupera la sala, los jugadores y sus cartones.
- Si un móvil se desconecta (por ejemplo, se bloquea la pantalla), al volver recupera su mismo cartón.

**Requisitos:** la TV y los móviles necesitan internet. Lo ideal es estar todos en la misma wifi de casa. Algunas redes muy restrictivas (wifis de empresa, algunos datos móviles) pueden bloquear WebRTC.

## Publicarlo con GitHub Pages

1. Sube `index.html` a un repositorio público.
2. Ve a **Settings → Pages**.
3. En **Source** elige *Deploy from a branch*, rama `main` y carpeta `/ (root)`.
4. En un minuto estará en `https://TU-USUARIO.github.io/NOMBRE-DEL-REPO/`.

## Música y derechos

No subas archivos de música con derechos (por ejemplo, canciones de Disney) al repositorio: sería redistribuirlos públicamente. Usa los avances de iTunes o tus propios archivos cargados en local desde la TV.
