# LiveCaptures — sales one-pager

Statische landingspagina voor livecaptures.nl (pre-sell). Geen build-stap: `index.html` is
zelfstandig, inline CSS + inline SVG-logo.

## Deploy

Zelfde patroon als `ibrave-os-landing` / `social-rebel-landing`: bij een push naar `main`
draait `.github/workflows/deploy.yml` en:

1. Kloont/pullt deze repo naar `/opt/livecaptures-website-repo` op de Hetzner-server (`46.225.212.58`).
2. Serveert die map via een `nginx:alpine`-container `livecaptures-website` op poort **8084**,
   aangesloten op het bestaande Docker-netwerk `ibrave-os_default`.

**Vereiste repo-secrets** (Settings → Secrets and variables → Actions) — nog niet gezet:
- `HETZNER_SSH_PASSWORD` — zelfde SSH-wachtwoord als gebruikt in `ibrave-os-landing`/`social-rebel-landing`.
- `DEPLOY_PAT` — GitHub Personal Access Token met leesrecht op deze repo, zelfde als de andere landingspagina's.

Publieke bereikbaarheid op livecaptures.nl vereist daarna nog een Cloudflare Tunnel-hostname
naar `localhost:8084` op de server (zelfde tunnel-ID als de andere iBrave-producten,
`0c81673a-dbee-4129-b538-7263fc3d695a`) — dit regelt Dylan zelf, zoals bij de eerdere
producten.
