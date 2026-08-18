# [2026-08-18] — Restauración de `docs/` y sincronización del handbook con AI_CODE_INSTRUCTIONS

> Autor: claude-oscar
> Tipo: docs

## Resumen

Primera reconciliación del `DEVELOPER_HANDBOOK.md` de este repo con `wiki/AI_CODE_INSTRUCTIONS.md` (§29). Al ir a actualizarlo se descubrió que **la carpeta `docs/` no existía en `main`**: se creó en `6ed3125` y se borró en `45875f6`, ambos del 2026-06-05 y ambos titulados "update". El `CHANGELOG.md` llevaba desde entonces anunciando una estructura que no estaba en el repo.

## Cambios

- Restaurada `docs/` completa desde `45875f6^`: `guides/DEVELOPER_HANDBOOK.md`, `project/ROADMAP.md`, `shell/SECURITY_PROTOCOL.md`, `archive/.gitkeep`.
- **Handbook — nueva sección "Prerequisitos de deploy — acceso a las VMs de Google"**: la credencial de deploy es la service account nominal `<nombre>-dev`, nunca la cuenta personal `@trawlingweb.app` (caduca a las ~16 h por política de sesión de la organización **anpro21.com** —no del Admin console de trawlingweb.com— y en no-interactivo muere con `Reauthentication failed. cannot prompt during non-interactive execution`; las SA están exentas). `--tunnel-through-iap` explícito en todo `compute ssh`/`scp`: el puerto 22 está cerrado a internet y gcloud solo autodetecta IAP si la VM no tiene IP externa, y ambas la tienen por Caddy. Tabla de diagnóstico por mensaje de error, prohibición de repartir `*.json` de SA, nota de que la impersonation no elimina la reauth y de que Tailscale JIT (§28) no aplica a GCP.
- **Handbook — marcador** `<!-- AI_CODE_INSTRUCTIONS-sync: 2026-08-18 -->`.
- **Handbook — §32**: los cambios de sintaxis de keywords tocan tres repos y más de un dev → Issue de coordinación en `trawlingweb/wiki`, assignee = quien debe actuar.
- **Handbook — §9.3 y §23**: encadenamiento con la wiki tras commit/deploy y registro de tareas en `satKanbanTasks`.
- **Handbook — contenido propio del repo**: árbol de arquitectura con `API Reddit/`, `API Telegram/` y `changelogs/`; convención `user_name`/`user_screen_name` (Reddit duplica handle en ambos); nota de que desde 2026-06-22 una keyword Lucene inválida ya no bloquea `/counts`, `/posts/:worker_id` ni `/count/:worker_id`.
- `SECURITY_PROTOCOL.md`: regla sobre ficheros de service account y sobre secretos en `wiki/docs/` (indexada por el bot de Telegram).
- `ROADMAP.md`: entrada F3 y registro de la restauración.
- `CHANGELOG.md`: versiones 1.0.0 (2026-06-05) y 1.1.0 (2026-08-18) — antes todo colgaba de `[Unreleased]`.

## Impacto

Documentación pura: no cambia ningún endpoint ni sintaxis expuesta a cliente. Lo relevante es que este repo no despliega a VM (su deploy es el push a GitHub), pero **sus consumidores sí** (`feedscale_console_app` y las 6 APIs sociales en `mochi-vm`/`crawlers-vm`), y ahora el handbook explica por qué esos deploys fallaban.

## Referencias

- Branch: `v1`
- Wiki: `wiki/AI_CODE_INSTRUCTIONS.md` §9.3, §9.6, §23, §29, §32 · `wiki/docs/acceso_vms_google_gcloud.md`
