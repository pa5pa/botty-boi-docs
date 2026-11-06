# Botty Boi Privacy Policy

**Last updated: November 6, 2026**

Botty Boi is a private Discord bot for one gaming server, run by that server's owner as a hobby. It isn't a business or a public service. This page explains what it stores, why, who can see it, and how to have it removed.

**The short version:** the bot keeps only what it needs to run news, moderation and the streamer leaderboard. It doesn't sell your data, show ads or track you outside the server. It never asks for your passwords or stream keys, and you should never give them to it.

## What the bot stores

### Everyone in the server

| What | Why | How long it's kept |
|---|---|---|
| Commands you run: your Discord ID and username, the command, its options, the channel and the time. This includes commands the bot can see you run on other bots, such as Jockie Music. | So admins can see who did what | 30 days |
| Messages the bot removes under a server rule: your ID and username, the channel, and up to the first 120 characters | So admins can review moderation | 30 days |
| Role changes made through the roles channel | So admins can see changes | 30 days |
| While the streamer links channel is open for you: your Discord ID and when you last used it | To close it automatically | Deleted when it closes, normally within about 30 minutes |
| News votes, if your votes count: your Discord ID, the story, your vote and the time | To learn which news sources are useful | 30 days with your ID. After that, the vote stays without your ID. |

These entries are also posted to private log channels in the server. The bot deletes its log posts and database entries once they're past 30 days. The cleanup runs nightly, so an entry can last a little longer, and it also remains in backups until they're replaced.

**Reading messages.** The bot can read messages in the channels it has access to, because it needs to spot commands and apply server rules. It checks each message and moves on. It doesn't keep an archive of conversations.

### If you link a streaming channel

This only applies if you link a channel, or an admin links one for you.

| What | Why | How long it's kept |
|---|---|---|
| Your Discord ID, display name, linked Twitch, Kick or YouTube channel, and any nicknames you add | To know whose stream is whose | Until you remove it |
| Each stream: start and end time, title, peak viewers, and people named in the title or description as streaming with you | Leaderboard stats and collab tracking | Up to about 800 days |
| Regular checks during a stream: viewer count, game, and whether a title and game were set | Leaderboard stats | Up to about 200 days |
| Weekly and quarterly results: your place, points and hours | Past winners | Until you remove them |

People named this way may not be in the server. The bot keeps only the name as written in the public title or description, and how often it came up. Anyone named can ask the server owner to remove it.

All of this is public information from those platforms. The bot only looks up public stream details. It can't sign in to your account, post for you, or see anything private.

**What others can see:** leaderboard channels show your Discord name, hours, viewer numbers, games and collabs to anyone with access to those channels. While you're live, you may get the Live Now role, which anyone in the server can see. Moderators and admins can see which platforms you've linked. Only admins, the bot and anyone given access to the private log channels can see which channel you linked.

## What the bot doesn't collect

- Passwords, stream keys or account logins
- Your online status or what you're playing on Discord
- Voice chat or anything said in voice channels
- Your email address, payment details or location

## Who can see it

- The server owner, who runs the PC the bot lives on
- Server admins and anyone given access to the private log channels
- Moderators, who can read recent log lines with linked channel names hidden
- The people listed under "What others can see" above, for leaderboard information

## Other services

- **Discord** carries everything the bot does, under [Discord's Privacy Policy](https://discord.com/privacy).
- **Twitch, Kick and YouTube** (Google): when these checks are turned on, the bot sends the linked channel name to the matching platform to ask whether that channel is live.
- **GitHub:** an off-site backup copy of the bot's database is kept in a private GitHub repository, so it can be restored if the PC fails. That copy includes the information described on this page, and GitHub stores it under [GitHub's Privacy Statement](https://docs.github.com/site-policy/privacy-policies/github-general-privacy-statement).
- **News sites:** the bot reads public news feeds. No information about you is sent to them.
- **Google Gemini (AI reading of streams):** when turned on, the bot sends the public title and description of a live stream to Google to work out who's named and which game is being played. It doesn't send your Discord name or ID, your nicknames or which channel is yours, but the title or description may name people. The bot uses Google's free service, so Google may use this text to improve its products and its human reviewers may read it.
- **Anthropic (AI summaries):** currently **off**. This policy will be updated before it's ever turned on, because it would send news text to Anthropic.

Your information is never sold or shared for advertising.

## Where it's stored

Information is stored in a file on one PC controlled by the server owner, along with a technical log and up to 14 nightly backups. One backup copy of the database is also kept in the server owner's private GitHub repository. Access is limited to the owner of that PC and that GitHub account, but no system is perfectly secure.

## Your choices

- **Remove your streamer data:** run `/streamer leave`. This deletes your links, stream history, stats and past results straight away.
- **Remove one platform:** run `/streamer unlink`. Your past stats stay until you use `/streamer leave`.
- **Drop a role:** remove your reaction in the roles channel.
- **Anything else:** ask the server owner on Discord to show you or delete what's stored about you, including votes and log entries.

**What `/streamer leave` doesn't reach straight away:** older backups on the PC, which are replaced within about 14 days; the GitHub backup copy, which is normally replaced every night; log entries, which expire after 30 days; and leaderboard posts already made in Discord channels, which the server owner can remove if you ask.

## Age

Discord requires users to be at least 13, or older where local law says so. The bot isn't intended for anyone below that age.

## Changes

If this policy changes, the date at the top will change too, and this link will always show the current version. Significant changes will be announced in the server.

## Questions

Message the server owner on Discord.
