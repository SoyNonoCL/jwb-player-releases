# JWB Player — descargas públicas

Este repositorio se utiliza **solo para distribuir los APK** de JWB Player. El código fuente y las claves de firma permanecen en el repositorio privado `SoyNonoCL/JWB-Player`.

## Migración de Releases desde el repositorio privado

Se preparó el workflow [Migrar APK de JWB Player](.github/workflows/migrar-releases.yml), que copia los APK publicados sin subir el código fuente.

Para ejecutar la migración una vez:

1. Genera un **fine-grained personal access token** en https://github.com/settings/personal-access-tokens/new
   - **Resource owner:** `SoyNonoCL`
   - **Repository access:** Only select repositories → `JWB-Player`
   - **Repository permissions:** Contents → **Read-only** (Metadata Read se incluye automáticamente)
   - Elige una vigencia limitada.
2. Ve a **Settings → Secrets and variables → Actions** de este repositorio:
   https://github.com/SoyNonoCL/jwb-player-releases/settings/secrets/actions
3. Crea un **New repository secret** de nombre exacto `SOURCE_READ_TOKEN` y pega el token allí. **No lo pegues en README, archivos, issues ni chats.**
4. Abre [Actions → Migrar APK de JWB Player](https://github.com/SoyNonoCL/jwb-player-releases/actions/workflows/migrar-releases.yml) y elige **Run workflow → main → Run workflow**.
5. Comprueba que finaliza con marca verde y revisa la pestaña [Releases](https://github.com/SoyNonoCL/jwb-player-releases/releases).

Si aparece un error 403 al publicar, revisa **Settings → Actions → General → Workflow permissions**, porque el workflow necesita `contents: write` sobre **este repositorio público**. El token secreto solo necesita lectura del repositorio privado.

El workflow es **repetible**: no duplica los Releases que ya tienen APK. Copia sus tags, nombres, notas y archivos APK, pero GitHub les asigna **nuevas fechas de publicación y contadores de descarga** en el repositorio público.

## Versiones detectadas en el repositorio privado

- `v1.0.4`
- `v2.0.9`
- `v2.0.10`
- `v2.0.11`
- `v2.0.12`
- `v2.0.13`

Tras la migración, la descarga estable podrá enlazarse desde JW PlayerHUB:

`https://github.com/SoyNonoCL/jwb-player-releases/releases/latest/download/JWB-Player.apk`

No se debe reemplazar el enlace de Google Drive del sitio hasta verificar que el APK es accesible sin iniciar sesión. Si solo necesitas una migración única, puedes revocar el token al terminar.
