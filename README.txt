SOLCORD 2.1.0

INSTALL / UPDATE
1. Extract this ZIP.
2. Quit Discord completely, including its tray icon.
3. Run SolcordInstaller.exe.
4. Select your installed Discord client and install/update.
5. Reopen Discord.

ONLINE INSTALLATIONS
Open User Settings > Solcord > Community.
The public online total is displayed there.
Enable "Include this installation in the online count" to participate.
This setting is OFF by default.
A random local installation ID is sent about once per minute.
No Discord account ID, messages, username, or token is sent.
Turning it off stops heartbeats, clears the local ID, and attempts an immediate leave.
Normal app shutdown attempts to leave while keeping the same ID for the next start.
Offline entries expire after three minutes. The total can lag briefly because of caching.

Backend: https://solcord-presence.adammohamedali01.workers.dev
Website: https://avyxl.github.io/SolCord/

LOADING
The separate custom intro and its music are removed.
Discord's normal in-app loading screen keeps its timing and transitions.
Its logo becomes Sol and its tip always reads "developed by avyxl".
Discord's separate native updater window is not part of this in-app screen.

EXISTING FEATURES
Light profiles stay readable.
User Settings > Solcord > Use Solcord chat colors can restore your normal chat theme.
Session Desk and the Bleood 1-in-50 sound/image plugin remain available.
Panda remains removed.

WEBSITE FILE
Website/index.html is configured for the live counter.
The separate website package includes the public installer download under site/downloads.
Publish that package's site contents together to avoid a missing download.

SOURCE
Source/Solcord contains the editable corresponding source.
Required copyright and GPL license notices remain.
build-info.json records the current installer and embedded payload checksums.
No signed automatic online update feed is enabled.

VALIDATION
Desktop build, TypeScript, edited-file lint/styles, presence lifecycle tests,
existing appearance/Bleood/Session Desk/security/UI tests, live website count,
standard-loader fixture, and all eight installer self-tests passed.
No signed-in Discord session was tested.
