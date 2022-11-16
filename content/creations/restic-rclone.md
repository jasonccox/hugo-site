---
title: restic-rclone
date: 2020-06-25
layout: code
code:
    git: https://github.com/jasonccox/restic-rclone-docker
---

A Dockerfile for running scheduled backups using restic with rclone as the backend. I used to run this on my home server but have since abandoned it in favor of running restic and rclone directly on the host OS to integrate my backups with ZFS snapshots. (There's also an [image](https://hub.docker.com/r/jasonccox/restic-rclone) available on Docker Hub, but it's quickly becoming out-of-date...)
