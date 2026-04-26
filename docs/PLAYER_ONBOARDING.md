# Lorehold — Player Onboarding

Lorehold lets us share live-collaborative notes between our Obsidian vaults. The DM hosts everything on his home server. You'll see his shared notes appear in your vault, and edits go both ways (when you have write permission).

## What you need from the DM

Before starting, the DM will give you:

1. **A PocketBase email + password** — your login for the control server.
2. **A server URL** — looks like `http://<some-ip>:8090`. This is the DM's home server as it appears on the shared Tailscale network.
3. **A Tailscale invite** — so your machine can reach the home server. The DM shares his node with you; accept the invite from `https://login.tailscale.com/admin/machines/shared`.
4. **A share key** — a long string like `relay-XXXX...`. You'll paste this into the plugin to join the campaign.

The plugin itself you'll install yourself in the next steps. You **do not** need a GitHub account.

## Install the plugin via BRAT

The Lorehold plugin isn't in Obsidian's community plugin store, so we use [BRAT](https://github.com/TfTHacker/obsidian42-brat) (Beta Reviewers Auto-update Tool) to install and auto-update it from a public GitHub repo. BRAT itself **is** in the community store and is widely trusted.

1. **Enable community plugins**: Open Obsidian → Settings → Community plugins. If you see a "Restricted mode" toggle, turn it off.
2. **Install BRAT**: Click **Browse** in the Community plugins page, search for **"BRAT"**, click **Install**, then **Enable**.
3. **Add the Lorehold plugin** via BRAT:
   - Open the command palette (`Cmd/Ctrl+P`).
   - Run **"BRAT: Add a beta plugin for testing"**.
   - Paste this URL: `https://github.com/tlyon3/lorehold-plugin`
   - Click **Add Plugin**. BRAT downloads the latest release.
4. **Enable Lorehold**: Settings → Community plugins → Installed plugins → toggle **Lorehold** on.

Updates land automatically: BRAT checks for new releases on Obsidian startup (and ~every 30 min while running). When the DM ships a fix, you'll see a notification and the plugin reloads itself.

## Log in

1. Open the command palette (`Cmd/Ctrl+P`) and run **"Lorehold: Log in with email + password"**.
2. **Server URL** — paste the URL the DM gave you. Make sure Tailscale is running first; this URL only works inside the DM's tailnet.
3. **Email + password** — paste what the DM gave you.
4. Click **Log in**. The plugin's settings page will open.

## Join the campaign

1. In the plugin settings (Settings → Community plugins → Lorehold → ⚙ icon), find the **"Join a Relay Server"** card.
2. Paste the **share key** the DM gave you. Click **Join**.
3. The campaign appears in your Relay Servers list. Click it to open the manage view.

## Add the shared folder to your vault

1. In the manage view for the campaign, click **"Add remote folder"**.
2. Pick the folder name the DM shared (e.g. "Session Notes").
3. **Local path** — choose where in *your* vault to put it. You can pick any path; it doesn't have to match the DM's. A common choice is `Campaign/Session Notes`.
4. Click **Confirm**. Files start materializing in that folder.

You should see notes appear within seconds. If the DM types in a shared note while you're watching, you'll see edits live.

## Day-to-day

- **Editing**: Just edit the notes like any other Obsidian note. Edits go up to the server in real time.
- **Read-only folders**: If a folder was shared as Reader, you can view but not edit. Trying to edit will revert.
- **Offline**: Edit offline; your changes sync when you reconnect.
- **Images / attachments**: Attachments embedded in shared notes are uploaded automatically. They lazy-load on your side.
- **Plugin updates**: Handled by BRAT — no action needed. If you want to manually check, run **"BRAT: Check for updates to all beta plugins"** from the command palette.

## Troubleshooting

- **"Failed to connect"** — Tailscale may be down. Check menu-bar icon. If Tailscale is fine, the DM's home server might be down — message him.
- **Login form won't open / errors on login** — toggle the plugin off then on (Settings → Community plugins → Lorehold). This forces a fresh load.
- **Notes aren't appearing** — make sure you accepted the Tailscale invite *and* the server URL is correct (no typo). The plugin connects to both PocketBase (port 8090) and a relay server (port 8082) — both need to reach the home server.
- **BRAT didn't fetch the plugin** — open BRAT's settings (Settings → Community plugins → BRAT → ⚙) and check that `tlyon3/lorehold-plugin` is in the Beta Plugin List. If not, re-run "BRAT: Add a beta plugin for testing".
- **Anything else** — paste the error from `Cmd+Opt+I` → Console tab to the DM.

## Privacy notes

- The DM's home server sees all shared content. He's the host, so he can read everything. Don't put anything in shared folders you wouldn't share with him.
- Notes outside your shared folders stay local to your vault — never uploaded.
- Player-to-player private notes (e.g. for secrets between just two players + DM) get a separate shared folder per pairing — ask the DM to set one up if needed.
