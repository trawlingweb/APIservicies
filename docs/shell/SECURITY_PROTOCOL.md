# Protocolo de Seguridad — feedscale_APIservicies

> Repo de **documentación pública**. No hay código ejecutable, ni servidor, ni credenciales. La superficie de ataque se limita al contenido que se publica.

## Autenticación y Autorización

No aplica — el repo es público.

## Gestión de Secretos y Credenciales

**Regla absoluta**: NUNCA commitear tokens, API keys, passwords ni ejemplos con credenciales reales.

- Los ejemplos de URL/curl deben usar tokens placeholder (`YOUR_API_KEY`, `xxxxxxxx`).
- Si un ejemplo necesita un payload realista, anonimizar IDs, emails y dominios.
- Si se descubre un secreto commiteado por error, **rotar inmediatamente** la credencial real y purgar del historial vía `git filter-repo` (no basta con un revert).
- **Ficheros `*.json` de service account de Google**: nunca se copian, se mueven ni se comparten — ni a este repo, ni a un chat, ni a la wiki. Si un dev no puede desplegar, se le crea su propia SA nominal (`wiki/docs/acceso_vms_google_gcloud.md` §6.2).
- Los secretos de infraestructura no van a `wiki/docs/` (el bot de Telegram indexa esa carpeta y la reenvía al canal), sino a `wiki/MAQUINAS.md`.

## Validación de Entrada

No aplica — no hay inputs de usuario.

## Dependencias y Vulnerabilidades

No aplica — sin dependencias ejecutables.

## Logs y Auditoría

No aplica.

## Reglas Específicas del Proyecto

- **No publicar URLs internas** de infraestructura (IPs de VMs, hostnames de DBs, paneles internos) en la documentación pública de APIs.
- **No publicar nombres de clientes** ni datos reales de su uso. Los ejemplos deben ser genéricos.
- **No referenciar endpoints en desarrollo** que aún no estén soportados en producción — clientes los intentarán llamar.
- **Coherencia con `validateWordsForApi()`**: cualquier sintaxis documentada aquí debe coincidir con la validación de `feedscale_console_app`. Documentar algo que el validador rechace genera tickets de soporte.

## Referencias

- Estándar Trawlingweb: `wiki/AI_CODE_INSTRUCTIONS.md` §9.2.
- Acceso a VMs de Google: `wiki/docs/acceso_vms_google_gcloud.md`.
