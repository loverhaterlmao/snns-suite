# API

## The short answer

**There is no public API for Noetic Suite yet.** Everything an account does goes through the app at
[noetic.lol](https://noetic.lol) or the Windows app. This page documents what *can* be called from outside today, so
nobody has to guess, and says what will not work.

## What is open to anyone

All of these are on `https://noetic.lol`.

| Method and path | What it does | Notes |
|---|---|---|
| `GET /` | The front page | Carries link-preview tags and structured data (schema.org `SoftwareApplication`) |
| `GET /robots.txt` | Crawler rules | Lists the sitemap |
| `GET /sitemap.xml` | Sitemap | |
| `GET /support` | The contact page | |
| `POST /apply` | Apply to use Noetic | JSON: `name`, `email`, `org` (optional), `use` (at least a sentence). Limited to a few per hour per address |
| `POST /contact` | Write to support | JSON: `name`, `email`, `topic` (`support`, `bug`, `redteam` or `legal`), `subject`, `message`. Limited per address |

Both `POST` endpoints answer `200 {"ok":true}` or `400 {"error":"…"}` with a sentence a person can read. Visitors on
a VPN, proxy or hosting network may be asked to pass a person check first; the form on the site handles that, a bare
script will be refused.

### Example

```bash
curl -s https://noetic.lol/contact \
  -H 'Content-Type: application/json' \
  -d '{"name":"Pat","email":"pat@example.org","topic":"bug","subject":"Preview is blank","message":"The preview frame stays blank after a build on Firefox 131."}'
```

## What is not open

- Anything under `/api/`. Those calls need a signed-in session **and** a page token, change without notice, and are
  not a supported interface. Scripts written against them will break.
- Sign-in by script. Accounts sign in through the site, with a password, a quick sign-in, or a passkey.
- The desktop app's download address. It answers only to a signed-in account.

## Automated access

Do not crawl, scrape or load-test the service. Addresses that request paths which do not exist, or that flood, are
shut out automatically and reported. If you are testing security on purpose, read [SECURITY.md](SECURITY.md) first.

## What we intend to offer

A supported API for accounts, with keys you can make and revoke, is planned. It is not built. When it exists it will
be documented here first, with versioning and limits. If you have a concrete use for one, tell us at
support@snns.dev: that decides what gets built.

## The other S&NS projects

Each documents its own interface on its own site: [sick.cat](https://sick.cat) (the sick CLI and workspaces),
[sickenn.info](https://sickenn.info) (Sykbot), [beat.rip](https://beat.rip), [wrote.ink](https://wrote.ink).
