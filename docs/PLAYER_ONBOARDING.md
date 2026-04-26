# Lorehold — Player Onboarding

Lorehold lets us share live-collaborative notes between our Obsidian vaults. The DM hosts everything on his home server. You'll see his shared notes appear in your vault, and edits go both ways (when you have write permission).

## What you need from the DM

Before starting, the DM will give you:

1. **`lorehold-plugin.zip`** — the plugin itself.
2. **A PocketBase email + password** — your login for the control server.
3. **A server URL** — looks like `http://<some-ip>:8090`. This is the DM's home server as it appears on the shared Tailscale network.
4. **A Tailscale invite** — so your machine can reach the home server. The DM shares his node with you; accept the invite from `https://login.tailscale.com/admin/machines/shared`.
5. **A share key** — a long string like `relay-XXXX...`. You'll paste this into the plugin to join the campaign.

## Install the plugin

1. **Unzip** `lorehold-plugin.zip`. You'll get a folder called `lorehold/` containing `main.js`, `manifest.json`, `styles.css`.
2. **Find your vault folder** in Finder/Explorer. Inside it is a hidden folder called `.obsidian/`. Inside that, a `plugins/` folder.
   - macOS: show hidden files with `Cmd+Shift+.`
   - Windows: enable "Hidden items" in File Explorer's View menu
3. **Copy the `lorehold/` folder** into `<your vault>/.obsidian/plugins/`. Final path should be `<your vault>/.obsidian/plugins/lorehold/main.js`.
4. **Restart Obsidian** (or reload via the command palette: `Cmd/Ctrl+P` → "Reload app without saving").
5. **Enable the plugin**: Settings → Community plugins → Installed plugins → toggle **Lorehold** on. If "Community plugins" is off ("Restricted mode"), turn it on first.

## Log in

1. **Open the command palette** (`Cmd/Ctrl+P`) and run **"Lorehold: Log in with email + password"**.
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

## Troubleshooting

- **"Failed to connect"** — Tailscale may be down. Check menu-bar icon. If Tailscale is fine, the DM's home server might be down — message him.
- **Login form won't open / errors on login** — toggle the plugin off then on (Settings → Community plugins → Lorehold). This forces a fresh load.
- **Notes aren't appearing** — make sure you accepted the Tailscale invite *and* the server URL is correct (no typo). The plugin connects to both PocketBase (port 8090) and a relay server (port 8082) — both need to reach skybreaker.
- **Anything else** — paste the error from `Cmd+Opt+I` → Console tab to the DM.

## Privacy notes

- The DM's home server sees all shared content. He's the host, so he can read everything. Don't put anything in shared folders you wouldn't share with him.
- Notes outside your shared folders stay local to your vault — never uploaded.
- Player-to-player private notes (e.g. for secrets between just two players + DM) get a separate shared folder per pairing — ask the DM to set one up if needed.
