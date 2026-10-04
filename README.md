# Immich

Self-hosted photo and video backup, like Google Photos but on your own server.

## What you need

- A server or PC with Docker and Docker Compose installed
- A bit of free disk space for your photos

## Setup

1. Clone this repo onto your server:

   ```bash
   git clone https://github.com/trafficit/Immich.git
   cd Immich
   ```

2. Copy the example env file and open it:

   ```bash
   cp .env.example .env
   ```

3. Edit `.env` and change `DB_PASSWORD` to your own random password. Leave everything else as is unless you know you need to change it.

4. Start everything:

   ```bash
   docker compose up -d
   ```

   The first run downloads the images, so it can take a few minutes.

5. Check it's running:

   ```bash
   docker compose ps
   ```

   You should see 4 containers up: `immich-server`, `immich-machine-learning`, `redis`, `database`.

## Using it

1. Open `http://<your-server-ip>:2283` in a browser.
2. Create your admin account on first visit.
3. Install the Immich app on your phone (App Store / Play Store).
4. In the app, enter the same address, log in, open **Backup**, pick your albums, and hit **Start Backup**.

Keep your phone on charge with the screen on for the first backup — it's faster that way.

## Where your data lives

- Photos/videos: `./library`
- Database: `./postgres`

Both folders are created next to `docker-compose.yml` and are ignored by git, so your photos never end up in this repo.

## Updating

```bash
docker compose pull
docker compose up -d
```

## Stopping

```bash
docker compose down
```

This stops the containers but keeps your data in `./library` and `./postgres`.
