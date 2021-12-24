bwrap-scripts
=============

[![sourcehut](https://img.shields.io/badge/repository-sourcehut-lightgrey.svg?logo=data:image/svg+xml;base64,PHN2ZyBmaWxsPSIjZmZmIiB2aWV3Qm94PSIwIDAgNTEyIDUxMiIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj48cGF0aCBkPSJNMjU2IDhDMTE5IDggOCAxMTkgOCAyNTZzMTExIDI0OCAyNDggMjQ4IDI0OC0xMTEgMjQ4LTI0OFMzOTMgOCAyNTYgOHptMCA0NDhjLTExMC41IDAtMjAwLTg5LjUtMjAwLTIwMFMxNDUuNSA1NiAyNTYgNTZzMjAwIDg5LjUgMjAwIDIwMC04OS41IDIwMC0yMDAgMjAweiIvPjwvc3ZnPg==)](https://sr.ht/~seirdy/bwrap-scripts) [![GitLab mirror](https://img.shields.io/badge/mirror-GitLab-orange.svg?logo=gitlab)](https://gitlab.com/Seirdy/bwrap-scripts) [![GitHub mirror](https://img.shields.io/badge/mirror-GitHub-black.svg?logo=github)](https://github.com/Seirdy/bwrap-scripts) [![Codeberg mirror](https://img.shields.io/badge/mirror-Codeberg-blue.svg?logo=codeberg)](https://codeberg.org/Seirdy/bwrap-scripts)

This is a set of bubblewrap scripts and allowed syscalls, the latter of which can generate ebpf filters using the Whonix [sandbox-app-launcher](https://github.com/Whonix/sandbox-app-launcher).

Be aware that these contain some personal preferences and were designed for my personal use; you should double-check the contents of the scripts and make them work for you.

Some quirks:

- Shebang lines are `#!/usr/bin/env dash`; you should be able to change them to another common POSIX-y shell (bash, zsh, etc) if you don't have the Debian Almquist Shell installed.
- I run Wayland, so there are some Wayland-specific envvars/paths involved
- I symlink a few FF config files (like my user.js and userChrome.css) from the Flatpak config dir to ~/.mozilla because I use the FF beta version via Flatpak (mostly headless).
- I set my FF GTK theme to Breeze-dark, but my system currently uses Adwaita-dark.
- Browsers (Chromium, Firefox, NetSurf) get their own "Downloads" subdir. What `chromium-sandbox` thinks is `~/Downloads` is actually `~/Downloads/chromium` on the host system.
- A few of the ro-binds are less granular than I'd like them to be. For instance, all programs get full access to library directories. Chromium gets full access to XDG_CONFIG_HOME because it has chromium configs, fontconfig settings, GTK settings, and a bunch of other stuff that I haven't gotten around to listing.
- Chromium's nav widgets have poor font rendering since they don't have access to all the files needed for proper antialiasing. I'm okay with this because the actual page content looks fine and the text is still readable.

The most useful script here is probably w3m-sandbox, useful for parsing HTML from stdin or from a file offline. I use it to preview HTML emails, among other things.
