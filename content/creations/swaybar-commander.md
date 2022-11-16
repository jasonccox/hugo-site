---
title: swaybar-commander
date: 2022-10-29
lastmod: 2022-11-16
layout: code
code:
    git: https://git.sr.ht/~jcc/swaybar-commander
    contributing:
        email: ~jcc/public-inbox@lists.sr.ht
        mailing_list: https://lists.sr.ht/~jcc/public-inbox
---

A status command for the [Sway window manager](https://swaywm.org)'s built-in swaybar that allows sections of the bar to update independently. Each section updates at a regular frequency, and additional updates can be requested on-demand via a helper command and/or a background script. The sections are configured in a simple [TOML](https://toml.io/en/) file and communicate with the bar using the [swaybar-protocol](https://man.archlinux.org/man/swaybar-protocol.7.en).

<!--more-->

Here are a few of my configured sections that illustrate swaybar-commander's capabilities:

- A date/time section shows the time down to the second, so it updates every second.
- A volume level section updates every 10 seconds, but an update is also triggered every time I use the volume up/down/mute keyboard shortcut.
- A network section shows the names of connected networks (e.g. the WiFi SSID) and refreshes every 60 seconds. It also uses a background script which runs `nmcli monitor` and triggers a new update as soon as a network change is detected.
