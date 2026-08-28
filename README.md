# Day Trade Bot — umbrelOS community app store

Community app store for [umbrelOS](https://umbrel.com), packaging an automated
day-trading bot that runs against the Interactive Brokers API.

Add it in umbrelOS under **App Store → ⋯ → Community App Stores**:

```
https://github.com/Drumblow/umbrel-daytradebot-store
```

## Apps

| App | Status |
|---|---|
| `daytradebot-probe` | temporary — validates umbrelOS packaging assumptions, will be removed |
| `daytradebot` | not published yet |

## This repository is public and must never contain a secret

The bot authenticates with a **personal Interactive Brokers account**. Anything
committed here is world-readable, forever, including in the git history.

Rules, no exceptions:

- **No credentials.** No IBKR username or password, no `ibc.ini`, no account
  numbers, no database passwords, no API keys.
- **No addresses.** No LAN IPs, no hostnames of the machine running this.
- **Secrets come from the host at runtime**, never from this repo: either
  derived by umbrelOS (`${APP_SEED}`, `${APP_PASSWORD}`) or read from
  `${APP_DATA_DIR}/secrets/`, which lives only on the user's own device.
- **No redistribution of Interactive Brokers binaries.** The IB Gateway
  installer is downloaded at build time from IBKR, not vendored here.

Templates in this repo carry placeholders only. If a secret is ever committed,
rotating it is mandatory — deleting the commit is not enough, because the
history is already public.

## Related

The bot itself lives in a separate repository. This store only packages it.
