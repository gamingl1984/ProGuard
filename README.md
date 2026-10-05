# ProGuard — Local Discord Bot

An all-in-one Discord bot (moderation, security, AutoMod, tickets, staff tools, Roblox logging) that runs locally on your Windows PC or Linux machine — or 24/7 on a free cloud host, even when your PC is off. See [HOSTING.md](HOSTING.md).

**Licensing:** this bot is free to use and share, but **selling it is prohibited** — see [LICENSE](LICENSE). People who use the bot in a server agree to the [Terms of Service](TERMS_OF_SERVICE.md), also viewable in Discord with `/terms`.

## Included

### Moderation
- `/ban`
- `/tempban` (auto-unban when time is up)
- `/unban`
- `/kick`
- `/timeout`
- `/untimeout`
- `/warn`
- `/warnings`
- `/clearwarnings`
- `/purge`
- `/slowmode`
- `/lock`
- `/unlock`
- `/nick`
- `/softban`
- `/dm`
- `/blacklist add` / `/blacklist remove` / `/blacklist list` / `/blacklist check`
- Configurable **auto-demotion**: after X warnings (e.g. 3) a role of your choice is removed automatically (`/config warn-demotion`)

### Role management
- `/role add`
- `/role remove`
- `/role create`
- `/role delete`
- `/role edit`
- `/role list`

### Server / utility
- `/help`
- `/ping`
- `/serverinfo`
- `/userinfo`
- `/avatar`
- `/announce`
- `/say`
- `/embed`
- `/poll`
- `/botinfo`
- `/servericon`
- `/stealemoji`
- `/snipe`
- `/setstatus`
- `/remind`
- `/roll`
- `/rps`

### Security & AutoMod
- `/automod anti-invite` / `anti-link` / `anti-spam` / `banned-words` / `max-mentions` / `ignore-channel` / `status`
- `/lockdown` (lock/unlock every public text channel at once)
- `/nuke` (clone-and-delete a channel to wipe its messages)
- Security alerts: channel deletions, role deletions and external bans are reported to the log channel with the responsible user (from audit logs)

### Case system (Dyno-style)
- Every ban / kick / timeout / warn / softban / tempban automatically gets a numbered case
- `/case view <id>`, `/case recent`, `/modlogs <user>` (full history + summary), `/reason <id> <new reason>`

### Staff clock-in
- `/clock in` / `/clock out` — records session length and running totals (persisted)
- `/clock panel` — posts a **button panel** (🟢 Clock In / 🔴 Clock Out) so staff clock in with one click
- `/clock status [user]`, `/clock leaderboard` (top 10 by total time)
- Clock in/out events are logged to the log channel and to file

### Welcome & engagement
- `/welcome set` / `leave-set` / `off` / `test` — customizable messages with `{user} {username} {server} {count}` placeholders
- `/config autorole` — automatic role for new members
- `/config persistroles` — members keep their roles when they leave and rejoin
- `/rr add` / `remove` / `list` — reaction roles
- `/giveaway` — timed giveaways with 🎉 reactions and automatic winner selection
- `/welcome view` — see the current messages; run `/welcome set` again to change them

### Announcements
- `/announce set <channel>` — set the default announcement channel
- `/announce send <title> <message> [role1] [role2] [role3] [channel]` — sends a styled embed and **pings up to 3 roles of your choice** with your message

### Roblox integration
- `/roblox log-channel <channel>` — choose where Roblox logs go
- `/roblox log <executor> <command> [server] [target]` — log an in-game command with a formatted embed
- `/roblox blacklist player|server <name>` — blacklist **Roblox players and servers** (with reason)
- `/roblox unblacklist`, `/roblox blacklist-list`, `/roblox check`
- **Server startup announcer:** `/roblox startup-config` (game name, Roblox game link, group link, channel, up to 3 roles to ping) then `/roblox startup [message]` any time your game server goes live — it posts a green embed with the links and pings the configured roles
- Logged commands from blacklisted players/servers are automatically flagged in red
- All Roblox logs also go to the Discord log channel and `data/logs/` files

### Logging
- Every command and moderation action is logged to the log channel of your choice (`/config logs`)
- Everything is **also written to dated files**: `data/logs/bot-YYYY-MM-DD.log`
- Toggle per-command logging with `/config command-logging`
- Member joins/leaves, deleted/edited messages, tickets and all moderation actions are logged

