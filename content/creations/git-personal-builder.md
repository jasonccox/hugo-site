---
title: git-personal-builder
date: 2022-11-21
lastmod: 2022-11-22
layout: code
code:
    git: https://git.sr.ht/~jcc/git-personal-builder
    contributing:
        email: ~jcc/public-inbox@lists.sr.ht
        mailing_list: https://lists.sr.ht/~jcc/public-inbox
---

A base Docker image for creating build sidecars for [git-personal](/creations/git-personal/). These sidecars allow git-personal to trigger a build every time new code is pushed. For example, I use git-personal-builder to [auto-deploy my website](https://git.sr.ht/~jcc/hugo-site/tree/master/build/Dockerfile) and to [auto-publish its own Docker image](https://git.sr.ht/~jcc/git-personal-builder/tree/master/build/Dockerfile).

<!--more-->

git-personal-builder runs a super simple HTTP server listening for `POST /build` requests from git-personal. These requests include the hash of the commit being built, any tags associated with the commit, and a `tar.gz` archive of the code at that commit. The server extracts the code archive into a directory and then calls a build command with the hash, directory, and tags as arguments. This build command is supplied by the image created on top of the git-personal-builder image -- check out the examples linked above to see how it is used in practice.
