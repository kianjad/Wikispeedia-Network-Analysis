# Wikispeedia Network Analysis

A network analysis of the [Wikispeedia](https://snap.stanford.edu/data/wikispeedia.html) hyperlink graph, exploring its structure, centrality, community organization, and statistical significance.

**Authors:** Jayden Gould, Harrison Funk, Elijah DiFuria, Kian Jadbabaei  
**Date:** March 2026  
**Language:** R (RMarkdown)

---

## Overview

Wikispeedia is an online game where players navigate from one Wikipedia article to another using only hyperlinks. This project treats the underlying hyperlink structure as a directed network — articles are nodes, hyperlinks are directed edges — and applies a range of network science techniques to characterize it.

The full network contains **4,592 nodes** and **119,882 directed edges** (density = 0.00569).

---

## Key Findings

- **Small-world properties:** Diameter of 9 and average path length of 3.18 within the largest strongly connected component, meaning most articles are reachable in just a few clicks.
- **Heavy-tailed degree distribution:** A small number of hub articles (e.g., *United States*, *United Kingdom*, *France*) dominate incoming links across all three centrality measures (degree, betweenness, eigenvector).
- **Strong community structure:** Louvain community detection achieved modularity Q = 0.663 on subgraphs and Q = 0.3722 on the full network, with communities aligning closely to known Wikipedia topic categories.
- **Statistically significant communities:** A Monte Carlo null model test across 1,000 Erdős–Rényi random graphs confirmed the observed modularity is far above chance (p ≈ 0).

---

## Repository Structure

```
├── wikispeedia-network-analysis.Rmd   # Full analysis source (RMarkdown)
├── wikispeedia-network-analysis.pdf   # Rendered report with all figures
├── links.tsv                          # Edge list (article → article hyperlinks)
├── categories.tsv                     # Article-to-category mappings
└── README.md
```

---

## Methods

| Step | Details |
|---|---|
| Data source | SNAP Wikispeedia dataset |
| Network type | Directed graph (igraph) |
| Subgraphs | 4 induced subgraphs, 200 nodes each (random sample) |
| Visualization | Fruchterman-Reingold, Kamada-Kawai, Circular layouts |
| Centrality | In-degree, betweenness, eigenvector centrality |
| Community detection | Fast Greedy, Louvain, Walktrap |
| Statistical test | Monte Carlo null model (1,000 Erdős–Rényi random graphs) |

---

## Network Metrics (Full Graph)

| Metric | Value |
|---|---|
| Nodes | 4,592 |
| Edges | 119,882 |
| Density | 0.00569 |
| Reciprocity | 0.221 |
| Global Clustering Coeff. | 0.1029 |
| Degree Assortativity | -0.0562 |
| Diameter (largest SCC) | 9 |
| Avg. Path Length (largest SCC) | 3.181 |

---

## Requirements

```r
install.packages(c("igraph", "dplyr", "Matrix", "knitr"))
```

To render the report:

```r
rmarkdown::render("wikispeedia-network-analysis.Rmd")
```

---

## Data Source

West, R. & Leskovec, J. — *Wikispeedia Navigation Paths*  
Stanford Network Analysis Project (SNAP): https://snap.stanford.edu/data/wikispeedia.html
