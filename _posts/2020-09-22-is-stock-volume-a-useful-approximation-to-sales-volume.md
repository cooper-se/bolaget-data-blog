---
layout: post
title: "Is stock volume a useful approximation to sales volume? [TODO]"
description: ""
date: 2020-09-22
feature_image: images/salestext.jpg 
tags: ["stock"]
---

Systembolaget releases in detail sales figures infrequently.
However, they release stock level data on an almost daily basis. The stock data also includes a huge amount of geographic data than the sales figures lack.

Having an up-to-date and geographically detailed view of sales would help producers a lot. **Can stock levels be a useful approximation for this?**

<!--more-->

Let's compare average stock levels for the year 2020 with that year's sales figures, article by article. Then we'll visualize that data and then apply an appropriate correlation test.

> TODO I can't write this yet I don't have the data. I have 2020 stock data (which btw needs rebuilding), so I need the 2020 years report but here's the plan:
>
>    artikels
>        .Where(a => a.Volym_i_ml > 0 && a.Aktuellt_pris > 0 && a.Försäljning_i_liter > 0)
>        .Select(a => new
>        {
>            articleId = a.Artikel_ID,
>            salesvalue = a.Försäljning_i_liter * ((a.Aktuellt_pris * 1000) / (decimal)a.Volym_i_ml)
>        });
>
>
> Zip that together with average TotalStock from the database. Something like this for queries:
>
>   select articleid, sum(EXTRACT(epoch FROM (COALESCE(upper(sys_period), NOW()) - lower(sys_period))) * quantity) / sum(EXTRACT(epoch FROM (COALESCE(upper(sys_period), NOW()) - lower(sys_period)))) as averagestock
>    from totalstock_with_history
>    where upper(sys_period) > '2020-01-01'::timestamptz
>    and lower(sys_period) < '2021-01-01'::timestamptz
>    group by articleId
>
>
> Then do this on the the collections:
> http://www.sthda.com/english/wiki/correlation-test-between-two-variables-in-r
>
> Then speculate a bit about what that means and comment about how it doesn't show anything about geographical,
> but it seems like a decent working assumption (maybe?) Let's see how the data comes out.
