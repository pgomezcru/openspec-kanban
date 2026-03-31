# openspec-kanban

Scripts y configuración para usar [Kanban](https://docs.cline.bot/kanban/overview) como frontend de orquestación para [OpenSpec](https://github.com/Fission-AI/OpenSpec).

Diseño detallado: [`docs/integration.md`](docs/integration.md)

---

## Instalación en un proyecto

```bash
copier copy /ruta/a/openspec-kanban . --trust
# o cuando esté publicado:
copier copy gh:<usuario>/openspec-kanban . --trust
```

> `--trust` es necesario porque el template ejecuta un script Python post-copia
> para añadir la entrada a `.gitignore` sin sobreescribir su contenido.

Para actualizar cuando el template cambie:

```bash
python -m copier update --trust --src-path /ruta/a/openspec-kanban
```

## Qué se copia al proyecto

```
scripts/
  opsx-to-kanban.sh          Crea tarjetas Kanban desde changes de OpenSpec
  copilot-kanban-wrapper.sh  Lanza GitHub Copilot CLI con hooks Kanban

.claude/
  settings.json              Hooks de Claude Code → Kanban

.gitignore                   Añade openspec/.kanban-mapping (sin sobreescribir el existente)
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
