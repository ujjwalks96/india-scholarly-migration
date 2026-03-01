# India Scholarly Migration Analysis
## An Independent Replication and Deep-Dive Extension of the MPIDR Scholarly Migration Database

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.9%2B-blue?style=flat-square&logo=python" />
  <img src="https://img.shields.io/badge/Jupyter-Notebook-orange?style=flat-square&logo=jupyter" />
  <img src="https://img.shields.io/badge/Data-Zenodo%2011145735-green?style=flat-square" />
  <img src="https://img.shields.io/badge/License-MIT-lightgrey?style=flat-square" />
  <img src="https://img.shields.io/badge/Status-Complete-brightgreen?style=flat-square" />
</p>

<p align="center">
  <strong>Ujjwal Kumar Swain</strong><br>
  Geospatial AI and Data Analyst, UNFPA India (Odisha State Office)<br>
  M.Sc. Geoinformation Science and Earth Observation, University of Twente / IIRS-ISRO
</p>

---

## Table of Contents

1. [The Work That Inspired This Project](#the-work-that-inspired-this-project)
2. [Why This Matters: Rationale](#why-this-matters-rationale)
3. [Aims and Objectives](#aims-and-objectives)
4. [Repository Structure](#repository-structure)
5. [How to Run](#how-to-run)
6. [Analytical Framework](#analytical-framework)
7. [Key Findings](#key-findings)
8. [Interpretations](#interpretations)
9. [Figures Produced](#figures-produced)
10. [Dependencies](#dependencies)
11. [References](#references)
12. [Acknowledgements](#acknowledgements)

---

## The Work That Inspired This Project

This repository would not exist without four landmark papers from the **Digital and Computational Demography group at the Max Planck Institute for Demographic Research (MPIDR)**, led by Professor Emilio Zagheni. These papers collectively represent the most rigorous and comprehensive effort ever made to measure international scholarly migration at scale using bibliometric data.

---

### Paper 1 - The Primary Data Foundation

> **Akbaritabar A., Theile T. and Zagheni E. (2024)**
> *Bilateral flows and rates of international migration of scholars for 210 countries for the period 1998-2020*
> **Scientific Data 11:816, 1-14**
> doi: [10.1038/s41597-024-03655-9](https://doi.org/10.1038/s41597-024-03655-9)
> Data: [10.5281/zenodo.11145735](https://doi.org/10.5281/zenodo.11145735) (CC-BY 4.0, Open Access)

This paper is the direct foundation of everything in this repository. The authors tracked affiliation changes of researchers indexed in both Scopus and OpenAlex to construct bilateral flow estimates for 210 countries across 23 years. Key innovations:

- First dataset to provide both country-level rates and bilateral corridor volumes simultaneously
- Cross-validation across two independent bibliometric databases, enabling reliability assessment
- Introduction of the padded population denominator for Net Migration Rate (NMR), preventing extreme values for micro-states with tiny scholar populations
- Full open data release on Zenodo under CC-BY 4.0, enabling replication and extension by any researcher worldwide

What makes this paper exceptional is its epistemological honesty: the authors are transparent about what affiliation-change data can and cannot measure, and they provide both database sources precisely so users can assess the robustness of any finding before building on it.

---

### Paper 2 - The Subnational Extension

> **Akbaritabar A., Danko M. J., Zhao X. and Zagheni E. (2025)**
> *Global subnational estimates of migration of scientists reveal large disparities in internal and international flows*
> **Proceedings of the National Academy of Sciences 122:15, e2424521122**
> doi: [10.1073/pnas.2424521122](https://doi.org/10.1073/pnas.2424521122) (Open Access)

This PNAS paper broke new ground by disaggregating scholar migration to the subnational level, revealing that national averages can mask enormous internal variation. It contains a critical observation about India that directly motivated the India-specific analysis in this repository:

> "India, at the country level, has a negative NMR. However, when zooming in on subnational regions, a more complex picture emerges. Some regions in India have a positive NMR."

This observation was stated but never systematically pursued in the paper. The India notebook in this repository addresses that gap at the country-level bilateral and temporal dimensions, as a step toward understanding what subnational complexity the national average conceals.

---

### Paper 3 - The Working Paper Precursor

> **Akbaritabar A., Theile T. and Zagheni E. (2023)**
> *Global flows and rates of international migration of scholars*
> **MPIDR Working Paper WP-2023-018**
> [mpidr.de/publications](https://www.mpidr.de/publications/details/?pubId=65730) (Open Access)

The working paper that preceded the Scientific Data publication. Reading this alongside the published paper reveals how the methodology evolved, particularly in the handling of OpenAlex coverage gaps for earlier years and the refinement of the NMR formula. Essential reading for anyone interested in the methodological development of this line of research.

---

### Paper 4 - The Economic Development Connection

> **Sanlitürk A. E., Zagheni E., Danko M. J., Theile T. and Akbaritabar A. (2023)**
> *Global patterns of migration of scholars with economic development*
> **Proceedings of the National Academy of Sciences 120:4, e2217937120**
> doi: [10.1073/pnas.2217937120](https://doi.org/10.1073/pnas.2217937120) (Open Access)

This companion PNAS paper asks what drives the patterns observed in the migration data: why do some countries consistently receive scholars while others consistently send them? The authors connect NMR trajectories to GDP per capita, research expenditure, and university quality rankings. The finding that NMR and economic development follow a nonlinear relationship, with middle-income countries showing the most outflow, is directly relevant to interpreting India's position at the upper boundary of this middle-income high-outflow zone.

---

## Why This Matters: Rationale

India is the world's most populous country and operates one of the largest scientific workforces in the Global South. It runs more than 1,000 universities, 40+ National Institutes of Technology, and 23 IITs. It produces more STEM graduates annually than almost any other country on earth. And yet, for over two decades, it has sent more scholars abroad than it has attracted from anywhere.

The Akbaritabar et al. dataset makes it possible, for the first time, to examine this brain drain not as a rough stylised fact but as a precisely measured, year-by-year, corridor-by-corridor empirical phenomenon. The questions that motivated this work are concrete:

- How bad is it really, and has it improved or worsened over 23 years?
- Is India unique among its large emerging economy peers, or is this a shared pattern?
- Which bilateral corridors drive the net loss, and are any showing signs of reversal?
- Is there any signal of increasing return migration or circulation?
- Does India function as a scholarly hub within South Asia, or do its flows entirely bypass the region?
- How unequal is scholar migration within Asia, and where does that inequality sit?

These questions matter for Indian research policy, for the design of diaspora engagement programmes, and for understanding whether decades of investment in domestic research infrastructure have produced measurable changes in scholarly mobility patterns.

---

## Aims and Objectives

### Primary Aim

To independently replicate the core descriptive results of Akbaritabar, Theile and Zagheni (2024) and to extend that analysis with a focused, multi-dimensional investigation of India's position in global scholar migration flows from 1998 to 2020.

### Specific Objectives

| # | Objective | Notebook | Section |
|---|-----------|----------|---------|
| 1 | Reproduce the global NMR distribution and confirm data coverage | Replication | 3 |
| 2 | Cross-validate Scopus and OpenAlex estimates and diagnose disagreement | Replication | 4 |
| 3 | Replicate temporal NMR trends for major sender and receiver country groups | Replication | 5 |
| 4 | Build an interactive animated choropleth extending the paper's static maps | Replication | 6 |
| 5 | Identify and visualise the top bilateral corridors globally | Replication | 7 |
| 6 | Track India's annual rank among all net-sending countries 1998-2020 | India | 3 |
| 7 | Compare India's NMR trajectory against all other BRICS economies | India | 4 |
| 8 | Quantify bilateral asymmetry for India's top 12 partner corridors | India | 5 |
| 9 | Measure within-region inequality in scholar migration using Gini coefficients | India | 5.5 |
| 10 | Decompose India's corridor mix across three temporal periods | India | 6 |
| 11 | Construct a return migration proxy using the bilateral USA-India flow ratio | India | 6.5 |
| 12 | Test whether India functions as a scholarly hub within South Asia | India | 7 |

---

## Repository Structure

```
india-scholarly-migration/
|
+-- scholarly_migration_replication.ipynb     Replication of Akbaritabar et al. (2024)
+-- india_scholarly_migration.ipynb           India deep-dive (7 analyses, 8 figures)
+-- README.md                                 This file
+-- LICENSE                                   MIT License
+-- .gitignore
|
+-- figures/                                  Generated at runtime (not committed to git)
|   +-- fig1_global_nmr_distribution.png
|   +-- fig2_scopus_vs_openalex.png
|   +-- fig3_temporal_trends.png
|   +-- fig4_global_coverage.png
|   +-- fig5_interactive_world_map.html       Animated choropleth with year slider
|   +-- fig6_top_corridors.png
|   +-- fig7_corridor_trends.png
|   +-- india_nmr_trend.png
|   +-- india_corridors.png
|   +-- india_regional_heatmap.png
|   +-- india_flow_map.html                   Interactive flow map
|   |
|   +-- india/
|       +-- fig1_india_ranking.png
|       +-- fig2_brics_comparison.png
|       +-- fig3_corridor_asymmetry.png
|       +-- fig4_temporal_decomposition.png
|       +-- fig5_regional_hub.png
|       +-- fig_gini_regions.png
|       +-- fig_return_migration_proxy.png
|       +-- india_dashboard.html              Interactive 4-panel Plotly dashboard
|
+-- data/                                     Created at runtime, not committed to git
    +-- raw/
    +-- processed/
        +-- scopus_country.parquet
        +-- scopus_flows.parquet
```

---

## How to Run

### Option 1: Google Colab (zero setup, recommended)

Open either notebook in Colab and run all cells top to bottom. The notebooks install all dependencies and download all data automatically from Zenodo.

**Run order matters:**

```
1. Run scholarly_migration_replication.ipynb first
   Downloads approx 500 MB from Zenodo
   Generates all replication figures
   Exports processed Parquet files to data/processed/

2. Run india_scholarly_migration.ipynb second
   Loads Parquet files (fast path, under 1 second)
   Falls back to raw CSVs if Parquet files not found
   Falls back to fresh Zenodo download if nothing found
   Generates all India analysis figures
```

Each notebook ends with a ZIP export cell that bundles all figures and triggers a browser download. Run that cell last.

### Option 2: Local environment

```bash
git clone https://github.com/ujjwal-swain/india-scholarly-migration
cd india-scholarly-migration

python3 -m venv venv
source venv/bin/activate

pip install pandas numpy matplotlib seaborn plotly kaleido scipy pycountry tqdm pyarrow requests geopandas jupyter

jupyter notebook
```

---

## Analytical Framework

### The Net Migration Rate

The central measure throughout both notebooks is the Net Migration Rate as defined in the paper:

```
NMR = (in-migrations - out-migrations) / padded_scholar_population  x  1,000
```

Positive NMR means net brain gain. Negative NMR means net brain drain.
The padded denominator applies a minimum floor to prevent extreme values for micro-states.

### Data

| Source | Coverage | Notes |
|--------|----------|-------|
| Scopus bilateral flows | 210+ countries, 1996-2022 | Primary source for all analysis |
| OpenAlex country rates | 180+ countries, 1998-2022 | Used for cross-validation only |

All analysis is filtered to 1998-2020 to match the paper's study window.

### A Note on the Cross-Validation Result

The raw Pearson correlation between Scopus and OpenAlex is 0.09, which sounds alarming. After investigation, all top-10 discrepancies are micro-states and dependent territories (Kiribati, Montserrat, San Tome and Principe, Aruba, San Marino, Andorra). These have negligible scholar populations where a single affiliation change creates massive rate swings in one database but not the other. After clipping and excluding these, Spearman r = 0.46, indicating moderate rank-order agreement on the countries that matter analytically. All subsequent analysis uses Scopus only.

---

## Key Findings

### From the Replication Notebook

**Global NMR distribution confirms the paper's core claim.** The distribution is right-skewed: a small group of wealthy English-speaking countries (USA, UK, Australia, Switzerland, Canada) have strongly positive NMR while the large majority of countries have small negative values. Brain drain is the norm, not the exception, in the global academic system.

**Scopus and OpenAlex agree on what matters.** Disagreements between the two databases are concentrated entirely in micro-states and dependent territories. For all analytically important countries the two sources tell a consistent directional story.

**The global scholar population has grown substantially.** From a few million tracked scholars in 1998 to tens of millions by 2020, reflecting both real growth and expanding database coverage. Annual migration events have grown in parallel.

**The USA-China and USA-India corridors dominate globally.** By total volume across 1998-2020, these are among the largest bilateral corridors in the entire dataset. Both reflect the gravitational pull of the US research system on Asian scientific talent.

### From the India Analysis Notebook

**India is a persistent and consistent net sender of scholars.** Its NMR has been negative in every single year from 1998 to 2020 without exception. There is no year in which India was a net receiver.

**India's global rank has not improved.** Fluctuating between approximately rank 25 and rank 90 out of 210 countries (where rank 1 means strongest net sender), India is consistently in the bottom 25% by NMR. The drain worsened sharply in the early 2000s, partially recovered around 2013, then deteriorated again toward 2020.

**India stands apart within BRICS.** India has the most persistently negative average NMR among all five BRICS economies. China's NMR has improved dramatically and trends toward zero by 2020. Brazil shows a slight positive NMR. Only India shows no sustained improvement across the entire study period.

| BRICS Country | Average NMR 1998-2020 | Trend |
|---------------|-----------------------|-------|
| India | Most negative | Persistently negative, no improvement |
| Russia | Moderately negative | Slowly improving |
| South Africa | Near zero, volatile | No clear trend |
| China | Near zero | Strong improvement, approaching balance |
| Brazil | Slightly positive | Mild net receiver throughout |

**India loses scholars to every major partner without exception.** The corridor asymmetry analysis shows net scholar losses to all 12 top bilateral partners. There is no partner country from which India gains more scholars than it sends. The USA represents the largest absolute net loss. The UK shows the smallest asymmetry, suggesting the most genuine bidirectional exchange. Saudi Arabia and South Korea appear prominently, destinations that are often overlooked in conventional brain drain narratives.

**Scholar migration within Asia is highly unequal.** The Gini coefficient of net migration rates across Asian countries averages above 0.6 across the study period. A small number of countries (Japan, Singapore, South Korea as receivers; India as the dominant sender) drive the regional pattern. This inequality is not declining over time.

**India's destination mix is diversifying but the loss continues.** USA share of India's outflows fell from approximately 16% in 1998-2005 to approximately 7% in 2013-2020. The USA remains the top destination in all three periods, but South Korea and Saudi Arabia have grown substantially. Diversification of destinations does not mean reduction of outflow.

**Some scholars are returning.** The USA-to-India return ratio averages between 0.3 and 0.5 across the study period. Roughly one scholar is recorded returning for every two to three who leave for the USA. India's diaspora is not an entirely one-way pipeline, though the net flow remains strongly outward.

**India is not a South Asian scholarly hub.** Intra-South Asian flows account for less than 1% of both India's inflows and outflows. Despite rhetoric about regional academic cooperation, scholarly flows in South Asia bypass the region entirely and connect individual countries directly to global hubs. India and its South Asian neighbours do not substantially exchange scholars with each other.

---

## Interpretations

### The structural nature of India's position

The persistence of a negative NMR across 23 years, through three global economic cycles, and despite repeated domestic research investments suggests something structural rather than cyclical. India's position in the global academic hierarchy, where institutional prestige, research funding density, and quality-of-life factors create persistent pull forces toward a small number of wealthy countries, is not easily shifted by domestic policy alone.

### Why China improved and India has not

China's NMR improvement toward zero is one of the most striking patterns in the dataset. It likely reflects a combination of explicit return migration incentive programmes, massive increases in domestic research funding, rapid rise of Chinese universities in global rankings, and the growth of domestic publishing markets that reduced the career premium of foreign affiliation. India has pursued analogous policies but has not achieved comparable results in this data. Whether the difference reflects policy design, implementation quality, or deeper structural economic factors is beyond the scope of this analysis but is a question the data makes sharply visible.

### The Gulf and Korea corridors are underappreciated

Policy discussions about India's brain drain almost always centre on the USA and UK. The data shows that South Korea and Saudi Arabia are significant and growing destinations, particularly in the most recent period. The Gulf corridor reflects academic hiring at rapidly expanding universities in Saudi Arabia and the UAE. The Korea corridor reflects research collaborations and postdoctoral mobility. Neither appears prominently in Indian policy discussions, and neither is typically addressed in diaspora engagement strategies.

### The return ratio as an encouraging but insufficient signal

A return ratio that stays between 0.3 and 0.5 rather than collapsing toward zero means there is a real and ongoing return flow. Whether these returning scholars build lasting research networks, bring funding, and strengthen domestic institutions or represent short-term visits with limited lasting impact is not determinable from this data. The flow exists and is measurable. What it produces institutionally is a separate empirical question.

### South Asia's missing academic community

The near-zero intra-South Asian flow share is the finding with the most direct policy relevance beyond India itself. Despite SAARC research exchange agreements, India's stated ambitions as a regional knowledge hub, and the geographic proximity of several substantial research systems (Bangladesh, Nepal, Sri Lanka), the data shows essentially no meaningful intra-regional scholarly exchange. Building genuine regional academic networks would require sustained institutional investment that the current data suggests has simply not occurred.

---

## Figures Produced

### Replication Notebook

| Figure | What it shows |
|--------|--------------|
| fig1_global_nmr_distribution.png | NMR histogram and top-20 senders and receivers globally |
| fig2_scopus_vs_openalex.png | Cross-validation scatter with OLS fit and Pearson r |
| fig3_temporal_trends.png | NMR over time for 15 countries across three groups |
| fig4_global_coverage.png | Global scholar population and annual migration event counts |
| fig5_interactive_world_map.html | Animated choropleth 1998-2020 with play button and year slider |
| fig6_top_corridors.png | Top 20 bilateral corridors by total volume 1998-2020 |
| fig7_corridor_trends.png | Top 5 corridor time series with direct endpoint labels |
| india_nmr_trend.png | India NMR with shaded green and red fill regions |
| india_corridors.png | Top 10 inflows and outflows side by side |
| india_regional_heatmap.png | South and Southeast Asia NMR heatmap by country and year |
| india_flow_map.html | Interactive map of India outflow corridors, line thickness = volume |

### India Analysis Notebook

| Figure | What it shows |
|--------|--------------|
| fig1_india_ranking.png | Annual global rank (inverted axis) and NMR dual-panel chart |
| fig2_brics_comparison.png | Five BRICS countries NMR trajectories, India highlighted thicker |
| fig3_corridor_asymmetry.png | Diverging bar: net loss by partner country, all bars red |
| fig4_temporal_decomposition.png | Top 8 destinations per period across three historical eras |
| fig5_regional_hub.png | Donut charts: intra-South Asian vs global share of flows |
| fig_gini_regions.png | Gini inequality six-panel by UN macro-region 1998-2020 |
| fig_return_migration_proxy.png | IND-USA absolute flows and return ratio panel chart |
| india_dashboard.html | Interactive four-panel Plotly dashboard for presentations |

---

## Dependencies

| Package | Purpose |
|---------|---------|
| pandas >= 1.3 | Data manipulation and aggregation |
| numpy >= 1.20 | Numerical operations and Gini computation |
| matplotlib >= 3.4 | All static publication-quality figures |
| seaborn >= 0.11 | Visual theme (whitegrid) |
| plotly >= 5.0 | Interactive HTML figures and dashboard |
| kaleido >= 0.2 | Plotly static image export backend |
| scipy >= 1.7 | Pearson and Spearman correlation |
| pycountry | ISO 3166 alpha-2 to alpha-3 code conversion |
| tqdm | Download progress bars |
| pyarrow | Parquet file read and write |
| requests | HTTP requests to Zenodo REST API |
| geopandas | Spatial data support |

```bash
pip install pandas numpy matplotlib seaborn plotly kaleido scipy pycountry tqdm pyarrow requests geopandas
```

---

## References

Akbaritabar A., Theile T. and Zagheni E. (2024). Bilateral flows and rates of international migration of scholars for 210 countries for the period 1998-2020. *Scientific Data* 11:816, 1-14. doi: 10.1038/s41597-024-03655-9

Akbaritabar A., Danko M. J., Zhao X. and Zagheni E. (2025). Global subnational estimates of migration of scientists reveal large disparities in internal and international flows. *Proceedings of the National Academy of Sciences* 122:15, e2424521122. doi: 10.1073/pnas.2424521122

Akbaritabar A., Theile T. and Zagheni E. (2023). Global flows and rates of international migration of scholars. MPIDR Working Paper WP-2023-018. Max Planck Institute for Demographic Research, Rostock.

Sanlitürk A. E., Zagheni E., Danko M. J., Theile T. and Akbaritabar A. (2023). Global patterns of migration of scholars with economic development. *Proceedings of the National Academy of Sciences* 120:4, e2217937120. doi: 10.1073/pnas.2217937120

---

## Acknowledgements

This analysis was made possible entirely by the open science practices of the Digital and Computational Demography group at the Max Planck Institute for Demographic Research. Aliakbar Akbaritabar, Tom Theile, and Emilio Zagheni not only produced a methodologically rigorous dataset but released it openly under CC-BY 4.0, enabling exactly this kind of independent replication and extension from anywhere in the world.

The fact that a researcher at a UNFPA state office in Odisha can independently reproduce, interrogate, and extend results from one of the world's leading demographic research institutes is itself a demonstration of what open data practices make possible.

---

## License and Data Rights

The code in this repository is released under the MIT License.

The underlying scholarly migration data is released by the original authors under Creative Commons Attribution 4.0 (CC-BY 4.0). You may use and redistribute it with attribution to Akbaritabar, Theile and Zagheni (2024).

---

<p align="center">
  <em>Open data enables open science. This project is a small demonstration of that principle.</em><br><br>
  Made with care in Bhubaneswar, Odisha.
</p>