### Staff / LOA
- `/staff loa` (with an optional `days` length — the LOA auto-expires and removes itself)
- `/staff loa-remove`
- `/staff loa-check`
- `/staff loa-list`
- `/staff promote`
- `/staff demote`
- `/staff note`
- Persistent local LOA records
- Expected return date/time
- LOA reason and moderator tracking
- LOA start/end logging

### Configuration
- `/config logs`
- `/config ticket-category`
- `/config ticket-staff`
- `/config levelup-channel` / `/config levelrole`
- `/config show`

### Extra utilities
- `/utility roleinfo`
- `/utility channelinfo`
- `/utility permissions`
- `/utility timestamp`
- `/utility choose`

### Tickets
- `/ticket setup`
- `/ticket open`
- `/ticket close`
- `/ticket add`
- `/ticket remove`
- `/ticket claim`
- Button-based opening/closing
- Private ticket permissions
- Optional staff role/category
- Ticket open/close logging

### Levels & engagement (MEE6/Carl-bot style)
- XP for chatting (1 drop per minute), `/rank` with progress bar, `/leaderboard` (top 10)
- `/config levelup-channel` — level-up announcements, `/config levelrole add/remove/list` — roles granted at levels
- `/trigger add/remove/list` — custom auto-responses (exact or contains match)
- `/sticky set/off` — a message that keeps reposting at the bottom of a channel
- `/afk [message]` — AFK notice when mentioned, auto-clears when you return
- `/starboard set/off` — messages with enough ⭐ reactions get posted to a starboard channel

### More moderation & utility (ProBot/Dyno style)
- `/mute` / `/unmute` — timeout aliases
- `/voice kick/move/mute/unmute` — voice channel moderation
- `/channel create/delete/rename/topic` — channel management
- `/banlist`, `/firstmessage`, `/emojis`, `/banner`, `/invite`

### Economy (Dank Memer style)
- `/economy balance` / `daily` (500 coins/day) / `work` (every 30 min)
- `/economy gamble` / `rob` / `pay` / `leaderboard` — persistent per-server wallets

### Smart tools & more fun
- `/trivia` — real trivia questions with **clickable answer buttons** (20s timer)
- `/action hug/pat/punch/kiss` — animated GIF actions
- `/urban` (Urban Dictionary), `/wiki` (Wikipedia), `/weather` (live weather, no API key), `/calculate`
- `/serverbanner`, `/massrole add/remove` (admin, confirmation required)
- `/giveaway start` / `/giveaway reroll`

### Fun (live from public APIs)
- `/meme` (Reddit), `/joke`, `/cat`, `/dog`

### Harmless fun/troll
- `/troll slap`
- `/troll ship`
- `/troll 8ball`
- `/troll coinflip`
- `/troll mock`
- `/troll reverse`

The bot intentionally does NOT include destructive PC commands, token stealers, self-bot behavior, mass-DM spam, mass-channel destruction, or anything intended to damage a computer/server.

---

# 1. Create the Discord application

1. Open the Discord Developer Portal.
2. Create a New Application.
3. Open the **Bot** page and create the bot.
4. Copy the bot token.
5. Keep the token private. Never post it in Discord or GitHub.
6. Open **OAuth2 → URL Generator**.
7. Select:
   - `bot`
   - `applications.commands`
8. Give the bot only the permissions it actually needs. For the included moderation features, the bot normally needs:
   - View Channels
   - Send Messages
   - Embed Links
   - Read Message History
   - Manage Messages
   - Manage Channels
   - Manage Roles
   - Kick Members
   - Ban Members
   - Moderate Members
9. Invite the generated bot URL to your server.

Discord's command permissions can also be controlled later from Server Settings → Integrations.

# 2. Install Node.js

Install Node.js 20 or newer.

Check:

```cmd
node -v
npm -v
```

Both commands should return a version.

# 3. Configure the bot

Copy:

```text
.env.example
```

to:

```text
.env
```

Open `.env` and enter:

```env
DISCORD_TOKEN=YOUR_BOT_TOKEN
CLIENT_ID=YOUR_APPLICATION_ID
GUILD_ID=YOUR_SERVER_ID
```

