---
title: "Blog"
date: 2020-01-05T17:07:51+13:00
---

This website!

## Core

### Framework

This site is built with [Hugo](https://gohugo.io/) using the [Minimo](https://themes.gohugo.io/minimo/) theme. I looked at Jekyll and Gatsby too but ultimately went with Hugo as it looked like the best balance of simplicity and flexibility. Plus it's built on Golang, so it's extremely fast.

### Hosting

This site is hosted on [Netlify](https://www.netlify.com/). I cannot recommend them enough. They offer free hosting for basic websites like mine, and offer automatic deployments from a github repo.

All images are hosted on [Cloudinary](https://cloudinary.com/). You get tons of storage and bandwidth for free, without even having to put in a credit card! Their API is also extremely flexible, allowing you to add simple parameters to the url to reduce image file sizes on demand.

### Domain

I bought the domain on Google Domains. I liked that they had simple pricing, with no upsells.

## Mailing List

### Get sign ups

Netlify Form (only 100/month for free) -> Zapier -> Google Sheet

### Notify on new post

I manually add people from the Google Sheet to my Google Contacts and add a label, then send a group email to the label.

### Allow you to unsubscribe

Anyone receiving the emails will need to respond to me and I'll remove them from the list.

## Analytics

I'm currently deciding between a few options to implement analytics:

- Google Analytics
- Netlify Analytics
- Roll my own

### Google Analytics

The simplest option, and free. However, ad blockers can lead to GA not capturing all sessions and I feel a bit bad about willingly sharing all my visitor's data with Google.

### Netlify Analytics

This seems like a great option, as it uses server side logs to track analytics, so it's not subject to issues caused by ad blockers. Unfortunately, it's $9 per month, which is a bit steep for me at the moment.

- https://www.raymondcamden.com/2019/07/12/netlify-analytics-an-initial-look
- https://news.ycombinator.com/item?id=20405040

### Roll my own

I did see one blog post about rolling your own analytics using js, AWS Lambda, and Google Sheets, so I may explore that a bit more.

- https://www.pcmaffey.com/roll-your-own-analytics/
- https://news.ycombinator.com/item?id=19388489