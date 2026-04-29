# DNS Blocklists – NichtTube

[![License: MIT](https://img.shields.io/github/license/NichtTube/DNS_Blocklists_NichtTube?style=flat-square)](LICENSE)
[![Last Commit](https://img.shields.io/github/last-commit/NichtTube/DNS_Blocklists_NichtTube?style=flat-square)](https://github.com/NichtTube/DNS_Blocklists_NichtTube/commits/main)
[![Latest Release](https://img.shields.io/github/v/release/NichtTube/DNS_Blocklists_NichtTube?style=flat-square)](https://github.com/NichtTube/DNS_Blocklists_NichtTube/releases)
[![Stars](https://img.shields.io/github/stars/NichtTube/DNS_Blocklists_NichtTube?style=flat-square)](https://github.com/NichtTube/DNS_Blocklists_NichtTube/stargazers)
[![Issues](https://img.shields.io/github/issues/NichtTube/DNS_Blocklists_NichtTube?style=flat-square)](https://github.com/NichtTube/DNS_Blocklists_NichtTube/issues)

Custom DNS blocklists in AdGuard filter syntax for use with **AdGuard Home** and **AdGuard DNS**.

## Available Lists

| List | Purpose | Rules |
|---|---|---|
| `meta_quest_pro_dns_blocklist.txt` | Blocks Meta / Oculus / Facebook endpoints to suppress OTA updates and telemetry on the Meta Quest Pro | 16 |

## Subscription URLs

Pick one channel and use it consistently in your DNS resolver.

| Channel | URL pattern | When to use |
|---|---|---|
| **Latest (rolling)** | `https://raw.githubusercontent.com/NichtTube/DNS_Blocklists_NichtTube/main/<list>.txt` | Always tracks `main`. Auto-updates with every commit. |
| **Latest via CDN** | `https://cdn.jsdelivr.net/gh/NichtTube/DNS_Blocklists_NichtTube@latest/<list>.txt` | Same as above, served via jsDelivr. Faster + cached. |
| **Pinned version** | `https://cdn.jsdelivr.net/gh/NichtTube/DNS_Blocklists_NichtTube@v1.0.0/<list>.txt` | Locks to a specific release tag. No surprise changes. |
| **Pinned commit** | `https://cdn.jsdelivr.net/gh/NichtTube/DNS_Blocklists_NichtTube@<sha>/<list>.txt` | Locks to an exact commit. Maximum reproducibility. |

> Recommended for production: pinned version (`@vX.Y.Z`). Recommended for "set and forget": `@latest` via jsDelivr.

## How to Add

### AdGuard Home
1. Web UI → **Filters** → **DNS blocklists** → **Add blocklist** → **Add a custom list**
2. Name: e.g. `NichtTube – Meta Quest Pro`
3. URL: any subscription URL from the table above
4. **Save** — list is fetched on the next refresh interval

### AdGuard DNS (Cloud)
1. Dashboard → select profile → **Blocklists** → **Custom blocklists** → **Add blocklist**
2. Enter name + URL
3. **Save**

## Format
AdGuard filter syntax: `||domain` rules, `!` header comments, `#` section comments. Compatible with AdGuard Home, AdGuard DNS, the AdGuard browser extension, and Pi-hole when the AdBlock Plus parser is enabled.

## Versioning

This repo follows [SemVer](https://semver.org/) via Git tags:

- **MAJOR** – breaking changes (list renamed/removed, format change)
- **MINOR** – new lists or significant additions of rules
- **PATCH** – rule additions/removals/fixes within an existing list

Each release is tagged (`vX.Y.Z`) and listed under [Releases](https://github.com/NichtTube/DNS_Blocklists_NichtTube/releases). The `Version:` header inside each `.txt` file mirrors the repo tag at release time.

## Notes
- Lists are maintained manually — no CI/automated build.
- **Meta Quest Pro list** intentionally breaks update and tracking traffic. Future features that strictly require online verification against Meta servers may stop working. Use at your own risk.
- Issues / PRs for additions or false positives are welcome.

## License
[MIT](LICENSE) © NichtTube
