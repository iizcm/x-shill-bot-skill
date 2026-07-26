---
name: x-shill-bot
description: Automate posting or shilling to multiple X (Twitter) accounts on a schedule. Critical hard-won facts about X Free API being read-only and browser-cookie auth being required. Use when the user has several X accounts and wants scheduled shill posts, e.g. every 6 hours.
license: MIT
category: social-media
---

# X Shill Bot (multi-account)

Post to many X accounts automatically. The user has 7 accounts and wants 6h cadence.

## HARD FACTS (cost real debugging time)
- **X API Free tier = READ ONLY.** tweepy.Client.create_tweet (v2, OAuth1.0a user context) returns 401 Unauthorized even after setting app Permissions to "Read and Write" in the developer portal. Write access requires Basic ($100/mo). Do NOT burn time retrying API write, it will not work on Free.
- **Bot login via user/pass FAILS.** Playwright login reaches X then gets stuck at onboarding knowledge-check quiz URL. The bot cannot pass it, so the user must finish onboarding manually OR provide cookies.
- **Use cookie auth, not password.** Scrape auth_token + ct0 from the browser (DevTools, Application, Cookies) AFTER the user logs in manually. Store in /root/x_keys.txt (PRIVATE, never in memory, never public repo).
- **Cloud/VPS IPs get flagged by X.** For bot posting, route each account through a residential proxy (per-account) or X will shadowban or lock. Do not run X automation directly from the VPS datacenter IP.
- **Free tier rate limit:** ~1500 tweets/month total, 17 tweets/24h per account. Fine for 7 accounts shilling every 6h (4/day x 7 = 28/day, under limit).

## Approach (when user provides cookies)
1. x_post_browser.py: launch Playwright chromium with auth_token + ct0 cookies, navigate to x.com, post the shill text, verify tweet appears.
2. Schedule via cron every 6h (one post per account, or rotate accounts).
3. Keep a template bank of shill texts (vary per post to avoid spam detection).

## Gotchas
- Cookies expire, script must detect "login required" and alert the user to re-scrape.
- Never paste the user's X password or cookies into chat or memory.
- Onboarding must be completed by the user once per account before cookies work.
