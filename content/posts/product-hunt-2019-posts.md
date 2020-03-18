---
title: "Product Hunt 2019 Posts"
date: 2020-03-18T14:39:36+13:00
---

🚧🚧🚧🚧 In Progress 🚧🚧🚧🚧

{{< ph-import-highcharts >}}

I retrieved the top 1944 posts by votes between 2019-01-01T12:00:00Z and 2020-03-01T12:00:00Z on Product Hunt using their [GraphQL API](https://api.producthunt.com/v2/docs). Arbitrary? Absolutely. But my goal was simply to get a lot of posts over the last year and take a look at some of the trends.

## Top Posts

{{< ph-top >}}

## Vote counts by hour submitted

I binned the posts into the hour they were submitted to see if that would affect their vote count.

{{< ph-hourly-trend >}}


## Topics

### Most Common

Topics submitted most often.

{{< ph-topics-count >}}

### Performance

See how topics performed. Two things - sort by binned votes then standard deviation and one where we just sort by standard deviation.

Votes -> Std

{{< ph-votes-bin-std >}}

Std

{{< ph-votes-std >}}