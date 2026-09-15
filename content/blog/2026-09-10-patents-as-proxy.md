---
title: Does R&D Actually Buy You Patents? EPO vs. USPTO
description: Revisiting a classic question from Griliches's foundational 1990 survey on patents and R&D, comparing EPO and USPTO-issued patents with real EU R&D and TechLand data
tags: ["patent analytics", "R&D", "innovation economics", "TechLand"]
author: Altay Özaygen
date: 2026-09-15
include_footer: true
sidebar: false
---

Patent data can tell you far more than who owns which invention.
Analyzed in bulk, across companies, technologies, and time, it
reveals:

- what a firm, or an industry, is technically capable of,
- how that capability evolves over time,
- where entire technology fields are heading,
- which firms are active in a given technology,
- how technologies and firms concentrate geographically, and
- which firms complement each other well enough to make sense as an
  M&A target.

This list is not exhaustive. It is a starting point for understanding
a technology landscape, the kind of understanding researchers,
innovation managers, and dealmakers alike can all draw on. Patent
data can answer far more than these questions alone, and none of them
require reading a single patent by hand: technological classification
codes (IPC/CPC), NACE Rev. 2 industry codes, keyword search, and
citation networks, which trace how knowledge actually flows between
inventors, companies, and technologies, do the heavy lifting.

Over this blog series, using our own platform,
[TechLand](/techlandfeatures), we will walk through a range of what is
actually possible with patent data, on its own and combined with other
sources.

We start where the field of statistical patent analysis itself
effectively started: with the question of whether patents are even a
reliable signal of a firm's inventive activity at all. Is there a
relationship between a company's R&D spending and the number of
patents it is granted?

