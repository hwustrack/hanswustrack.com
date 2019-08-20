---
title: "Analytics"
date: 2019-08-14T07:43:44-07:00
---

I'm currently deciding between a few options to implement analytics

- Google Analytics
- Netlify Analytics
- Roll my own

# Google Analytics

The simplest option, and free. However, ad blockers can lead to GA not capturing all sessions and I feel a bit bad about willingly sharing all my visitor's data with Google.

# Netlify Analytics

This seems like a great option, as it uses server side logs to track analytics, so it's not subject to issues caused by ad blockers. Unfortunately, it's $9 per month, which is a bit steep for me at the moment.

- https://www.raymondcamden.com/2019/07/12/netlify-analytics-an-initial-look
- https://news.ycombinator.com/item?id=20405040

# Roll my own

I did see one blog post about rolling your own analytics using js, AWS Lambda, and Google Sheets, so I may explore that a bit more.

- https://www.pcmaffey.com/roll-your-own-analytics/
- https://news.ycombinator.com/item?id=19388489