# openspec-kanban

Scripts y configuración para usar [Kanban](https://docs.cline.bot/kanban/overview) como frontend de orquestación para [OpenSpec](https://github.com/Fission-AI/OpenSpec).

Diseño detallado: [`docs/integration.md`](docs/integration.md)

---

## Instalación en un proyecto

```bash
copier copy /ruta/a/openspec-kanban .
# o cuando esté publicado:
copier copy gh:<usuario>/openspec-kanban .
```

Para actualizar cuando el template cambie:

```bash
copier update
```

## Qué se copia al proyecto

```
scripts/
  opsx-to-kanban.sh          Crea tarjetas Kanban desde changes de OpenSpec
  copilot-kanban-wrapper.sh  Lanza GitHub Copilot CLI con hooks Kanban

.claude/
  settings.json              Hooks de Claude Code → Kanban

.gitignore                   Excluye openspec/.kanban-mapping del control de versiones
```

## Requisitos

- [`kanban` CLI](https://docs.cline.bot/kanban/getting-started) (`npm i -g cline`)
- [`openspec` CLI](https://github.com/Fission-AI/OpenSpec) (`npm i -g @fission-ai/openspec`)
- Para Copilot: `gh` CLI con `gh extension install github/gh-copilot`

## Uso rápido

```bash
# 1. En tu proyecto, propón un change con OpenSpec
/opsx:propose "descripción del cambio"

# 2. Sincroniza el change al tablero Kanban
bash scripts/opsx-to-kanban.sh <change-id>

# 3. Abre Kanban y ejecuta el agente desde la tarjeta
cline
```
