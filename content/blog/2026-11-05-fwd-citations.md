---
title: "Beyond patent counts: forward citations in electronics and health sectors"
date: 2026-11-06
description: "Who cites the patents of Europe's persistent R&D investors? A comparison of forward citations in electronics and health sectors, with Trajtenberg (1990) as the reference point."
tags: ["patents", "forward citations", "PATSTAT", "R&D", "TechLand"]
---

## From counting patents to following their forward citations

Counting patents tells us how much a firm patents, but not whether
anyone builds on those patents. In the first post of this series, I
used the Griliches framework to relate firm R&D spending to patent
counts. Here I take the next step and look at forward citations,
meaning the citations that a patent receives from later patent.

The reference point is Trajtenberg (1990), ["A Penny for Your Quotes:
Patent Citations and the Value of
Innovations"](https://www.researchgate.net/profile/Manuel-Trajtenberg/publication/24048715_A_Penny_for_Your_Quotes_Patent_Citations_and_the_Value_of_Innovations/links/0a85e5331821349e9a000000/A-Penny-for-Your-Quotes-Patent-Citations-and-the-Value-of-Innovations.pdf)
(RAND Journal of Economics). Studying computed tomography scanners, he
showed that citation-weighted patent counts follow the social value of
innovations much better than raw counts do. The work that followed,
collected in the volume edited by Jaffe and Trajtenberg (2002),
[*Patents, Citations, and Innovations: A Window on the Knowledge
Economy*](https://mitpress.mit.edu/9780262600651/patents-citations-and-innovations/)
(MIT Press), treats citations as traces of knowledge flows between
inventors.


> A patent count shows how much a firm or an industry files. Forward
> citations show who builds on that technology later, and from which
> fields. For a company, this points to the neighbouring fields that
> draw on its technology and to the ones worth watching for new
> competitors or partners. For an analyst or an investor, it shows
> whether a portfolio is cited mostly from its own field or from
> several fields. The two groups in this post differ in this way:
> electronics patents are cited mostly by more electronics and
> computing patents, while health patents are also cited from
> diagnostics, surgery and analysis. The figures describe where
> citations land, not how much a technology is worth.

This post uses the idea differently. Instead of weighting each patent
by the forward citations it receives, I ask where those citations come
from: which applicants and which technical fields cite the patents in
later families, and whether this differs between industries. I compare
two groups of European firms, one in electronics and one in health.

## What TechLand adds to a citation count

Trajtenberg collapses the citations of a patent into one number.
TechLand keeps their structure, so the same data can answer a
different question: who builds on a technology, and from which field.

- **Patent families, not single patents.** An invention filed at
  several offices counts once, so citing activity is not inflated by
  duplicate filings.
- **A fixed window.** Only citing families first filed within four
  years after the earliest filing date of the cited family are
  counted, so older and newer patents are measured over the same time
  span.
- **Citing applicants and citing IPC classes.** For each set of
  patents, TechLand reports which applicants and which IPC classes
  appear among the forward-citing families, with their share of all
  citing families.
- **Priority years.** Every date is the earliest filing date of the
  family, the date closest to the invention. In the citation views,
  the year is that of the cited family, and its citers are the
  families first filed in the four years that follow.

## Data and groups

The firms come from the European Commission's [EU Industrial R&D
Investment Scoreboard](https://iri.jrc.ec.europa.eu/data), which ranks
the top EU R&D investors each year. I kept firms that appear in at
least 18 of the 20 editions from 2006 to 2025, so the groups consist
of persistent R&D investors. They describe established incumbents, not
new entrants, and firms that were acquired or dropped out are missing.

Each firm was matched by hand to its applicant names in TechLand.
Large firms file under several names, so I searched the main variants
I could identify, for example two for Ericsson, two for Nokia and five
for Bayer. The sector of a firm is the Scoreboard's own label in its
most recent edition:

- **Electronics, 35 firms:** electronic and electrical equipment,
  technology hardware and semiconductors, and telecom equipment.
- **Health, 26 firms:** pharmaceuticals, biotechnology and health care
  equipment.

Patents are EP publications with a priority year of 2004 or later:
36,036 for electronics and 5,007 for health. Both groups are uneven.
Ericsson, Siemens and Nokia account for roughly three quarters of the
electronics patents (counted by applicant name), and Bayer, with five
applicant names, is about 30% of the applicant-name counts in the
health group. I left out Bayer's crop science and materials science
names. BAYER IP GMBH and BAYER AG hold patents for all Bayer divisions
and remain, so some agricultural patents are still in the group.

## Electronics citations concentrate, health citations spread out

Electronics technology is cited from a narrower set of fields than the
group patents in, while health technology is cited from a wider one.
The table compares the class mix of each group's own patents with the
class mix of the families that cite them. Shares are computed over IPC
class assignments, so a patent or family with several classes counts
once in each.

| Measure | Electronics | Health |
| --- | --- | --- |
| Patents (EP, priority year 2004 or later) | 36,036 | 5,007 |
| Home sections | H and G | A and C |
| Share outside the home sections, own patents to citing families | 16.1% to 10.8% | 14.7% to 19.3% |
| Share of the three largest classes, own to citing | 38.3% to 47.7% | 31.6% to 29.9% |

In electronics, wireless and digital transmission dominate both sides.
H04W is 17.3% of the group's own patents and 22.0% of the citing
families, H04L is 15.9% and 18.0%, and G06F is 4.4% and 7.8%. Sections
H and G together rise from 83.9% of the own patents to 89.2% of the
citing families.

In health, the largest classes are similar on both sides (A61K is
12.5% of own patents and 11.8% of citing families, A61M is 11.1% and
10.9%), but the citing families reach further. Section G rises from
6.9% to 9.7% and section H from 0.9% to 2.0%, while chemistry (section
C) falls from 32.4% to 30.5%.

I read this as follows. Electronics patents are mostly cited by more
electronics and computing patents. Health patents are cited by
neighbouring fields such as diagnostics, surgery and analysis. This
describes where citations come from, not which technology is worth
more. Part of the electronics result also reflects the weight of
Ericsson and Nokia, which patent mainly in telecommunications.

{{< citfig fig="1" >}}

*Figure 1. Share of the twelve classes with the largest combined
weight among the group's own patents and among the forward-citing
families, for each group. Shares are computed over IPC class
assignments.*

## Which classes are cited more or less than the group patents in them

A simple ratio shows where citations land: the share of a class among
the citing families divided by its share among the group's own
patents. A ratio above 1 means the class is more present among the
citers than in the group's own portfolio. For example, a ratio of 1.78
means the class is 1.78 times more present among the citers than among
the group's own patents. The tables list the four largest and the four
smallest ratios among classes with at least 0.7% of the own patents.

### Electronics

| Class | Field | Own patents | Citing families | Ratio |
| --- | --- | --- | --- | --- |
| H04N | Pictorial communication | 1.5% | 2.7% | 1.78 |
| G06F | Digital data processing | 4.4% | 7.8% | 1.77 |
| H04J | Multiplex communication | 1.1% | 1.9% | 1.75 |
| H04B | Transmission | 5.1% | 6.9% | 1.34 |
| H02H | Protective circuit arrangements | 0.8% | 0.3% | 0.36 |
| H01R | Electric connectors | 1.0% | 0.4% | 0.35 |
| H01H | Electric switches | 2.2% | 0.6% | 0.26 |
| H02G | Installation of cables and lines | 0.8% | 0.2% | 0.24 |

### Health

| Class | Field | Own patents | Citing families | Ratio |
| --- | --- | --- | --- | --- |
| A61B | Diagnosis and surgery | 3.2% | 4.1% | 1.30 |
| A01P | Biocidal activity of chemical compounds | 1.4% | 1.8% | 1.29 |
| G01N | Analysis of materials | 2.2% | 2.7% | 1.24 |
| A61N | Electrotherapy and radiation therapy | 1.2% | 1.4% | 1.17 |
| C12N | Microorganisms and enzymes | 7.1% | 5.5% | 0.78 |
| C08G | Macromolecular compounds (for example polyurethanes) | 1.5% | 1.0% | 0.71 |
| A61F | Implants, prostheses, bandages | 6.3% | 4.4% | 0.69 |
| A61L | Sterilisation, materials for implants | 1.8% | 1.2% | 0.67 |

In electronics, the over-cited classes are communication and data
processing, and the under-cited ones are switches, cables, connectors
and protection circuits, the parts of the portfolio closest to power
and industrial equipment. In health, diagnosis and surgery, biocidal
compounds, analysis and radiation therapy are cited more than they are
patented, while microorganisms and enzymes, polymers, implants and
sterilisation materials are cited less. The biocide result comes from
agricultural patents that remain in the group through the Bayer names
that cover all divisions. Taken with the first result, health patents
are cited from diagnostics and measurement as well as from drugs and
chemistry.

Citation habits differ between fields, so these ratios describe where
citations land and are not a ranking of value.

{{< citfig fig="2" >}}

*Figure 2. Ratio of citing share to own share: the eight highest and
the eight lowest ratios among classes with at least 0.7% of the
group's own patents. Bars start at 1, where a class has the same
weight on both sides.*

## Shares by priority year, up to 2019

Up to the 2019 priority year, the class mix of the citing families
changes gradually, with a few clear trends. Each year below is the
priority year of the cited patents, and their citers are the families
filed in the following four years. I stop at 2019 because the window
of later priority years is incomplete (see the limits below).

In electronics, among the families citing patents of priority year
2007, 22.6% carry H04W, against 28.9% for 2009 and 28.2% for 2019.
H04L goes from 25.2% to 21.8%, G06F from 14.3% to 10.0% and H04B from
13.6% to 7.2%. Wireless stays high, while computing and general
transmission lose weight.

In health, A61K goes from 20.7% in 2007 to 14.0% in 2019 and C07D from
11.8% to 8.8%. Devices and diagnostics roughly keep their share: A61M
goes from 13.6% to 14.8% (peaks of 16.8% in 2013 and 2015) and A61B
from 7.8% to 8.1%. C12R, a class used for indexing microorganisms,
goes from 0.2% to 1.7% (2 families in 2007, 55 in 2019). The mix moves
away from drugs and chemistry.

Among the named citers of the electronics patents, Huawei goes from
0.02% of the families citing 2008 patents to 1.47% for 2019 patents,
and Vivo from 0.01% (2014) to 0.93% (2019). Samsung falls from a peak
of 1.80% for 2014 patents to 0.57% for 2019, and IBM from 1.98% (2007)
to 1.57% (2019). For health, citing applicants are spread over many
small names and the 1,000 largest named citers cover only 9.5% of the
citing families, so I do not draw an applicant story there.

{{< citfig fig="3" >}}

*Figure 3. Share of the citing families carrying selected IPC classes,
by priority year of the cited patents, for each group (upper panels),
and number of citing families per priority years (lower panels).*

## What the citation structure shows

For these two groups, forward citations come from different places.
Electronics patents are cited mostly by other electronics and
computing patents, and the citing families sit even more in
telecommunications and data processing than the firms' own portfolios
do. Health patents are cited from a wider range of fields, with
diagnostics, surgery and analysis weighing more among the citers than
among the firms' own patents. Across the priority years up to 2019 the
health mix moves away from drugs and chemistry, while wireless stays
high in electronics.

A citation count tells how much a technology is built upon. The
structure tells by whom and from which field, which a single number
hides. This is a description of where citations land, not a ranking of
value.

## Limits and how to read the figures

- **Recent years are incomplete** because citing families need time to
  be published, so the shares in this post stop at 2019. For strategy,
  the latest citing families are still worth looking at one by one.
  The TechLand interface shows them, and they can reveal new
  applicants or technologies that start to build on a patent before
  the statistics are stable.
- **No self-citation flag.** Citations from a firm’s own later patents
  are not separated. Matching the citing names with the groups’ own
  applicant names gives a lower bound of 2.0% of the citing families
  in electronics and 1.0% in health, so self-citation is small in
  these data. [do we need it, if so, then a simple explication]
- **Corporate changes.** Applicant names follow the legal entity at
  filing. Turbine classes almost disappear from the electronics own
  patents after 2016 (F01D assignments fall from 63 in 2015 to 7 in
  2018, and F03D is absent from 2017), when Siemens reorganised its
  wind and gas turbine businesses. 
- **A mixed health group.** The health group combines pharmaceuticals,
  medical devices, enzymes (Novozymes) and dialysis (Fresenius Medical
  Care), and some Bayer patents are agricultural. The comparison
  describes this group of firms, not a single industry.
- **What a citation means.** Many citations are added by patent
  examiners, and citation practices differ between patent offices, so
  a citation shows that a later application is related to an earlier
  one, not that its inventors used it. The findings are descriptive
  and do not explain why the patterns arise.

## What comes next
The previous post combined patent counts with R&D spending from the EU
Industrial R&D Investment Scoreboard, in the spirit of Griliches. This
post follows with the forward citation of the health and electronics
sectors' patents. The next one stays with citations but looks at them
as a network. Various aspects of a patent can be aggregated
(applicants, IPC classes etc) become nodes and citations become the
links between them. This allows questions that shares of citing
families cannot answer: which applicants or classes sit at the centre,
which groups cite each other most, and how the citation network
structure differs between electronics and health.

If you work with patent data and want to explore something like this
for your own sector or portfolio, [contact us](/#section5) or [DM me on
LinkedIn](https://www.linkedin.com/in/altayoz).
