# Cómo se trabaja acá

Convenciones de los repositorios de Mindy Haxor Team. Aplican por defecto a
todos; si un repositorio necesita algo distinto, lo escribe en su propio
`CONTRIBUTING.md`, que reemplaza a este.

Estos proyectos se construyen con ayuda de IA y no todos los que trabajan acá
programan. Por eso este documento pide poco y explica por qué: lo que está acá
es lo que de verdad evita problemas, no una ceremonia.

## Ramas

La rama principal se llama **`main`**, siempre.

Para trabajar, sal de `main` y crea una rama con un nombre que diga qué estás
haciendo:

```
feat/agregar-login       una funcionalidad nueva
fix/corregir-total       un arreglo
chore/subir-next         configuración o dependencias
```

Después abres un pull request hacia `main`. No es obligatorio técnicamente —en
estos repositorios no hay bloqueo— pero sí es la forma en que alguien más puede
ver qué cambió antes de que llegue a producción. Trabajar directo sobre `main`
significa que un error va a producción sin que nadie lo haya visto.

Si el proyecto necesita una rama de pruebas o de staging, agrégala y déjalo
escrito en el `README.md`, para que el resto del equipo y los agentes sepan a
qué rama apuntar.

Las ramas se borran solas al mergear.

## Mensajes de commit

Empieza el mensaje con una de estas palabras y dos puntos. No es capricho: de
eso sale el registro de cambios automático.

| Palabra | Cuándo |
| -- | -- |
| `feat:` | algo nuevo |
| `fix:` | un arreglo |
| `docs:` | documentación |
| `style:` | formato, sin cambiar comportamiento |
| `refactor:` | reordenar código sin cambiar qué hace |
| `chore:` | dependencias, configuración, CI |

```
feat: agregar filtro por fecha en el listado
fix: el total no sumaba el descuento
chore: actualizar dependencias
```

## Tests

En estos repositorios los tests **no bloquean**. Corren, se ven en el pull
request, y si están rojos es información — no un portón cerrado.

Lo que sí conviene tener, y es poco:

- **Un smoke test**: que el proyecto compile, arranque, y que la página
  principal responda. Un solo archivo, y atrapa el "lo rompí y no me di cuenta",
  que es la falla más común.
- **Un test por cada bug que arregles.** Escríbelo *antes* del arreglo y
  comprueba que falla. Un test escrito después casi nunca prueba lo que cree
  probar, y este es el único hábito de testing que sobrevive sin una cultura de
  tests previa.

Si le pides tests a un agente, revisa que realmente verifiquen algo. Un test que
no comprueba nada es peor que no tener test: se ve verde y da confianza falsa.

## Documentación

Toda la documentación del proyecto vive en el directorio `docs/` de la raíz del
repositorio, y se escribe en Markdown (`.md`). No se dejan documentos sueltos en
la raíz ni repartidos por otras carpetas: si es documentación, va en `docs/`.

El `README.md` es la excepción: se queda en la raíz, porque es lo primero que se
ve al abrir el repositorio. Todo lo demás —guías, notas técnicas, decisiones,
instrucciones de setup— va en `docs/`, con nombre en minúsculas y palabras
unidas por guiones (`docs/deploy-a-staging.md`, no `docs/Deploy Staging.md`).

## Registro de cambios

Cada repositorio tiene un `CHANGELOG.md`. Si tu cambio altera cómo se comporta
el proyecto, agrega una línea bajo `## [No publicado]` diciendo qué cambió, en
lenguaje de quien usa el proyecto. Los cambios de configuración o dependencias
no la necesitan.

El historial de commits ya dice *qué* se cambió. El changelog es para el *por
qué*, que es exactamente lo que se pierde cuando el código lo escribió un
agente.

## Seguridad

Acá no hay flexibilidad, y es la parte más importante de este documento.

**Nunca subas al repositorio**: archivos `.env`, llaves, certificados, tokens,
contraseñas, ni exports de datos reales (planillas, CSV, dumps de base de
datos). Cuando un proyecto necesita variables de entorno, se versiona un
`.env.example` con los **nombres** de las variables y sin ningún valor.

Cada push pasa por un escaneo automático de secretos. Si marca algo, **no lo
silencies para que pase**: confirma primero si es real.

**Si un secreto llegó a un commit, lo primero es rotar la credencial** — o sea,
generar una nueva y desactivar la vieja. Borrarlo del historial no lo invalida:
cualquiera que haya clonado el repositorio antes ya lo tiene.

Instala el hook que revisa esto antes de cada commit, una vez por proyecto:

```
git config core.hooksPath .githooks
```

## Trabajar con agentes

Cada repositorio tiene un `AGENTS.md` en la raíz con el contexto del proyecto.
Si el agente se equivoca siempre en lo mismo, la corrección va **en ese
archivo**, no en el prompt de cada sesión. Así el próximo que trabaje —persona o
agente— arranca con eso ya resuelto.

Un cambio escrito por un agente entra igual que cualquier otro: con alguien que
lo leyó y responde por él. "Lo hizo la IA" no es una explicación cuando algo se
rompe.

Para reportar una vulnerabilidad, ver [SECURITY.md](SECURITY.md).
