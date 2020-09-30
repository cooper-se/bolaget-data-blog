---
layout: post
title: "Does high stock volatility suggest high sales?"
description: "tododod"
date: 2020-09-23
feature_image: images/stockgraph.jpg 
tags: []
---

Systembolaget releases in detail sales figures infrequently.
However, they release stock level data on an almost daily basis. The stock data also includes a huge amount of geographic data than the sales figures lack.

We've already looked at how correlated the amount of stock is to the sales that a given article is making. Now we're going to see if we can detect if an item is flying of the shelves by looking at the volatility of its stock level. **But can stock volatility tell us anything about sales?**

<!--more-->

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
> Zip that together with a measure of variance of TotalStock from the database.
>
> Maybe dig out history and shove it in this: https://traces.readthedocs.io/en/latest/api_reference.html#histogram to get s.d.?
>
> Then another correlation comparison (http://www.sthda.com/english/wiki/correlation-test-between-two-variables-in-r)
> But Actually you probably need to control for volume (which you have from before), like this http://sherrytowers.com/2013/09/23/correlations-and-partial-correlations/
>
> And then blah blah words
>