`GUILD_ID` is recommended while setting up because guild slash commands appear quickly. Remove it later if you want global commands.

Optional settings:

```env
LOG_CHANNEL_ID=123456789012345678
TICKET_CATEGORY_ID=123456789012345678
TICKET_STAFF_ROLE_ID=123456789012345678
```

The same IDs can be configured later in `data/config.json`.

# 4. Install dependencies

Windows CMD:

```cmd
cd C:\path\to\pro-discord-bot
npm install
npm run deploy
npm start
```

Linux:

```bash
cd /path/to/pro-discord-bot
npm install
npm run deploy
npm start
```

When you see:

```text
YourBot#0000 is online.
```

the bot is running.

# 5. Configure logging

Put your log channel ID in `.env`:

```env
LOG_CHANNEL_ID=YOUR_LOG_CHANNEL_ID
```

Restart the bot.

The bot logs important moderation actions plus member joins/leaves and message edits/deletions.

# 6. Configure tickets

Create a category and staff role in Discord.

Put their IDs in `.env`:

```env
TICKET_CATEGORY_ID=YOUR_CATEGORY_ID
TICKET_STAFF_ROLE_ID=YOUR_STAFF_ROLE_ID
```

Restart the bot.

Then run:

```text
/ticket setup
```

The bot creates a professional ticket panel with buttons.

# 7. Windows — start automatically when you sign in

The simplest method is Windows Task Scheduler.

Create:

```text
start-bot.bat
```

with:

```bat
@echo off
cd /d C:\path\to\pro-discord-bot
npm start
```

Test it by double-clicking it.

Then:

1. Press Win + R.
2. Type `taskschd.msc`.
3. Create Basic Task.
4. Name it `ProGuard Discord Bot`.
5. Trigger: `When I log on`.
6. Action: `Start a program`.
7. Select `start-bot.bat`.
8. Finish.

For a PC that stays logged in, this will start the bot whenever you sign into Windows.

# 8. Windows — simple startup folder option

Press Win + R and enter:

```text
shell:startup
```

Put a shortcut to `start-bot.bat` in that folder.

This starts the bot after you log into Windows.

# 9. Linux — systemd service

Create:

```text
proguard.service
```

Example:

```ini
[Unit]
Description=ProGuard Discord Bot
After=network-online.target
Wants=network-online.target

[Service]
Type=simple
User=YOUR_LINUX_USERNAME
WorkingDirectory=/home/YOUR_LINUX_USERNAME/pro-discord-bot
ExecStart=/usr/bin/node /home/YOUR_LINUX_USERNAME/pro-discord-bot/src/index.js
Restart=always
RestartSec=5
Environment=NODE_ENV=production

[Install]
WantedBy=multi-user.target
```

Install it:

```bash
sudo cp proguard.service /etc/systemd/system/proguard.service
sudo systemctl daemon-reload
sudo systemctl enable proguard
sudo systemctl start proguard
```

Check it:

```bash
sudo systemctl status proguard
```

Live logs:

```bash
journalctl -u proguard -f
```

Stop:

```bash
sudo systemctl stop proguard
```

Restart:

```bash
sudo systemctl restart proguard
```

# 10. Important Discord permissions

The bot's role must be ABOVE roles it needs to manage.

For example, if the bot needs to assign `Moderator`, the bot's role must be above `Moderator`.

The bot cannot moderate the server owner, and it cannot manage members/roles above its own highest role. This is enforced both by Discord and by the bot.

# 11. What this bot is designed to cover

ProGuard is intended as an all-purpose server-management bot rather than only a moderation bot. It combines moderation, role/staff management, staff availability/LOA tracking, tickets, logging, announcements, embeds, polls, server information, utility tools and harmless entertainment.

It deliberately avoids destructive computer operations, malware, credential/token theft, mass-DM abuse, self-botting and intentionally destructive server nukes.

# 12. Updating

Stop the bot, update the files, then:

```cmd
npm install
npm run deploy
npm start
```

Linux:

```bash
npm install
npm run deploy
npm start
```

# 13. Security

Never upload `.env`.

If your token is ever exposed:
1. Open the Discord Developer Portal.
2. Reset the bot token.
3. Replace `DISCORD_TOKEN` in `.env`.
4. Restart the bot.

The bot stores configuration and warnings locally in `data/config.json`.
