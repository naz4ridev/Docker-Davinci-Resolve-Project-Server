# DaVinci Resolve Project Server — naz4ri fork

Fork de `elliotmatson/Docker-Davinci-Resolve-Project-Server` para nuestra infra Coolify + Cloudflare Tunnel.

## Cambios vs upstream
- Compose simplificado sin `x-common` anchors.
- Volúmenes named managed por Coolify.
- Postgres 13-alpine (Alpine para menor tamaño).
- pgAdmin sin ports directos; se expone vía Traefik en `pgadmin.davinci.naz4ri.dev` (o similar).
- Datos migrados del studio-server-client viejo (v1.0.11 de wirebear) — mismos hashes SCRAM, colaboradores no notan cambio.

## Envs
- `POSTGRES_PASSWORD` — usar el hash SCRAM heredado
- `PGADMIN_PASSWORD` — password pgAdmin

## Acceso remoto
Cloudflare Tunnel expone el puerto 5432 sin dejar puertos abiertos ni IP visible.
Ver `/root/docs/davinci-tunnel.md` para setup del tunnel + `cloudflared access` en clientes.
