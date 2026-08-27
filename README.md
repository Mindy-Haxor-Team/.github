# .github

Repo especial de la organización **Mindy-Haxor-Team** en GitHub.

## Qué es

GitHub le da un tratamiento particular al repo llamado `.github` dentro de una organización: el archivo `profile/README.md` que contiene se muestra como la página de presentación pública de la organización (`github.com/Mindy-Haxor-Team`). Ese es el único contenido que tiene hoy este repo.

Este repo además aloja los archivos de "community health" por defecto del resto de
repositorios de la organización, que GitHub aplica automáticamente a cualquier repo
de `Mindy-Haxor-Team` que no defina el suyo propio. Editar acá es editar el estándar
de todos los repos a la vez, sin copiar nada.

| Archivo | Qué es |
| -- | -- |
| `CONTRIBUTING.md` | Ramas, commits, tests, seguridad y trabajo con agentes |
| `SECURITY.md` | Cómo reportar una vulnerabilidad |
| `.github/PULL_REQUEST_TEMPLATE.md` | Plantilla de pull request |
| `.github/ISSUE_TEMPLATE/` | Formularios de bug y de solicitud |

**No se heredan** `CODEOWNERS`, `LICENSE`, `.gitignore`, `dependabot.yml` ni los
workflows: cada repositorio necesita los suyos, y para eso está
`mindy-haxor-template`. La herencia es todo-o-nada por archivo: un repo con su
propio `.github/ISSUE_TEMPLATE/` ignora por completo el de acá.

## Este repositorio es público

GitHub exige que el repositorio de archivos por defecto sea público; con uno privado
la herencia no ocurre. Todo lo que se agregue acá queda legible por cualquiera en
internet, así que no puede contener nombres de hosts, IPs, rutas internas, nombres
de clientes o instituciones, ni detalles de arquitectura. Si algo necesita ese
nivel de detalle, va en el repositorio privado que corresponda.

El workflow de seguridad que usan estos repos no vive acá: se invoca desde
`MindyNetworks/.github`, que también es público, así que un arreglo de reglas o de
pins llega a las tres organizaciones a la vez.

## Estructura

- `profile/README.md`: contenido que se ve en la página principal de la organización.
- `profile/mindy-banner.png`: banner usado en ese README.

## Alcance

Este README (en la raíz del repo) es solo para dejar constancia, a quien navegue el repo directamente, de para qué sirve. El contenido que ven los visitantes de la organización sigue siendo `profile/README.md`.
