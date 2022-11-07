---
title: How I Got Blocked by the ACM
date: 2022-11-07
summary: The amusing story of how trying to be clever got me blocked from accessing all ACM pubications.
---

I recently heard about the <abbr title="Association for Computing Machinery">ACM</abbr>'s [History of Programming Languages](https://dl.acm.org/doi/book/10.1145/800025) book. Being a nerd, I wanted to read it. The book is split into almost 100 sections on the ACM's website, each of which requires a separate PDF download. I'd prefer to have a single PDF that I can put on my e-reader, so I set about opening many tabs to download and combine all of the sections. A few sections in, I realized that the URLs were made up of sequential numbers; soon I had a nifty script ready:

```sh
for n in $(seq 339 429); do
    curl -LO "https://dl.acm.org/doi/pdf/10.1145/800025.1198$n"
done
```

I ran the script and... now I'm blocked from accessing any publications on the ACM's website. Oof.

![screenshot of the ACM website showing that my IP address is blocked with a support email listed for help](/images/banned-by-acm.png)

Let's hope they actually check that support email! If not, I'll be stuck using a VPN to read papers for school.
