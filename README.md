bwrap-scripts
=============

This is a set of bubblewrap scripts and allowed syscalls, the latter of which can generate ebpf filters using the Whonix [sandbox-app-launcher](https://github.com/Whonix/sandbox-app-launcher).

Be aware that these contain some personal preferences and were designed for my personal use; you should double-check the contents of the scripts and make them work for you.

Some quirks:

- I run Wayland, so there are some Wayland-specific envvars/paths involved
- I symlink a few FF config files (like my user.js and userChrome.css) from the Flatpak config dir to ~/.mozilla because I use the FF beta version via Flatpak (mostly headless).
- I set my FF GTK theme to Breeze-dark, but my system currently uses Adwaita-dark.
- Browsers get their own "Downloads" subdir.
- A few of the ro-binds are less granular than I'd like them to be. For instance, all programs get full access to library directories. Chromium gets full access to XDG_CONFIG_HOME because it has chromium configs, fontconfig settings, GTK settings, and a bunch of other stuff that I haven't gotten around to listing.
- Chromium's nav widgets have poor font rendering since they don't have access to all the files needed for proper antialiasing. I'm okay with this because the actual page content looks fine and the text is still readable.

The most useful script here is probably w3m-sandbox, useful for parsing HTML from stdin or from a file offline. I use it to preview HTML emails, among other things.