Economists have been asking some version of this question since at
least the 1950s. The most thorough answer came from Zvi Griliches,
whose 1990 survey *Patent Statistics as Economic Indicators*
([pdf@NBER](https://www.nber.org/system/files/chapters/c8351/c8351.pdf))
remains the reference point for anyone working with patent data at
scale. His conclusions on the R&D-patents relationship specifically
are, roughly: R&D and patent counts align strongly across firms and
industries in the long run, though small firms tend to generate more
patents per R&D dollar, and patenting intensity varies by sector more
because of strategic choices than differences in inventiveness. Patent
data remains an unparalleled resource, especially once you move beyond
raw counts to use other information that is available within patent
documents.

We want to see whether that finding still holds today. We focus on
Europe's top R&D spenders and check their patents at both the European
Patent Office and the USPTO. This post walks through what we did, what
we found, and where the caveats are, using our technology landscape
analysis tool, [TechLand](/techlandfeatures), to join nearly two
decades of R&D data to patent data.

> Patent data is a genuinely rich signal, even in its simplest use,
> relating R&D spend to a raw patent count. Across our 197 companies,
> the biggest R&D spenders in Europe over nearly two decades, log R&D
> explains an average R² of 0.45 under EPO scope, versus roughly 0.9
> in Griliches's original US-based data, which covered a much wider
> range of firm sizes and therefore had more variance to explain.
> Switch to USPTO patents for the 187 of those companies with matched
> USPTO data, and that R² climbs to 0.59. Some sectors shift
> dramatically: Software & Computer Services patents roughly 7.5 times
> as much per R&D euro under USPTO scope as under EPO scope. How much
> a euro of R&D turns into patents also varies enormously by industry:
> automakers still sit well below the middle of the ranking, echoing
> what Griliches noted more than three decades ago. All of this,
> pulled and compared easily with TechLand, shows just how much there
> is to learn from patent data when analyzed in bulk.

## The data

Two sources:

- **R&D expenditure, by firm and year**: the European Commission's [EU
  Industrial R&D Investment
  Scoreboard](https://iri.jrc.ec.europa.eu/data), which has ranked the
  top R&D-spending companies in the EU annually since 2004 (1,000
  companies in most years, narrowed to 800 from 2024 onward).
- **Patent counts, by firm and year**: pulled directly from TechLand,
  built on PATSTAT/DOCDB, matched to the same companies, separately
  for the EPO and the USPTO. Pulling and matching data like this
  would normally mean writing and maintaining a fair amount of
  custom SQL; we built TechLand to avoid that kind of headache.

We started from 258 companies with 18 to 20 years of Scoreboard
history, favoring long, consistent series over brief ones, and ended
with 197 of them successfully matched to confirmed EPO patent data
(187 of those 197 also matched under USPTO scope). Patents are counted
by **application year**, the closest date to the actual invention. The
counts themselves cover **first publication of granted patent
applications**, and only those published by the **European Patent
Office** or the **USPTO**, compared side by side.

## R&D and patents, firm by firm

{{< scatter-rd-patents >}}

Each dot is a company. Drag the slider and watch the cloud move as R&D
spending and patenting grow together across nearly two decades. The
relationship is visibly there: bigger R&D spenders cluster toward more
patents. But it is not a straight line, and the scatter is wide,
which is exactly what you would expect if some of what a patent
captures is inventive effort, and some of it is timing, firm-specific
patenting strategy, and the industry a company belongs to, visible in
the chart as the color of each dot.

One caveat visible in the animation: the final one to three years,
especially 2023, show artificially low patent counts because recent
applications have not yet been published or granted. Read the
right-hand edge as incomplete, not as a real slowdown.

Across our 197 companies, the log-log relationship between R&D and
patents is real and systematic, but weaker than Griliches's original
cross-section, partly because our sample is restricted to large R&D
spenders and has less variance to explain. Averaged across 2006 to
2023, R² comes out to 0.45 under EPO scope (ranging from 0.36 in the
weakest year to 0.54 in the strongest). Note that the 2023 endpoint is
affected by incomplete patent publication and grant lags; including it
in the average slightly understates the relationship. Some of the gap
with Griliches is genuinely about scope: switching to USPTO patents
for the 187 of these companies with matched USPTO data lifts R² to
0.59, closing part of the distance to his original US-based finding.
The rest likely comes down to our sample itself: 197 already-large R&D
spenders have less variation left to explain than the broader mix of
firm sizes Griliches worked with.

## Not every industry patents the same way

{{< bar-patents-per-rd >}}

Two industries can spend the same amount on R&D and end up with very
different numbers of patents. That gap is not really about which
industry is more "innovative." It reflects how central patenting is to
a given industry's competitive strategy: pharmaceutical and
electronics firms tend to patent almost everything patentable, while
others rely more on trade secrecy, speed to market, or manufacturing
know-how that does not lend itself to patenting at all. Which patent
office you count at matters too, as we will show below.

Support Services shows the highest ratio under EPO scope (0.57 patents
per €M of R&D), the chart's default view, by a wide margin, but it is
worth treating that with real caution: it is also one of the smallest
sectors in our data, built from only six years of matched companies,
and a ratio computed from that few observations can swing wildly on
one firm's numbers alone, exactly the kind of small-sample volatility
Griliches warns about throughout the original survey.

At the other end, Software & Computer Services shows one of the lowest
ratios in our sample under EPO scope (0.01 patents per €M of R&D),
backed by a full eighteen years of history: still near the very
bottom, because software firms often protect their work through
copyright and trade secrecy rather than patents, and because the EPO
has historically taken a stricter line than the US on software
patentability, requiring a technical effect beyond just running as
code.

We can check that directly: toggle the charts above to USPTO scope.
Software & Computer Services shows the clearest effect, its
patents-per-R&D-euro ratio is roughly 7.5 times higher under USPTO
scope than EPO scope, moving it from 17th out of 18 sectors up to
11th. Technology Hardware & Semiconductors shows an even sharper
version of the same pattern, from 16th up to 2nd. The overall R²
between R&D and patents rises too, from 0.445 under EPO scope to 0.591
under USPTO scope for the matched sample, closing part of the gap with
Griliches's 1990 result. Which patent office you count is part of that
gap, not just noise.

Automobiles & Parts sits well below the middle of the ranking too.
Griliches himself flagged motor vehicles specifically as an industry
that "patent[s] very much less than would be predicted from their R&D
numbers alone," and that finding still holds up, more than three
decades later, even as the exact ranking has shifted somewhat as our
own data has gotten cleaner.

## What this analysis does not do

Worth being clear about what this post is and is not. This is a fast,
practical demonstration meant to show what is possible when you join
patent data to other sources, not an exhaustive research exercise. A
more rigorous version of this analysis, chasing down every edge case,
is exactly the kind of work we would do for a client, or that a
researcher digging into a specific sector might want to do themselves.
Everything here is reproducible in TechLand, and every caveat is
something you can inspect, adjust, or override.

A few specific things worth naming:

- We did not correct for parent/subsidiary patent assignment, so some
  multinational R&D spenders may be undercounted.
- Company name matching runs into **applicant disambiguation**, a
  well-documented headache in patent search. For this post, we matched
  company names to applicant names by hand, tracing each one through
  the company's corporate history. A few patterns came up repeatedly:
  companies that share a brand name but are genuinely separate
  entities (Volvo Cars and Volvo Trucks split in 1999; only Volvo
  Trucks appears here), companies that file under a legal name
  unrelated to their brand (BMW appears in patent records as
  "Bayerische Motoren Werke AG"), companies that changed name entirely
  over time (Daimler has filed as DaimlerChrysler, Daimler, and
  Mercedes-Benz Group across our 20-year window; we matched all
  three), and companies that patent almost entirely through divisional
  subsidiaries rather than the parent name (Atlas Copco's patents sit
  under names like Atlas Copco Airpower NV and Atlas Copco Rock Drills
  AB, not "Atlas Copco AB" itself).
- R&D figures in the Scoreboard files are corrected for inflation
  using Eurostat's Euro area
  [HICP](https://ec.europa.eu/eurostat/web/hicp/database).
- The most recent one to three years of patent counts are artificially
  low: patents take time to publish and be granted, so treat the
  right-hand edge of any time series here with caution, not as a real
  slowdown.

None of this is unusual for a first pass at this kind of data, and
being upfront about it is part of doing the analysis properly.

> Patents are a real signal about a firm, an industry, or a technology.
> Relating how much a firm spends on R&D to its patent count alone,
> though, leaves a lot of variation unexplained. Most of that
> variation is not noise. It is sector strategy and patent office
> rules, and it is measurable. Add the right financial or other data,
> and the ground opens up for real econometric work. Landing on the
> right group of patents in the first place is itself iterative, often
> tedious work, which is what TechLand is built to streamline.

## What comes next

This is the first post in a blog series showing what is actually
possible with patent data, on its own and combined with other sources.
We will keep coming back to these same 197 companies, each time using
TechLand to ask something new of the same data.

If you work with patent data and want to explore something like this
for your own sector or portfolio, [contact us](/#section5) or [DM me on
LinkedIn](https://www.linkedin.com/in/altayoz).
