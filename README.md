# Botty Boi

A private Discord bot for one gaming server. It collects game news, tracks friends' streams on a leaderboard, hands out roles, and keeps the server tidy. It runs around the clock on a dedicated Windows PC.

It isn't a public bot and only stays in its own server. See the [Privacy Policy](PRIVACY.md) and [Terms of Service](TERMS.md).

## Features

| Feature | What it does |
|---|---|
| **News** | Checks about 40 sources. Official game feeds are checked every 3 hours and everything else every 10–30 minutes. It merges duplicate stories. |
| **News channels** | Every article goes to the firehose, the best stories get their own posts, and a digest covers each 3-hour block. |
| **News voting** | Admins and trusted voters rate posts with reactions, which adjusts source scores. The bot removes each reaction once it's counted, so votes aren't on show. |
| **Streamer leaderboard** | Tracks Twitch, Kick and YouTube: daily recap, weekly top 5, quarterly top 3 and a live standings message. |
| **Joint stream** | Lets a hand-picked list of people control the shared stream's OBS from Discord, shows everyone's channel links, and keeps a weekly stats post for the joint channel. |
| **Live Now** | A role that lists people in their own group in the member list while they stream. |
| **Roles** | People react in the roles channel to open the channels they want. |
| **Cleanup** | Deletes messages by rule and keeps commands in the right channel. Pinned messages are never removed. |
| **Logs** | Private channels record commands, moderation, news decisions and system events. |
| **Health** | Hourly PC status, warnings when the PC is struggling, nightly backups, and a weekly PC restart. |

## Using the bot

### Everyone

| Command | What it does |
|---|---|
| `/ping` | Checks the bot is awake |
| `/leaderboard` | Shows standings, today, yesterday, this week, this quarter or past winners |
| `/streamer profile` | Shows streamer stats for the last 30 days |
| `/links` | Channel links for everyone on the joint stream, or one person with `/links streamer:` |

**To pick roles:** react in the roles channel, and remove the reaction to drop the role.

**Music:** use `m!` commands in the music channel or any voice channel's text chat. Requests are removed automatically to keep things tidy.

### Streamers

| Command | What it does |
|---|---|
| `/streamer open` | Opens the private links channel so you can paste links |
| `/streamer link` | Links a channel from anywhere. Only you see the reply. |
| `/streamer unlink` | Removes one platform and keeps your stats |
| `/streamer aliases` | Adds other names people use for you, so naming you counts as a collab with you and your own name doesn't count as one |
| `/streamer leave` or `/streamer remove` | Deletes all your streamer data |

You can also paste your channel link in the private links channel, which you open with 🎥 in the roles channel or `/streamer open`. The bot removes the message and keeps one DM up to date, with a green or red light for each platform and a button back to the channel. Press **That's it** and the channel disappears for you. It also closes by itself after 30 minutes with nothing new.

**All the bot needs from a streamer is the channel link. Never share a stream key or password.**

### Joint stream controllers

Only the people listed by user ID in `config.py` can use these. Being the owner, an admin or a moderator doesn't count on its own. Replies are private.

| Command | What it does |
|---|---|
| `/feature` | Shows one streamer |
| `/next` | Skips to the next streamer |
| `/hold on` / `/hold off` | Stops or resumes switching away from who's on now |
| `/squad` | Switches to the grid view |
| `/auto` | Goes back to normal automatic switching |
| `/jointstatus` | Shows whether OBS is connected and which scene is live |

The bot only sends a short message to OBS. OBS decides what to do with it.

### Moderators and up

Admins and the owner can use these too. Anyone else gets a "no permission" reply. Most are hidden from regular members' slash menus. Discord can't hide part of a group, so some options still show up in the list.

| Command | What it does |
|---|---|
| `/streamer list` | Shows who has linked which platforms, with a green or red light for each. No channel names. |
| `/streamer test` | Checks the platform keys and how many people are live |
| `/news` | `sources`, `test`, `testall`, `stats`, `overlap`: looks at news sources without changing them |
| `/audit` | `status`, `recent`: shows log channels and recent log lines, with linked channel names hidden |
| `/cleanup`, `/restrict` | Lists the delete rules and channel restrictions |
| `/maintenance` | Shows planned maintenance |

### Admins and up

Anyone with Discord's Administrator permission or a role listed in `config.py`, and the owner.

