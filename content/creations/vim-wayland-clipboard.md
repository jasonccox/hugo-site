---
title: vim-wayland-clipboard
date: 2021-02-09
lastmod: 2022-11-16
layout: code
code:
    git: https://github.com/jasonccox/vim-wayland-clipboard
    contributing:
        email: ~jcc/public-inbox@lists.sr.ht
        mailing_list: https://lists.sr.ht/~jcc/public-inbox
        github: https://github.com/jasonccox/vim-wayland-clipboard
---

A simple Vim plugin to integrate the `+` register with Wayland's system clipboard using [wl-clipboard](https://github.com/bugaevc/wl-clipboard). This plugin allows you to yank text into the `+` register and paste it in other Wayland applications, or copy text in other Wayland apps and paste it in Vim from the `+` register. Operators and counts work, too!

<!--more-->

When running Vim outside of Wayland, the `+` register continues to work as normal.

{{% aside %}}
This plugin is really just a band-aid until Vim gets [built-in clipboard support on Wayland](https://github.com/vim/vim/issues/5157).
{{% /aside %}}
