# Imágenes de Mis_app_ha

Control común mantenido primero en el principal Headscale Gateway de Forgejo.
Se exporta al repositorio público `Gente-del-Condado/Mis_app_ha`:

- `build-images.yml` → `.github/workflows/build-images.yml`.
- Los Python de este directorio → `.github/ha-images/`.
- `check_gateway.py` deriva de `tools/check_container.py`; se actualizan juntos.

Cada origen entrega únicamente su aplicación a `build-source`, después de sus
comprobaciones habituales. La tienda conserva `main` para aplicaciones instalables.
El workflow selecciona árboles exactos pendientes, construye en runners nativos
amd64 y arm64, prueba los contenedores y publica candidatos identificados por el
árbol. Después crea la etiqueta de versión multi arquitectura y exige acceso
anónimo al índice antes de copiar la aplicación a main con `image:`.

Imágenes: `ghcr.io/gente-del-condado/ha-headscale-gateway`,
`ha-jacksignal-installer`, `ha-pivigia` y `ha-private-git-manager`.
Las versiones corresponden a config.yaml. Una modificación de un contexto ya
publicado exige incrementar su versión; no se reemplazan etiquetas estables.
`.images/APP.json` registra árbol, commit de preparación, origen Forgejo y digest.
La publicación conserva otras aplicaciones y reintenta conflictos sin forzar Git.

El GITHUB_TOKEN efímero de la tienda tiene `packages: write` en compilación y
además `contents: write` al actualizar main. No requiere tokens personales nuevos,
claves Android, ni acceso de escritura a Forgejo. GHCR crea los paquetes privados
la primera vez: el propietario debe configurar su visibilidad pública. El flujo
espera un máximo acotado y mantiene la tienda anterior si no puede descargarlos
anónimamente; nunca incorpora credenciales de registro a los manifiestos.

La primera entrega conserva las versiones actuales: las instalaciones existentes
seguirán utilizando su contenedor hasta una actualización explícita. No se
reinstalan aplicaciones ni se borran datos para efectuar esta migración.

Pruebas: Gateway (Supervisor/Ingress/CSRF/secretos/cierre), PiVigia (arranque,
autenticación y ejecución del modelo OpenCV), Private Git Manager (Ingress,
claves, redacción y rechazo de suplantación), JackSignal (instalación repetida,
copia de la versión anterior y archivos del usuario conservados). Son pruebas
nativas de las imágenes en contenedores desechables, no una actualización de
las instalaciones Home Assistant reales del usuario.
