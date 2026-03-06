# Media Companion

Mobile-friendly PWA for requesting content through [Media Manager](https://github.com/Pennderin/Media-Manager). Search for movies and TV shows from your phone, one-tap grab, and get notified when they're ready in Plex.

## What It Does

- **Search** — Find movies and TV shows via TMDB
- **One-tap grab** — Automatically finds the best torrent, downloads, renames, and organizes
- **TV modes** — Grab full series, single season, or specific episode
- **Top 20** — Browse trending content by day/week/month
- **Progress tracking** — Watch your requests move through the pipeline
- **Notifications** — Push notifications and SMS when content hits Plex

## Requirements

- [Media Manager](https://github.com/Pennderin/Media-Manager) running on your network
- That's it — Companion is a thin frontend that proxies everything through Media Manager

## Install

### Docker

```bash
docker run -d --name media-companion \
  --restart unless-stopped \
  -p 3000:3000 \
  -v /path/to/config:/config \
  -e MANAGER_URL=http://YOUR_NAS_IP:9876 \
  -e PORT=3000 \
  -e CONFIG_DIR=/config \
  ghcr.io/pennderin/media-companion:latest
```

### Unraid

Install from Community Applications — search for "Media Companion". Set the `MANAGER_URL` to your Media Manager instance (e.g., `http://192.168.0.190:9876`).

### docker-compose

Media Companion is included in the [Media Manager docker-compose.yml](https://github.com/Pennderin/Media-Manager/blob/main/docker-compose.yml) — both containers start together.

## Environment Variables

| Variable | Required | Default | Description |
|----------|----------|---------|-------------|
| `MANAGER_URL` | Yes | `http://127.0.0.1:9876` | URL of your Media Manager instance |
| `PORT` | No | `3000` | Port to serve the PWA on |
| `CONFIG_DIR` | No | App directory | Where to store config and request history |

## Usage

Open `http://YOUR_NAS_IP:3000` on your phone and add it to your home screen for the best experience. The app works as a PWA — it looks and feels like a native app.

### SMS Notifications

To receive a text when your content is ready in Plex, configure SMS in the settings tab. Requires SMTP credentials configured in Media Manager's settings.
