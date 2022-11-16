---
title: Why I Switched to a Simple Static Site
date: 2020-12-21
lastmod: 2021-03-06
summary: For the last year and a half I ran my personal website using Grav CMS with my own Webfolio theme. However, it’s now a super simple static site built with Hugo. In this post, I explain why I decided to make that switch.
---

For the last year and a half I ran my personal website using [Grav CMS](https://getgrav.org) with my own [Webfolio](/creations/webfolio) theme. However, it's now a super simple static site built with [Hugo](https://gohugo.io). In this post, I'll explain why I decided to make that switch.

Until recently, I was hosting my site for free through my university. As graduation approached, I knew I'd need to move to a different hosting provider. At the same time, I began thinking about expanding my site's purpose. Originally I designed the site as an online portfolio, but I was sick of that; the whole thing felt a bit fake, like a bad advertisement. I wanted to create a website to share my creations, thoughts, and interests, including the ones that are unrelated to my career as a software engineer.

Since I already wanted to make changes and needed to switch hosting providers, it seemed like a good time to consider moving away from Grav. My experience with Grav had been fine, but not stellar. At one point my whole site broke after a failed Grav update, and I had to restore a backup to get things working again. I had also noticed that load times were painfully slow -- 10-15 seconds over fast Internet -- whenever Grav didn't have a copy of the requested page in its cache. Because of these experiences, I decided to explore some alternatives with a focus on simplicity, flexibility, and speed.

I don't have any dynamic or interactive content, so it didn't take me long to settle on using a static site generator -- serving static files is dead simple and super speedy. I initially tried going totally custom with [Pandoc](https://pandoc.org) and a [Makefile](https://www.gnu.org/software/make/), and after a few hours and some help from a [blog post](https://itnext.io/glorious-makefile-building-your-static-website-4e7cdc32d985), I'd created my own basic static site generator. For a month or two it was great. Pandoc and Make provided the features I care about most -- converting Markdown to HTML; inserting a consistent header, footer, and stylesheet; and building the whole site with a single command -- but not much more. I understood how it all worked because I built it myself, yet I didn't have to maintain anything more than a simple `Makefile`. I even found a convenient way to [host the site for free with Digital Ocean's App Platform](https://www.digitalocean.com/community/tutorials/how-to-deploy-a-static-website-to-the-cloud-with-digitalocean-app-platform)!

After a few months I found myself wanting to add slightly more complex features like a site map or an RSS feed. I certainly could have made those by hand without too much work, but I wasn't excited about it. Plus I ran the risk of forgetting to update these other pieces and having them become out of date. As a result, I did some more exploring and decided to try out [Hugo](https://gohugo.io). Because the DIY approach had pushed me to do almost everything with only the basic structures of Markdown, converting it to Hugo was easy.

So far Hugo has been a great solution for me. I enjoy the fact that I don't have to worry about themes at all; while Hugo does provide support for themes, one can also simply create their own layouts (templates) that are specific to their site. For me, this was a great way to have complete control over how my site looks without feeling the need to develop an entire generalized, customizable theme.

I also appreciate that the structure of the generated site mirrors the directory structure of the source. This means that for things I don't feel like taking the time to auto-generate, like the navigation menu, I can easily hard-code links.

Most importantly, though, Hugo allows me to have a site that I understand without spending much time working on it. Layouts make sense and are there for me to use when they'll make building/maintaining my site easier, but it's also easy to add hard-coded content when auto-generating it would be more work than it's worth. I love having these niceties available to me without feel pushed to use them all the time.

Overall, I'm enjoying taking a simpler approach to my website. My DIY static site generator pushed me to keep the content basic, and using Hugo allows me to add some more complex features without losing that simplicity. Now I spend more time adding/updating content and less time worrying about breaking things along the way.
