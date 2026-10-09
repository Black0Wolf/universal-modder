# Safety, legality, etiquette

These rules keep the user's accounts, saves and machine safe, and keep their mod shareable. None of this is
legal advice. When a game's EULA or mod policy matters, read it (search "<publisher> mod policy").

- VAC (Valve) bans for modified clients on VAC-secured servers. Run local tests with `-insecure` and never
  join public servers while anything is injected.
- Tools running next to a protected game (debuggers, Cheat Engine, overlays that inject) can trip its
  anti-cheat even when you don't touch it. Close protected games before RE sessions.

## Ownership and redistribution
- Mod games the user owns, from their own install or dumps of cartridges and discs they own. Only download
  ROMs, ISOs or game files if explicitly stated by the user.
- **Don't publish:**
  - game files, or byte-identical copies of them;
  - extracted assets;
  - decompiled source;
  - retail offsets or decompiler names baked into shipped code.

  `um publish check --game <install>` catches the obvious cases.
- **Do publish:**
  - your code and your assets (fal output is yours to use under fal's terms; check the model's license for
    commercial use);
  - patches, diffs, and converters or installers that transform the user's own files at install time.
- Credit loaders, libraries and references, and disclose AI use honestly. Communities react badly to
  undisclosed "vibe-coded" releases, and some (certain recomp Discords) ban AI projects.

## The user's machine
- **Back up first:** `um backup create` for saves, profiles and config, before any modded launch. Restoring
  should be one command, written down in MODLOG.md.
- **Loaders and proxy DLLs** (`winhttp.dll`, `version.dll`, `dinput8.dll`, `dxgi.dll`) sit in the game
  folder. Tell the user what you added and how to remove it. Better still, use a separate copy of the game
  or a mod manager profile.
- **Registry and config changes:** `um win reg set` backs up the key first. Note what changed.
- **Input automation takes over the user's mouse and keyboard.**
  - Check `um win drive --proc X idle`. A small number means they're active.
  - Ask before long automated runs.
  - WinDrive only sends input while the game is in the foreground.
- **Processes:** kill by exact PID. `pkill -f <pattern>` from an agent shell kills the agent's own shell.
  Don't leave topmost windows (`untop`), global hooks or orphaned ffmpeg/PowerShell processes behind.
- **Networking:** bind any bridge, debugger or MCP server you add to `127.0.0.1` with a token. Some RE tools
  bind `0.0.0.0` by default.
- **Scripts from strangers:** a viral mod's "download" is often malware. Only run loaders from their
  official repositories and releases.

## When to stop and ask
- A step would delete or overwrite saves or game files without a backup.
- Publishing: always the user's call.
