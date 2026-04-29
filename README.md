# DNS Blocklists – NichtTube

[![License: MIT](https://img.shields.io/github/license/NichtTube/DNS_Blocklists_NichtTube?style=flat-square)](LICENSE)
[![Latest Release](https://img.shields.io/github/v/release/NichtTube/DNS_Blocklists_NichtTube?style=flat-square)](https://github.com/NichtTube/DNS_Blocklists_NichtTube/releases)
[![Last Commit](https://img.shields.io/github/last-commit/NichtTube/DNS_Blocklists_NichtTube?style=flat-square)](https://github.com/NichtTube/DNS_Blocklists_NichtTube/commits/main)
[![Repo Size](https://img.shields.io/github/repo-size/NichtTube/DNS_Blocklists_NichtTube?style=flat-square)](#)
[![jsDelivr Hits](https://img.shields.io/jsdelivr/gh/hm/NichtTube/DNS_Blocklists_NichtTube?style=flat-square&label=jsDelivr%20hits)](https://www.jsdelivr.com/package/gh/NichtTube/DNS_Blocklists_NichtTube)
[![Stars](https://img.shields.io/github/stars/NichtTube/DNS_Blocklists_NichtTube?style=flat-square)](https://github.com/NichtTube/DNS_Blocklists_NichtTube/stargazers)
[![Issues](https://img.shields.io/github/issues/NichtTube/DNS_Blocklists_NichtTube?style=flat-square)](https://github.com/NichtTube/DNS_Blocklists_NichtTube/issues)
[![Version](https://img.shields.io/badge/dynamic/regex?url=https%3A%2F%2Fraw.githubusercontent.com%2FNichtTube%2FDNS_Blocklists_NichtTube%2Fmain%2FVERSION&search=([0-9.]+)&label=version&style=flat-square)](./VERSION)

Custom DNS blocklists in AdGuard filter syntax for use with **AdGuard Home** and **AdGuard DNS**.

## Available Lists

| List | Purpose |
|---|---|
| [`meta_quest_pro_dns_blocklist.txt`](./meta_quest_pro_dns_blocklist.txt) | Blocks Meta Quest Pro OTA update check endpoints. Prevents automatic firmware updates without breaking login, store, pairing, or social features. |
| [`vrchat_allowlist.txt`](./vrchat_allowlist.txt) | Whitelist for VRChat (core API, Photon networking, Unity, trusted media hosts). Override for aggressive blocklists that break VRChat connectivity. |

## Subscription URLs

Pick one channel and use it consistently in your DNS resolver. Replace `<list>` with the filename (e.g. `meta_quest_pro_dns_blocklist`).

| Channel | URL pattern | When to use |
|---|---|---|
| **Latest (rolling)** | `https://raw.githubusercontent.com/NichtTube/DNS_Blocklists_NichtTube/main/<list>.txt` | Always tracks `main`. Auto-updates with every commit. |
| **Latest via CDN** | `https://cdn.jsdelivr.net/gh/NichtTube/DNS_Blocklists_NichtTube@latest/<list>.txt` | Same as above, served via jsDelivr. Faster + globally cached. |
| **Pinned version** | `https://cdn.jsdelivr.net/gh/NichtTube/DNS_Blocklists_NichtTube@<tag>/<list>.txt` | Locks to a specific release tag (see [Releases](https://github.com/NichtTube/DNS_Blocklists_NichtTube/releases/latest)). No surprise changes. |
| **Pinned commit** | `https://cdn.jsdelivr.net/gh/NichtTube/DNS_Blocklists_NichtTube@<sha>/<list>.txt` | Locks to an exact commit. Maximum reproducibility. |

> Recommended for production: pinned version. Recommended for "set and forget": `@latest` via jsDelivr.

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

> ⚠️ When applied at network level, scope the list to the Quest device only (per-client / per-profile assignment). Some endpoints are shared with other Meta services.

## Format
AdGuard filter syntax: `||domain^` rules, `!` header comments, `#` section comments. Compatible with AdGuard Home, AdGuard DNS, the AdGuard browser extension, and Pi-hole when the AdBlock Plus parser is enabled.

## Versioning

This repo follows [SemVer](https://semver.org/) via Git tags (`vX.Y.Z`). Each release is published under [Releases](https://github.com/NichtTube/DNS_Blocklists_NichtTube/releases). The `! Version:` and `! Last modified:` headers inside each `.txt` file are kept in sync automatically by a GitHub Action on every push.

- **MAJOR** – breaking changes (list renamed/removed, format change)
- **MINOR** – new lists or significant rule additions
- **PATCH** – rule additions/removals/fixes within an existing list

## Notes
- **Meta Quest Pro list** intentionally blocks update traffic. Future features that strictly require online verification against Meta servers may stop working. Use at your own risk.
- Some Quest firmware versions use hardcoded DoH resolvers and can bypass DNS-level blocking. If updates still arrive, also block outbound port 853 (DoT) and route Cloudflare/Google DNS IPs through your own resolver.
- Issues / PRs for additions or false positives are welcome.

## License
[MIT](LICENSE) © NichtTube
