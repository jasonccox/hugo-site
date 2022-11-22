---
title: git-personal-builder
date: 2022-11-21
layout: code
code:
    git: https://git.sr.ht/~jcc/git-personal-builder
    contributing:
        email: ~jcc/public-inbox@lists.sr.ht
        mailing_list: https://lists.sr.ht/~jcc/public-inbox
---

A base Docker image for creating build sidecars for [git-personal](/creations/git-personal/). These sidecars allow git-personal to trigger a build every time new code is pushed. For example, I use git-personal-builder to [auto-deploy my website](https://git.sr.ht/~jcc/hugo-site/tree/master/build/Dockerfile) and to [auto-publish its own Docker image](https://git.sr.ht/~jcc/git-personal-builder/tree/master/build/Dockerfile).

<!--more-->
