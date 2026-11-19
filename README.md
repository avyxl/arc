# Solcord 2.1.0

Maintained by [avyxl](https://avyxl.github.io/portfolio/). [Project website](https://avyxl.github.io/SolCord/).

Solcord is a desktop modification for the installed Discord app. This package includes the Windows installer and its corresponding source.

## This update

- Optional anonymous installation heartbeats connected to the deployed Solcord presence service.
- A live installation total and participation switch in User Settings > Solcord > Community.
- Participation is off by default. A random installation UUID is kept locally outside exported settings. No Discord account information, messages, or tokens are sent.
- Explicit opt-out stops heartbeats, deletes the local UUID, and attempts to leave immediately. Normal app shutdown attempts to leave while preserving the UUID for the next start.
- Heartbeats run about once a minute, with bounded requests and retry backoff. The server counts IDs seen in the last three minutes.
- The custom welcome intro, startup song, intro controls, and embedded startup audio are removed.
- Discord's existing in-app connecting screen keeps its normal timing, layout, transitions, and connection-error controls. Its logo is replaced with Sol and its tip reads “developed by avyxl.”
- Light-profile contrast, the chat-color switch, Session Desk, and Bleood remain available. Panda remains removed.

## Install or update

1. Extract the release ZIP.
2. Quit Discord completely, including its tray icon.
3. Run SolcordInstaller.exe and select your Discord installation.
4. Install/update, then reopen Discord.
5. To participate in the count, open User Settings > Solcord > Community and enable “Include this installation in the online count.”

The count includes participating open installations, including idle ones. It is not a total of unique people or downloads. Disabled and older clients are not counted. A failed leave request expires naturally after three minutes.

## Website

Website/index.html in the release ZIP is configured for the live Worker:
https://solcord-presence.adammohamedali01.workers.dev

The website only reads aggregate stats; visiting it does not count as an installation. Use the separate website package to publish the HTML and its downloads folder together.

## Build and test

Node.js 22+ and pnpm 11.9.0:

~~~sh
corepack pnpm install --frozen-lockfile
node scripts/build/build.mjs --standalone --disable-updater
node test/presence.mjs
~~~

On Windows, scripts/buildInstaller.ps1 compiles the installer from the current dist payload and writes accurate local checksums.

Validation for this update: desktop build, TypeScript, edited-file lint/style checks, consent and heartbeat lifecycle tests, existing appearance/Bleood/Session Desk/security/UI tests, live website count in a browser, a loader DOM fixture based on Discord's current public CSS, and all eight installer self-tests.

A signed-in Discord session was not exercised. Loader branding depends on Discord's component structure; it fails open if Discord changes it. Discord's separate native updater/launcher window is outside this in-app connecting-screen replacement.

## Privacy and licensing

Only the fixed presence endpoint is added to connect-src. Requests omit credentials and referrers. The service stores hashes of random IDs and last-seen times, and exposes the aggregate. Cloudflare processes the network requests under its own platform policies.

This is a public approximate counter; modified clients can imitate heartbeats. There is no embedded server secret or claim of tamper-proof installation verification.

GPL-3.0-or-later. See LICENSE and THIRD_PARTY_NOTICES.md. Original copyright notices remain. Solcord is not affiliated with Discord Inc. or the Solana Foundation. Supplied media and logos are included as provided.

Release metadata describes the actual locally built installer and payload hashes, without claiming an online update signature. Automatic background updates remain disabled in this package.
