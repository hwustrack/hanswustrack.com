---
title: "Product Hunt 2019 Posts"
date: 2020-03-18T14:39:36+13:00
---

{{< ph-import-highcharts >}}

🚧🚧🚧🚧 In Progress 🚧🚧🚧🚧

Product Hunt (PH) has a really awesome free [GraphQL API](https://api.producthunt.com/v2/docs) that I wanted to try out, so I figured I'd pull some posts and see what I could find.

I retrieved the top 1944 posts by vote count, submitted between 2019-01-01T12:00:00Z and 2020-03-01T12:00:00Z. The data was pulled on 3-12-2020. The goal was simply to get a lot of posts over the last year and take a look at some of the trends.

## Background

A bit about the terminology here (which is detailed in the [PH API docs](https://api.producthunt.com/v2/docs)). I'm mainly focused on Posts, which is the thing you scroll through on the [home page](https://www.producthunt.com/) of Product Hunt. Posts have assorted fields like name, creation time, description, vote count, etc. I also looked at the Topics. Each Post has a series of Topics associated with it, which is like a tag to categorize the Post.

## Top Posts

{{< ph-top >}}

[INK](https://www.producthunt.com/posts/ink-1c962f43-e6e2-4291-942f-6090712bf2b6) was the clear outlier here.

## Vote counts by hour submitted

I binned the posts hour submitted to see if we see any advantages to posting at a certain time of day.

{{< ph-hourly-trend >}}

70% of the posts were submitted between 6 - 8 UTC (2 - 4 EST), which was a bit surprising to me, but could mean a lot of people using PH are posting from Europe.

## Topics

### Most Common

{{< ph-topics-count >}}

Productivity and Tech clearly far exceed the others. 74% of the posts had at least one of these topics associated with it.

### Performance

The next two charts look at the average number of votes a particular topic received. Only topics that had at least 10 posts associated with it were included here.

The first chart sort is sorted by votes mean.

{{< ph-votes-count >}}

This second chart is sorted by votes standard deviation.

{{< ph-votes-std >}}

## Conclusion

You can see the code I use to retrieve and aggregate the posts [here](https://github.com/hwustrack/ph-queries).