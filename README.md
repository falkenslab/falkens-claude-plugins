# Falken's Claude Plugins

Marketplace personal de plugins para [Claude Code](https://claude.ai/code) — skills, hooks, servidores MCP y comandos que amplían tu flujo de trabajo con Claude Code.

Cada plugin es independiente y se puede instalar por separado.

## Plugins disponibles

| Plugin                              | Versión | Descripción                                                         |
| ----------------------------------- | ------- | ------------------------------------------------------------------- |
| [git-plugin](./plugins/git-plugin/) | 0.0.1   | Operaciones Git desde Claude Code: commits inteligentes, push y más |


## Estructura de un plugin

```
plugins/
└── <nombre-plugin>/
    ├── .claude-plugin/
    │   └── plugin.json       # Nombre, descripción y versión
    ├── skills/
    │   └── <nombre-skill>/
    │       ├── SKILL.md      # Prompt que carga Claude Code
    │       └── README.md
    ├── hooks/
    │   └── <nombre-hook>/
    │       ├── hook.sh
    │       └── README.md
    └── mcp/
        └── <nombre-servidor>/
            └── README.md
```

## Añadir un plugin

1. Crea `plugins/<nombre-plugin>/` siguiendo la estructura anterior.
2. Añade `.claude-plugin/plugin.json` con nombre, descripción y versión.
3. Escribe un `README.md` por componente (descripción + instalación + ejemplo de uso).
4. Registra el plugin en `.claude-plugin/marketplace.json`.

Consulta [CLAUDE.md](./CLAUDE.md) para las convenciones y guías completas.
