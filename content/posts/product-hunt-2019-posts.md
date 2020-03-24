---
title: "Product Hunt 2019 Posts"
date: 2020-03-18T14:39:36+13:00
---

{{< ph-import-highcharts >}}

Product Hunt (PH) has a really awesome free [GraphQL API](https://api.producthunt.com/v2/docs) that I wanted to try out, so I figured I'd pull some posts and see what I could find.

I retrieved the top 1944 posts by vote count, submitted between 2019-01-01T12:00:00Z and 2020-03-01T12:00:00Z. The data was pulled on 3-12-2020. The goal was simply to get a lot of posts over the last year and take a look at some of the trends.

## Background

A bit about the terminology here (which is detailed in the [PH API docs](https://api.producthunt.com/v2/docs)). I mainly focused on Posts, which is the thing you scroll through on the [home page](https://www.producthunt.com/) of PH. Posts have assorted fields like name, creation time, description, vote count, etc. I also looked at Topics. Each Post has a series of Topics associated with it, which is like a tag for categorization.

## Top Posts

{{< ph-top >}}

[INK](https://www.producthunt.com/posts/ink-1c962f43-e6e2-4291-942f-6090712bf2b6) was the clear outlier here.

## Vote counts by hour submitted

I binned the posts hour submitted to see if we see any advantages to posting at a certain time of day.

{{< ph-hourly-trend >}}

70% of the posts were submitted between 6 - 8 UTC (2 - 4 EST), which was a bit surprising to me, but could mean a lot of people using PH are posting from Europe. The standard deviations are so high here that you can't really say certain times are better to post at than others.

## Topics

### Most Common

{{< ph-topics-count >}}

Productivity and Tech clearly far exceed the others. 74% of the posts had at least one of these topics associated with it.

### Performance

The next two charts look at the average number of votes a particular topic received. Only topics that had at least 10 posts associated with it were considered.

The first chart is sorted by votes mean and the second is sorted by votes standard deviation.

{{< ph-votes-count >}}

{{< ph-votes-std >}}

Again, since standard deviations here are so high, you definitely can't say that everyone should build a Text Editor since that has the highest vote average. However, it does give you a general sense of how Topics have performed.

## Wrapping Up

Unfortunately, I haven't found anything too illuminating. Not too surprising, since there are a lot of factors that determine how a Post performs, the Topics associated with it not being a particularly important one.

You can find the code I used to retrieve and aggregate the posts [here](https://github.com/hwustrack/ph-queries).