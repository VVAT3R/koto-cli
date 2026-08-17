<div align="center">
  <img src="assets/logo.png" alt="koto-cli" height="128">
  <p><strong>Watch anime from your terminal.</strong></p>

  <p>
    <a href="https://github.com/VVAT3R/koto-cli">GitHub</a> •
    <a href="https://github.com/VVAT3R/koto-cli/issues">Issues</a>
  </p>

  <p>
    <img src="https://img.shields.io/badge/license-GPLv3-blue" alt="License">
    <img src="https://img.shields.io/badge/shell-POSIX-green" alt="POSIX">
  </p>
</div>

---

A standalone POSIX shell script to browse, search and watch anime from the command-line, inspired by [pystardust/ani-cli](https://github.com/pystardust/ani-cli). It scrapes **anikototv.to** for direct HLS streams — no crypto dependencies.
### Quick start

```sh
curl -fsSL https://raw.githubusercontent.com/VVAT3R/koto-cli/main/install.sh | sudo sh
```
### Features

- **anikoto** source — direct `.m3u8` streams, no crypto dependencies
- Hard-sub (hsub), sub, soft-server and dubbed playback
- Watch history with resume position tracking (`-c`, `--resume`)
- Batch download with progress indicator (`--batch`)
- Single & multi-episode selection, including ranges (`-e`, `-r`)
- Quality selection (`-q`)
- Interactive menus (fzf / rofi / dmenu)
- Jump between seasons of a show from the post-play menu
- Skip intros with ani-skip (`--skip`, mpv only)
- Player support: mpv, vlc, iina, android, flatpak, syncplay and more
- Next-episode countdown (`-N`)
- Install & uninstall scripts included

### Notes on episode availability

- **Episode not yet uploaded**: If the latest episode of an airing anime has been released but koto-cli shows it as unavailable, it means anikototv.to has not yet added it to their database. Try again later.
- **No valid sources**: If the episode exists on anikoto but koto-cli fails to play it, none of the supported servers (hsub, sub, soft-server, dub) are available for that episode.

### How koto-cli came to be

koto-cli started as a fork of ani-cli whose provider missed some anime I wanted to watch. I reverse-engineered [anikototv.to](https://anikototv.to) and built an **anikoto** provider, then spun it out into this standalone repo. Everything runs in plain POSIX shell — no API keys, no crypto, no python3.

The pipeline: search the site's AJAX endpoints → extract anime ID and episode list → resolve hsub/sub/soft-server/dub servers → grab `.m3u8` streams from megaplay embeds → auto-detect and strip obfuscated segment prefixes → feed clean MPEG-TS to the player.

### Usage

```sh
koto-cli [options] [query]
```

Run `koto-cli -h` for the full list of options.
