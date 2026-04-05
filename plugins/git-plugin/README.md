# git-plugin

Plugin para Claude Code que automatiza las operaciones más comunes de Git directamente desde la sesión de Claude.

## Skills disponibles

| Skill                      | Comando   | Descripción                                                                              |
| -------------------------- | --------- | ---------------------------------------------------------------------------------------- |
| [commit](./skills/commit/) | `/commit` | Analiza los cambios, los agrupa en commits lógicos y pide confirmación antes de ejecutar |
| [push](./skills/push/)     | `/push`   | *(próximamente)*                                                                         |

## Requisitos

- Git instalado y disponible en el `PATH`.
- El directorio de trabajo debe ser un repositorio Git válido.