| Command | What it does |
|---|---|
| `/streamer add` | Links a channel for someone else |
| `/streamer remove` | Removes someone else from the leaderboard and deletes their data |
| `/streamer postnow` | Posts the daily recap now |
| `/news` | `toggle`, `settier`, `addsource`, `pollnow`: changes sources and checks them now |
| `/status`, `/pc` | Shows bot and PC health |

### Owner only

Being a Discord admin isn't enough for these.

| Command | What it does |
|---|---|
| `/restart`, `/shutdown` | Restarts or stops the bot, with a notice |
| `/pcrestart` | Cleans up, backs up, and restarts the whole PC |
| `/maintenance` | `schedule`, `cancel`, `setchannel` |
| `/sync`, `/backup` | Re-registers commands, backs up now |
| `/roles refresh` | Applies role changes from `config.py` |
| `/cleanup`, `/restrict` | `add`, `remove`: changes delete rules and channel restrictions |
| `/audit` | `setchannel`, `clearchannel` |
| `/news` | `setchannel`, `setfirehose`, `setdigest`, `digest` |
| `/streamer setchannel` | Picks where the leaderboard posts |

## Running the bot

### Starting and stopping

- **Automatic start:** the `GameBot` task in Windows Task Scheduler runs `start_bot.bat` when the PC boots, with no sign-in needed. It runs in the background with no window, so use `/pc` or `logs/bot.log` to check on it.
- **By hand:** double-click `start_bot.bat`. If the bot is already running, the new window just waits, so a second copy can't post everything twice.
- **Crashes:** `start_bot.bat` restarts the bot after 10 seconds.
- **Turning it off:** use `/shutdown`. It stays off until started again.

### What runs automatically

| When | What |
|---|---|
| Every night at 4 AM (PC time) | Backup on the PC and to a private GitHub repository, cleanup of old records, and removal of log posts older than 30 days |
| About once a week at 4 AM | Cleanup and backup, then a PC restart. Announced 1 hour ahead, and due once the PC has been on for 7 days. |
| Hourly | PC status posted in the system log |

To cancel a PC restart during its 30-second countdown, run `shutdown /a` on the PC.

### Settings

- **`config.py`** holds all settings, the bot token and the keys.
- **The dashboard** edits delete rules, restrictions, news sources and shows feedback. Double-click `start_dashboard.bat`, then open <http://localhost:8080> on the bot's PC. Enter the dashboard password when asked; the username can be anything.

Restart the bot after editing `config.py`.

### Where things are

| Path | What it is |
|---|---|
| `data/bot.db` | The bot's database |
| `backups/` | Nightly database backups, 14 kept |
| `logs/bot.log` | Technical log, the first place to look when something's wrong |
| `sources.json` | The list of news sources |

## New install

In short:

1. Install Python 3.12 and run `install.bat`.
2. Create the bot in the [Discord Developer Portal](https://discord.com/developers/applications) and turn on the Server Members and Message Content intents.
3. Fill in `config.py`.
4. Run `start_bot.bat`.

The leaderboard needs one set of free developer credentials per platform you use, all owned by the bot's operator: a Client ID and Secret for Twitch and Kick, and an API key for YouTube.

## Project layout

| File | What it does |
|---|---|
| `bot.py` | Starts the bot and loads its features |
| `cogs/admin.py` | Owner tools, maintenance, backups and restarts |
| `cogs/auditlog.py` | Log channels |
| `cogs/jointstream.py` | Joint stream controls for OBS, and `/links` |
| `cogs/cleanup.py` | Delete rules and channel restrictions |
| `cogs/news.py` | News collection, posting, digest and votes |
| `cogs/pcstatus.py` | PC and bot health |
| `cogs/roles.py` | Roles message, Live Now role and the streamer area |
| `cogs/streamers.py` | Leaderboard and live tracking |
| `offsite.py` | Nightly off-site backup to GitHub |
| `dashboard.py` | Local settings page |

Built with Python, discord.py, SQLite, feedparser, BeautifulSoup, Playwright and Flask.

## Security

- **Never share `config.py`, `data/`, `backups/` or `logs/`, or put them anywhere public.** They hold the bot token and people's activity. `.gitignore` keeps them out of normal Git uploads, but not out of files uploaded by hand on GitHub's website.
- If the token ever leaks, reset it right away in the Developer Portal, on the Bot page.
- The dashboard only accepts connections from the bot's PC. Keep it that way.
- Keep **Public Bot** turned off in the Developer Portal. As a backstop, the bot leaves any server other than the one set in `SERVER_ID`.
