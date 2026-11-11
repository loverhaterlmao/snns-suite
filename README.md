<div align="center">

<a href="https://snns.dev"><img src="./banner.svg" alt="S&NS Suite: Every Sick & Nexra Studios project, in one place" width="100%"></a>

<p>
<a href="https://snns.dev"><img alt="open: snns.dev" src="https://img.shields.io/badge/open-snns.dev-f2484f?style=for-the-badge&labelColor=12161b"></a>
<img alt="access: by invitation" src="https://img.shields.io/badge/access-by%20invitation-232a2f?style=for-the-badge&labelColor=12161b">
<a href="./LICENSE"><img alt="source: closed" src="https://img.shields.io/badge/source-closed-232a2f?style=for-the-badge&labelColor=12161b"></a>
<a href="./SUPPORT.md"><img alt="support: a real person" src="https://img.shields.io/badge/support-a%20real%20person-232a2f?style=for-the-badge&labelColor=12161b"></a>
</p>

<p><a href="https://snns.dev"><b>Website</b></a> &nbsp;·&nbsp; <a href="./ACCESS.md"><b>Get in</b></a> &nbsp;·&nbsp; <a href="./TUTORIALS.md"><b>First hour</b></a> &nbsp;·&nbsp; <a href="./API.md"><b>API</b></a> &nbsp;·&nbsp; <a href="./PRICING.md"><b>Pricing</b></a> &nbsp;·&nbsp; <a href="./SUPPORT.md"><b>Support</b></a></p>

</div>

<br>

Sick & Nexra Studios (S&NS) makes a small family of tools. This page says what each one is, where to open it, and how
to get in. The source code of every project is closed; these repositories hold the guides, the terms and the place to
report problems.

| Project | What it is | Where |
|---|---|---|
| **Noetic Suite** | One AI assistant with a whole studio behind it. Ask in a sentence and get it finished: a game, a site, a document, a picture. Planned, built, run, reviewed and fixed before it reaches you. | [noetic.lol](https://noetic.lol) |
| **Claw** | Private code workspaces your AI can write to, with cloud sandboxes, real terminals, a built-in copilot and a command-line tool. Save a zip or commit to GitHub. | [sick.cat](https://sick.cat) |
| **Sykbot** | Discord server management: moderation, verification, anti-raid, tickets and logging, all set up inside Discord. | [sykbot.com](https://sykbot.com) · docs at [sickenn.info](https://sickenn.info) · account at [sicken.me](https://sicken.me) |
| **Beat.rip** | A username checker for 57 platforms and every popular domain, asked of each platform itself, with an honest "unknown" when one will not say. | [beat.rip](https://beat.rip) |
| **Ink** | A document editor that measures how text was written and says exactly what it measured. | [wrote.ink](https://wrote.ink) |

The studio's own page is [snns.dev](https://snns.dev).

## Who we are taking on right now

Noetic Suite is open **by invitation** while it is new. We are saying yes to:

- **small developers** and people making their first real project;
- people who **genuinely need the tool** for something they are trying to finish;
- people willing to **test it and tell us what broke**, plainly.

We are not taking bulk sign-ups, resellers, or accounts made to probe the service. If that sounds like a fit, apply on
the front page of [noetic.lol](https://noetic.lol): say who you are and what you would use it for. A person reads
every application. If it is a fit you get an invitation by email with a link to make your account.

## Getting in, step by step

1. **Apply** at [noetic.lol](https://noetic.lol) (the form at the foot of the page).
2. **Wait for the invitation.** It is tied to the email address you applied with and is good for two weeks.
3. **Make your account** from the link. Use a password of ten characters or more, or, if your invitation address is
   your GitHub or Google address, use "Continue with GitHub" or "Continue with Google" once those are switched on.
4. **Secure it** (user menu → *Sign-in and security*): add an authenticator app or a passkey.
5. **Start.** [TUTORIALS.md](TUTORIALS.md) walks through the first hour.

## The desktop app (Windows)

People with an account can download Noetic Suite for Windows. The download is behind your sign-in on purpose:

- sign in at [noetic.lol](https://noetic.lol), then open **user menu → Get the desktop app**, or go to
  `https://noetic.lol/download`;
- check the file against the SHA-256 shown on that page before you run it;
- unzip it anywhere and open `NoeticSuite.exe`. Windows will warn that the publisher is unknown, because the build is
  not code-signed yet.

Please do not pass the file on. People who want it can apply.

## In this repository

| File | What is in it |
|---|---|
| [ACCESS.md](ACCESS.md) | Who gets in, how applications are judged, what an account can and cannot do |
| [TUTORIALS.md](TUTORIALS.md) | First steps in Noetic: chat, building, pictures, projects, security, support |
| [API.md](API.md) | Calling Noetic from your own programs: keys, examples, errors, limits |
| [PRICING.md](PRICING.md) | Plans, seats, pay-as-you-go credit and what paying changes |
| [FAQ.md](FAQ.md) | The questions people ask first |
| [ROADMAP.md](ROADMAP.md) | What is being worked on |
| [CHANGELOG.md](CHANGELOG.md) | What changed, and when |
| [SECURITY.md](SECURITY.md) | How to report a weakness, what is in scope, what we will not chase you for |
| [SUPPORT.md](SUPPORT.md) | How to reach a person |
| [LEGAL.md](LEGAL.md) | Terms of use, acceptable use, privacy, testing terms, intellectual property |

## Support

Write to **support@snns.dev**, use the form at [noetic.lol/support](https://noetic.lol/support), or, inside Noetic,
**user menu → Contact support**. Problems with these guides can be opened as issues here. Do not put passwords,
keys or personal details in an issue.

## The API in one breath

```bash
curl https://noetic.lol/v1/chat/completions \
  -H "Authorization: Bearer $NOETIC_KEY" -H "Content-Type: application/json" \
  -d '{"model":"noetic-0.1","messages":[{"role":"user","content":"Hello"}]}'
```

Keys are made inside Noetic. Everything else is in [API.md](API.md).

<br>

<div align="center">

<sub>Part of the S&NS family</sub><br>
<a href="https://github.com/loverhaterlmao/noetic-suite"><b>Noetic Suite</b></a> &nbsp;·&nbsp; <a href="https://github.com/loverhaterlmao/claw"><b>Claw</b></a> &nbsp;·&nbsp; <a href="https://github.com/loverhaterlmao/sykbot"><b>Sykbot</b></a> &nbsp;·&nbsp; <a href="https://github.com/loverhaterlmao/beat-rip"><b>Beat.rip</b></a> &nbsp;·&nbsp; <a href="https://github.com/loverhaterlmao/ink"><b>Ink</b></a><br><br>
<a href="https://snns.dev"><b>snns.dev</b></a> &nbsp;·&nbsp; <a href="https://github.com/loverhaterlmao/snns-suite">S&NS Suite</a> &nbsp;·&nbsp; <a href="mailto:support@snns.dev">support@snns.dev</a>

<sub>© Sick & Nexra Studios. All rights reserved. No licence to the software is granted by this repository.</sub>

</div>
