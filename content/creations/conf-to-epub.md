---
title: conf-to-epub
date: 2022-04-22
lastmod: 2022-11-16
layout: code
code:
    git: https://github.com/jasonccox/conf-to-epub
    contributing:
        email: ~jcc/public-inbox@lists.sr.ht
        mailing_list: https://lists.sr.ht/~jcc/public-inbox
        github: https://github.com/jasonccox/conf-to-epub
---

A script to convert LDS General Conferences for e-readers, as well as pre-generated files for past conferences. These are pretty basic EPUBs -- the footnotes are removed, images may not show up right, and links aren't guaranteed to work -- but if you just want a table of contents and the text of each talk, they should be good enough.

<!--more-->

To **download the files for your e-reader**, check out the [`conferences/`](https://github.com/jasonccox/conf-to-epub/tree/master/conferences) directory in the repository. (Conferences are organized by year and month.) Currently, `.epub` and `.mobi` files are provided. If you need a different format, try using a tool like [Calibre](https://calibre-ebook.com/) (desktop application that also includes the `ebook-convert` CLI) or [Cloud Convert](https://cloudconvert.com/epub-converter) (online converter) to convert the `.epub` file to your desired format.
