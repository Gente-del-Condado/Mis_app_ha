# Aplicaciones de Gente del Condado

![Icono del catálogo](icon.png)

Mi repositorio oficial de aplicaciones para Home Assistant.

[![Añadir a Home Assistant](https://my.home-assistant.io/badges/supervisor_add_addon_repository.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https%3A%2F%2Fgithub.com%2FGente-del-Condado%2FMis_app_ha)

[Manual del gestor](https://gente-del-condado.github.io/HA-Private-Git-Manager/) · [Catálogo de integraciones y Forgejo Backup](https://gente-del-condado.github.io/HA-Private-Git-Manager/#componentes)

## Instalación

Pulsa el botón anterior o añade este repositorio desde **Ajustes → Aplicaciones →
Tienda → menú ⋮ → Repositorios**:

```text
https://github.com/Gente-del-Condado/Mis_app_ha
```

Después selecciona la aplicación y sigue su documentación. **JackSignal Installer** se inicia una vez para copiar la integración y se detiene; después debes reiniciar Home Assistant. Las aplicaciones con interfaz web se abren desde su ficha.
La primera instalación construye la app y requiere conexión a Internet.

## Aplicaciones

| Aplicación | Descripción | Arquitecturas |
| --- | --- | --- |
| [JackSignal Installer](jacksignal_installer/README.md) | Instala JackSignal: avisos de Alarmo, apertura/cierre, voz de sensores sin YAML y DLNA solo de audio con prioridades. | `amd64`, `aarch64` |
| [HA Private Git Manager](private_git_manager/README.md) | Gestiona claves SSH y aplicaciones de repositorios GitHub, Forgejo y Gitea desde Home Assistant. | `amd64`, `aarch64` |
| [PiVigia](pivigia/README.md) | Analiza localmente fotos de cámaras recibidas por SMTP y envía avisos por correo o Telegram; incluye RTSP opcional. | `amd64`, `aarch64` |
| [Headscale Gateway](headscale_gateway/README.md) | Ejecuta y administra Headscale Gateway en Home Assistant. | `amd64`, `aarch64` |

[Guía de uso](private_git_manager/DOCS.md) · [Historial de versiones](private_git_manager/CHANGELOG.md)

[Guía de PiVigia](pivigia/DOCS.md) · [Cambios de PiVigia](pivigia/CHANGELOG.md)

La integración opcional de sensores de PiVigia para
Home Assistant se instala por separado. Si ya utilizas PiVigia desde otro
repositorio o una carpeta local, añadir esta tienda no migra sus datos ni sustituye
automáticamente aquella instalación.

## Origen y actualizaciones

Los cuatro proyectos se desarrollan primero en Forgejo. GitHub recibe sus
espejos y ejecuta los publicadores, que escriben directamente en esta tienda.
No hay una copia de esta tienda en Forgejo ni sincronización de regreso.

| Aplicación | Origen Forgejo | Espejo GitHub | Carpeta publicada |
| --- | --- | --- | --- |
| Headscale Gateway | [Forgejo](https://gentedelcondado.es/forgejo/wolfbelmi88/headscale_gateway) | [GitHub](https://github.com/Gente-del-Condado/headscale_gateway) | `headscale_gateway/` |
| PiVigia | [Forgejo](https://gentedelcondado.es/forgejo/wolfbelmi88/pivigia) | [GitHub](https://github.com/Gente-del-Condado/pivigia) | `pivigia/` |
| JackSignal | [Forgejo](https://gentedelcondado.es/forgejo/wolfbelmi88/jacksignal) | [GitHub](https://github.com/Gente-del-Condado/jacksignal) | `jacksignal_installer/` |
| Private Git Manager | [Forgejo](https://gentedelcondado.es/forgejo/wolfbelmi88/HA-Private-Git-Manager) | [GitHub](https://github.com/Gente-del-Condado/HA-Private-Git-Manager) | `private_git_manager/` |

Headscale Gateway, PiVigia y JackSignal publican después de superar sus flujos
de calidad en el `main` vigente de GitHub. Private Git Manager tiene publicadores
propios por cambios en `main`. Los principales de los tres primeros son privados;
la distribución instalable es pública. Los commits de publicación identifican
la revisión de origen. Cada publicador conserva los demás proyectos.

No edites las carpetas generadas: corrige la fuente en el principal de Forgejo.
La publicación no instala automáticamente las actualizaciones en los equipos.
