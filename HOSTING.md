# Hosting ProGuard 24/7

Your PC has to be **off** sometimes, so the bot can't run from it around the clock.
The fix: run it on a free cloud host. The bot keeps running there even when your
PC is off — you only reconnect to update the files.

> **Keep your bot token secret.** Never upload your `.env` to Discord, GitHub, or
> anywhere public. If it leaks, regenerate it in the [Discord Developer Portal](https://discord.com/developers/applications).

---

## Recommended: Bot-Hosting.net (free, always-on, no sleep mode)

Free plan: 1 bot, always on, auto-restart on crash, daily backups, Node.js runtime.
No credit card required.

### Step-by-step

1. **Get the upload package**
   Use `pro-discord-bot-upload.zip` (in this folder). It contains everything
   **except** `node_modules` and your `.env` — the host installs dependencies for you.

2. **Create an account**
   Go to <https://bot-hosting.net/> → **Create free account**.

3. **Create a server**
   In the panel, create a new server and pick the **Node.js** runtime.

4. **Upload your files**
   Use the panel's file manager (or SFTP) and upload the contents of the zip.
   You should end up with `package.json` and the `src/` folder in the server root.

5. **Add your token as an environment variable**
   In the server's env-variables/settings section add:
   - `DISCORD_TOKEN` = your bot token (from the Developer Portal → Bot)
   - `CLIENT_ID` = your application ID (Developer Portal → General Information)

   Alternatively, upload a `.env` file containing the same two lines — both work.

6. **Set the startup command / file**
   Startup file: `src/index.js` — or startup command: `npm start`
   (the host runs `npm install` automatically from `package.json`).

7. **Start the server**
   The bot comes online and stays online 24/7, even with your PC off.

8. **Register the slash commands (once, from your PC or the host console)**
   Run this once after inviting the bot to your server:
   ```
   npm run deploy
   ```
   You can run it in the host's console tab. If `GUILD_ID` is set in your `.env`,
   commands appear instantly in that one server.

### Updating the bot later
Edit files locally, re-zip, and re-upload the changed files (or connect via SFTP),
then restart the server in the panel.

---

## Alternatives

| Host | Free tier | Notes |
|---|---|---|
| [Wispbyte](https://wispbyte.com/free-discord-bot-hosting) | Free forever, 24/7 | Similar panel, no credit card |
| [Koyeb](https://www.koyeb.com) | 1 free instance | **Sleeps after 1h without traffic** — that's why `index.js` now includes a keep-alive web server (auto-starts when the host sets `PORT`) |
| [Render](https://render.com) | Free web service | Sleeps after 15 min idle; needs the keep-alive server + an uptime pinger |

For a simple "set and forget" setup, Bot-Hosting.net or Wispbyte are the easiest
because they never sleep.

---

## Files added for hosting

- `src/index.js` — now starts a tiny health-check web server when the host
  provides a `PORT` environment variable (or when `KEEP_ALIVE=1` is set).
  Bot-Hosting.net doesn't need it; Render/Koyeb do.
- `pro-discord-bot-upload.zip` — ready-to-upload package (no `node_modules`, no `.env`).
