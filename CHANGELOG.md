# Changelog — feedscale_APIservicies

Formato basado en [Keep a Changelog](https://keepachangelog.com/).

## [1.1.0] — 2026-08-18 — Restauración de `docs/` y sincronización del handbook

### Corregido

- Restaurada la carpeta `docs/` completa (`guides/DEVELOPER_HANDBOOK.md`, `project/ROADMAP.md`, `shell/SECURITY_PROTOCOL.md`, `archive/`), borrada por error en el commit `45875f6` del 2026-06-05 el mismo día en que se creó. El `CHANGELOG.md` la seguía anunciando como existente.

### Añadido

- **Prerequisitos de deploy — acceso a las VMs de Google** en el handbook: credencial = service account nominal `<nombre>-dev` (las cuentas `@trawlingweb.app` caducan a las ~16 h por política de la organización anpro21.com y mueren en no-interactivo con `Reauthentication failed`), `--tunnel-through-iap` obligatorio y explícito en todo `compute ssh`/`scp`, tabla de diagnóstico por mensaje de error y prohibiciones absolutas (no repartir keys de SA, no escribir secretos en `wiki/docs/`).
- Marcador de sincronización `<!-- AI_CODE_INSTRUCTIONS-sync: 2026-08-18 -->` (§29) — primera reconciliación del handbook con `AI_CODE_INSTRUCTIONS.md`.
- Sección de coordinación cross-repo (§32): un cambio de sintaxis toca este repo + `wiki` + `feedscale_console_app` → Issue de coordinación en `trawlingweb/wiki`, el assignee dice quién actúa.
- Sección de encadenamiento con la wiki tras commit/deploy (§9.3) y sección de Kanban (§23).
- Convención `user_name` / `user_screen_name` y nota sobre keywords inválidas no bloqueantes desde 2026-06-22.

### Mejorado

- Árbol de arquitectura del handbook: incluye `API Reddit/`, `API Telegram/` y `changelogs/`, que faltaban.
- `SECURITY_PROTOCOL.md`: regla explícita sobre ficheros `*.json` de service account y sobre secretos en `wiki/docs/`.

---

## [1.0.0] — 2026-06-05 — Estructura documental estándar

### Añadido

- Estructura `docs/` estándar Trawlingweb: `docs/guides/DEVELOPER_HANDBOOK.md`, `docs/project/ROADMAP.md`, `docs/shell/SECURITY_PROTOCOL.md`, `docs/archive/`, `changelogs/_template.md` y este `CHANGELOG.md`.

---

## Historial previo

Antes de 2026-06-05 el repo no llevaba `CHANGELOG.md`. El historial de cambios anteriores está en `git log`. Cambios significativos relevantes:

- **2026-05-19** — Añadido `CLAUDE.md` con contexto del proyecto y estándares Trawlingweb.
