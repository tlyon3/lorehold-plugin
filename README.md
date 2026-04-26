# lorehold-plugin

Obsidian plugin for [Lorehold](https://github.com/tlyon3/lorehold-server) —
self-hosted CRDT note collaboration designed for small trusted groups (e.g. a
tabletop RPG party).

This is a hard fork of [Relay](https://github.com/NoInstructionsLLC/Relay)
(MIT, No Instructions LLC), patched to talk to a self-hosted PocketBase +
relay-server stack instead of Relay's hosted service. Server URL is
configurable per-vault, and login uses PocketBase password auth.

## Install

This plugin is **not** in Obsidian's community plugin store. Install via
[BRAT](https://github.com/TfTHacker/obsidian42-brat):

1. Install BRAT from Obsidian's community plugin store and enable it.
2. Open the command palette → **"BRAT: Add a beta plugin for testing"**.
3. Paste this repository's URL: `https://github.com/tlyon3/lorehold-plugin`.
4. Confirm — BRAT downloads the latest release and installs.
5. Enable **Lorehold** in Settings → Community plugins.
6. BRAT auto-checks for updates on Obsidian startup. New releases land
   automatically.

For player onboarding (server URL, login, joining a campaign), see
[`docs/PLAYER_ONBOARDING.md`](docs/PLAYER_ONBOARDING.md).

## Build from source

```bash
npm install
npm run release         # produces main.js
```

Output files for an Obsidian install: `main.js`, `manifest.json`, `styles.css`.

## Release process (maintainer)

1. Edit source in `src/`.
2. Bump version in `manifest.json` (semver).
3. Commit and tag: `git tag X.Y.Z && git push origin main && git push origin X.Y.Z`.
4. The release GitHub Action builds and publishes a Release with `main.js`,
   `manifest.json`, `styles.css` attached.
5. Players' BRAT picks up the new release within ~30 minutes.

## License

MIT. See [`LICENSE`](LICENSE) — chained attribution between Lorehold (Trevor
Lyon) and the upstream Relay plugin (No Instructions LLC).
