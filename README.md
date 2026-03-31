# openspec-kanban

Scripts y configuración para usar [Kanban](https://docs.cline.bot/kanban/overview) como frontend de orquestación para [OpenSpec](https://github.com/Fission-AI/OpenSpec).

Diseño detallado: [`docs/integration.md`](docs/integration.md)

---

## Qué incluye

```
scripts/
  opsx-to-kanban.sh          Crea tarjetas Kanban desde changes de OpenSpec
  copilot-kanban-wrapper.sh  Lanza GitHub Copilot CLI con hooks Kanban

.claude/
  settings.json              Hooks de Claude Code → Kanban
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

# 3. Abre Kanban en el navegador y ejecuta el agente desde la tarjeta
cline
```

## Configuración por agente

### Claude Code

Copia `.claude/settings.json` a tu proyecto (o fusiona con el existente).
Los hooks reportan progreso a Kanban automáticamente durante la sesión.

### GitHub Copilot CLI

```bash
bash scripts/copilot-kanban-wrapper.sh <change-id> "implementa los tasks pendientes"
```
