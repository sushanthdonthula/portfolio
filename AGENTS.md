# Base44 Dev Environment Notes

- This is a **pure static site** (no build step, no backend, no DB, no secrets).
- Served by `nginx:1.27-alpine` via `docker-compose.base44.yml`, source bind-mounted at `/usr/share/nginx/html`.
- `nginx.base44.conf` sets `user root;` because the sandbox repo dir is root-only (0700) — nginx's default worker user gets 403 without it.
- Edits to HTML/CSS/JS/images appear on refresh immediately (no rebuild needed); use `reload_preview` to force the preview to refresh.
- Verify with: `curl -s -o /dev/null -w "%{http_code}" http://localhost:3000/` → 200.
