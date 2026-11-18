---
title: "Another view of the technological landscape: citation network analysis"
date: 2026-11-18
description: "A citation network view of the patents of EU electronics R&D investors, by IPC class and by applicant, built with TechLand and Gephi."
tags: ["patents", "citation network analysis", "Gephi", "TechLand", "electronics"]
---

A high citation count does not tell the same thing as a central
position in the citation network built from patent references. Patents
and their citations can also be grouped by applicant, inventor, IPC
class or other patent information. Such a network shows who cites
whom, and the position and influence of each node within it. In the
previous posts I followed Griliches's approach to relate R&D spending
to patents, and then Trajtenberg's views to analyze the forward
citations of patents. In this post I turn to citation network
analysis, using our own platform,
[TechLand](https://www.metis-analytica.com/techlandfeatures).

For this series I selected firms from the European Commission's [EU
Industrial R&D Investment
Scoreboard](https://iri.jrc.ec.europa.eu/data), which ranks the top EU
R&D investors each year. I kept firms that appear in at least 18 of
the 20 editions from 2006 to 2025, so the groups consist of persistent
R&D investors. This post analyzes the patents of the electronics firms
only.

> This post uses the patents of the electronics firms from the EU
> Industrial R&D Investment Scoreboard. The patent data comes from
> TechLand, and the citation network analysis groups the patents by
> IPC class and by applicant name. The analysis shows the position of
> each technology class and each applicant within the network of
> knowledge flows built from patent citations. This analysis gives
> another view of the technology landscape of top EU R&D investor
> firms in electronics.

A citation network starts from the reference section of each patent.
Its entries are either other patents or non-patent literature,
generally scientific papers. TechLand builds the network from patent
families and the citations between them. Network analysis then
provides measures that make it possible to look at patents through a
network lens. It does not replace counts or forward citations. It is
another view of the same landscape, seen from a different angle. For
researchers, TechLand provides two types of networks: citation
networks, which can be aggregated by applicant, inventor,
[IPC](https://ipcpub.wipo.int/) or
[CPC](https://www.cooperativepatentclassification.org/cpcSchemeAndDefinitions/table)
class, [technology
field](https://www.wipo.int/edocs/mdocs/classifications/en/ipc_ce_41/ipc_ce_41_5-annex1.pdf)
or
[NACE2](https://ec.europa.eu/eurostat/web/products-manuals-and-guidelines/-/ks-ra-07-015),
and bi-modal networks, namely co-authorship and co-classification
networks, which are transformed into mono-modal networks for analysis.

## How the network is built

I started from the electronics firms of the 2025 Scoreboard and
searched by applicant name in TechLand (Ericsson, Nokia, Siemens,
ASML, Infineon and STMicroelectronics are among them). I call the
result the core patent families, and some of them have co-applicants
such as IBM. To these families I added every family that one of them
cites (backward citations), or that cites one of them (forward
citations), within four years of its filing date. This limit gives
every family a comparable citation window and removes the advantage
that older patents would otherwise gain by accumulating citations over
time.

The network is built on patent families, not on single patents. A
family groups the patents filed at different offices for the same
invention, for example at the EPO, the USPTO and in several national
offices. Without this step one invention would count as many patents,
and its citations would be counted many times. With families, one
invention counts once, and the citations received by all its members
are added together. The links between the nodes then show inventions
citing inventions, not the same invention repeated in each country.

Once the patents are collected, it is known which patent cites which
patent, and the patents can be grouped by the information they
contain. In this post the first network groups them by IPC class and
the second by applicant name. Each group is treated as a node. Two
nodes are linked when patents of one cite patents of the other, and
the link is heavier (edge weight) when this happens often. TechLand
shows the network and also exports the links as a table, and
[Gephi](https://gephi.org) turns the table into a picture.

The practical steps are short. The network data is exported from
TechLand and several measures are calculated in Gephi: PageRank for
the influence of a node, betweenness for its bridging position between
groups, and modularity for the groupings. The network is then explored
visually. The colours in both figures come from the modularity
calculation in Gephi, which uses the method of Blondel, Guillaume,
Lambiotte and Lefebvre (Fast unfolding of communities in large
networks, Journal of Statistical Mechanics: Theory and Experiment,
2008, 10, P10008). For network graphics, I have not found a better
tool than Gephi. It is free and open source software and handles
complex networks very well.

## Technology view: IPC classes

{{< zoom_figure src="/images/blog/electronics_eu_IPC.png" alt="Citation network of IPC classes of EU electronics R&D investors" caption="Figure 1. Citation network of IPC classes. Size shows PageRank, colour shows the groupings found by Gephi: communication and computing (blue), semiconductors and materials (green), other classes (pink). Click the figure to enlarge." >}}

Communication and computing (H04L digital information transmission,
H04W wireless networks, G06F digital data processing, H04B
transmission) form the largest block with more than half of all
forward citations, and semiconductors and materials (H01L
semiconductor devices, C23C coating of metals, G03F photolithography)
form the second. A looser third group gathers power, optics, turbines
and a long tail of mechanical classes. The six most cited classes all
sit in the first two blocks, and the links inside each block are
visibly denser than the links between them.

The table gives the ten most cited IPC classes and the ten classes
with the highest PageRank. Unlike the applicants below, the two
rankings almost agree. The top six are identical, H04J and H04M swap
seventh and eighth place, and H01J (10th by citations, 15th by
PageRank) and G02B (13th and 10th) each appear in only one of the two
top tens.

{{< sortable_table >}}

| IPC class | Rank by forward citations | Rank by PageRank |
| --- | --- | --- |
| H04L | 1 | 1 |
| H04W | 2 | 2 |
| H01L | 3 | 3 |
| G06F | 4 | 4 |
| H04B | 5 | 5 |
| C23C | 6 | 6 |
| H04J | 7 | 8 |
| H04M | 8 | 7 |
| H04N | 9 | 9 |
| H01J | 10 | 15 |
| G02B | 13 | 10 |

{{< /sortable_table >}}

Some classes matter more as connectors than by volume. Control systems
(G05B) and materials analysis (G01N) are not among the ten most cited
classes of the table (they rank 17th and 31st), but they rank second
and fifth by betweenness, which means that many of the shortest paths
between other classes run through them. A count would not show this.

A last pattern concerns direction. Chemistry and glass classes such as
C07F and C03C are cited several times more often than they cite, which
suggests they supply knowledge to others. Classes such as H01P
(microwave components) and G06N (computing models) show the opposite.
Most of the largest classes cite about as often as they are cited, so
they neither mainly supply nor mainly receive knowledge.

## Firm view: applicants

{{< zoom_figure src="/images/blog/electronics_eu_applicant.png" alt="Citation network of applicants in the patents of EU electronics R&D investors" caption="Figure 2. Citation network of applicants, filtered to the better connected ones. Size shows PageRank, colour shows the groupings found by Gephi: telecom and mobile (blue), networking (green), software and devices (red), industrial firms (cyan), semiconductor equipment makers (brown and gold). Click the figure to enlarge." >}}

The groupings among applicants are best read as neighbourhoods rather
than segments. Telecom and mobile (Qualcomm, Ericsson, Nokia, Samsung,
LG, together with IBM and Intel) is the largest. Networking (Cisco),
software and devices (Microsoft, Apple) and industrial firms (GE,
Siemens, Texas Instruments) make up most of the rest. Semiconductor
equipment forms two small groups: Applied Materials with its many
small citing applicants, and ASML with Canon and Nikon. Applied
Materials and its citing applicants sit apart on the far left, tied to
the rest by a few long links, which fits the separate semiconductor
block of the first figure.

The picture shows the neighbourhood of the patents I searched, not the
whole industry. The telecom group is large partly because Ericsson and
Nokia are among the searched firms, and the equipment group partly
because ASM, ASML and a few others are.

Most cited is not the same as most central. The table gives the rank
of some applicants by forward citations and by PageRank, computed on
the full exported network.

{{< sortable_table >}}

| Applicant | Rank by forward citations | Rank by PageRank |
| --- | --- | --- |
| Applied Materials | 1 | 17 |
| ASM | 2 | 12 |
| IBM | 3 | 2 |
| Tokyo Electron | 4 | 81 |
| Samsung Electronics | 5 | 6 |
| Cisco | 6 | 7 |
| Microsoft | 7 | 4 |
| Qualcomm | 8 | 1 |
| Nokia | 9 | 3 |
| Intel | 10 | 13 |
| Ericsson Telefon | 12 | 5 |
| LG Electronics | 15 | 8 |
| GE | 17 | 9 |
| Apple | 13 | 10 |

{{< /sortable_table >}}

The equipment makers are cited a lot, but by a relatively small number
of applicants citing them many times each. Applied Materials is cited
by about 150 different applicants, Qualcomm by about 600. PageRank
rewards the second pattern. Among the ten applicants with the highest
PageRank, only Nokia and Ericsson are EU firms of the Scoreboard
selection. The other eight are non-EU multinationals.

> The patents of these firms form two large technology blocks,
> communication and computing on one side, semiconductors and
> materials on the other, with a looser group of power, optics and
> mechanical classes around them. Citation counts and network position
> do not always agree, and that difference is where the network view
> adds something. Around these EU firms, many of the most central
> applicants are global multinationals such as IBM, Qualcomm, Samsung
> and Microsoft, all connected through the network to the EU firms, so
> their patents sit in a worldwide network and not in a European one.

## What a network adds

Counts show how much a class or a firm is cited. The network also
shows where it sits: which blocks it belongs to, which classes connect
them, and which firms share a neighbourhood. For landscape work this
helps in deciding where to look more closely, whom to benchmark
against, and which technologies lie between two areas of interest. It
also puts the firms in context. The EU firms we started from are
linked to many other enterprises, and multinationals such as IBM,
Samsung and Microsoft are all connected to them through the network. A
count of patents or citations does not show that the position of these
firms is shaped by a global neighbourhood.

For a technology transfer office, the network shows which technologies
sit next to a university's own and which firms work in the same
neighbourhood, so it is easier to choose partners or licensees. For
M&A teams, it shows which firms hold a central position in a field and
which sit at its edge, which is a different question from who owns the
most patents. For venture capital and other investors, it shows where
a young technology connects to established blocks, which classes link
two areas, and how a target compares with its neighbours before the
detailed work starts. In each case the network helps to decide where
to look first, and it does not replace the analysis that follows.

## Limits

- Citations are counted over four years after filing, so recent
  patents have had little time to be cited.
- Exports are capped at 50,000 edges. The applicant network loses some
  edges of low weight. The IPC network loses none.
- The figures show a filtered core to keep the view readable, while
  the full network has many more nodes and edges. All calculations use
  the full data, and the filtering only affects the display.
- Groupings come from the modularity algorithm, which looks for sets
  of nodes that are linked more densely with each other than with the
  rest of the network. They are a way to read the network graph, not a
  classification of firms.

## Beyond IPC classes and applicants

IPC classes and applicant names are not the only two ways to group
patents in a citation network. The same export is available by
inventor, CPC class, technological field and NACE2 sector, in TechLand
and the Gephi steps stay the same. Each choice answers a different
question. CPC gives a finer technology map, NACE2 shows how industries
cite each other and inventors show whose work builds on whose.

The second type of network, co-authorship and co-classification, is
built differently. Its raw form is bi-modal, with patents on one side
and a second kind of node on the other, such as inventors, applicants,
or IPC and CPC classes. For analysis it is transformed into a standard
mono-modal (or uni-modal) network, in which all nodes are of one type.
Two inventors are linked when they signed the same patent, which shows
who works with whom. Two classes are linked when they are assigned to
the same patent, which shows which technologies are combined.

The two types answer different questions. Citation networks describe
the flow of knowledge: which technologies, applicants or inventors
build on which, and which of them hold a central or a bridging
position. Co-authorship networks describe collaboration: who works
with whom, which partners connect separate groups, and how
collaboration is spread across countries and regions.
Co-classification networks describe technology combinations: which
fields are used together, and where new combinations appear. Used side
by side, they let a researcher study how knowledge, people and
technologies are connected in the same set of patents. The network
measures can also be combined with other data, such as the financial
data of firms, which extends the analysis beyond patents. This kind of
research is iterative. A researcher checks which firms are in which
technology classes, looks at the portfolio of a firm, runs another
network analysis, and returns to the first view with a better
question. A full grasp of a technology landscape rarely comes in one
pass, and TechLand makes this iterative work simpler.

## What comes next

In the next posts I will show how to interpret these results for
strategic questions, such as those of technology transfer offices,
venture capital investors, technology managers and M&A teams.

If you would like a similar view for your sector or your portfolio,
you can contact us or send me a message on LinkedIn.
