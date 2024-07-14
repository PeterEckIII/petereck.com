---
title: 'A little trouble deploying'
pubDate: 2024-07-15
description: 'Some thoughts on DNS records and AWS'
author: 'Peter Eck'
image:
  url: 'https://images.unsplash.com/photo-1720760891750-6a91487eca7a?q=80&w=1674&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'
  alt: 'Orange sand and sandstone combine to show a beautiful rock formation in the desert'
tags: ['aws', 'dns', 'astro', 's3', 'cloudfront', 'route53', 'networking', 'cdn']
---

I was following [the official deploy guide](https://docs.astro.build/en/guides/deploy/aws/) for Astro and AWS, which led me to an even [deeper dive](https://docs.aws.amazon.com/AmazonS3/latest/userguide/website-hosting-custom-domain-walkthrough.html) into the topic. I wanted to mess around with Astro to get a feel for its pros and cons. But the deployment process was so easy I decided to jump in and try it.

First you create a few S3 buckets for your domain and `www` subdomain. From there you have to setup the buckets for static web hosting. Since Astro builds conveniently to an `index.html` file I decided this would be a fun adventure to get a blog started by building a site with Astro.

What I didn't realize was the domain I registered 2-3 years ago had already been configured with an A record. The way I'm thinking about A records, it's almost like a redirect rule. I set up an A record on the `petereck.com` domain with a value of the static web hosting URL I got from S3. After I figured this out I was not only able to get it deployed easily, I was also able to seamlessly update that A record with my [CloudFront](https://aws.amazon.com/cloudfront/) distribution URL. This easily integrates a globally-available CDN that is supported by AWS's infrastructure.

Networking has been somewhat of an albatross for me, so it's nice to finally start to understand a thing or two about it!
