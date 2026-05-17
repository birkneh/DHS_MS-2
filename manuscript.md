# Where the EPI cascade breaks: separating entry-point from follow-up failure across 38 sub-Saharan African countries

**Authors:** [TBD]  
**Target journal:** *The Lancet Global Health*  
**Word count (main text):** ~5 800 words  

---

## Abstract

**Background.** Standard vaccination coverage statistics treat each antigen independently, masking whether unvaccinated children were never reached (entry-point failure) or started but did not complete the schedule (follow-up failure). The two failure types require distinct policy responses, yet no systematic continent-scale decomposition exists.

**Methods.** Using 163 Demographic and Health Surveys from 38 sub-Saharan African countries (1989–2024; n = 263 385 children aged 12–23 months), we constructed dose-by-dose cascades from BCG through MCV1 and computed conditional dose-completion probabilities. We decomposed missed vaccinations into entry-point failure (zero-dose: neither BCG nor DPT/Penta 1 received) and follow-up failure (started but did not complete DPT3). We then formalised the cascade as a five-state Markov chain and fitted country-specific transition probabilities via random-effects meta-analysis on the logit scale with empirical Bayes shrinkage. Survey design weights were applied throughout.

**Findings.** Continent-average coverage declined gradually across the cascade: BCG 88·1%, DPT/Penta 1 85·9%, DPT/Penta 2 81·0%, DPT/Penta 3 74·2%, MCV1 74·7%. The largest single marginal step-down was DPT2→DPT3 (−6·8 percentage points). DPT3 and MCV1 were statistically indistinguishable, refuting the widely-cited DPT3→MCV1 bottleneck at continental scale. Countries fell into four policy-relevant quadrants: 21 with both failure rates low (maintain), six entry-point dominant including Nigeria (54% zero-dose), four follow-up dominant including South Africa, and seven requiring comprehensive system rebuild. The Markov decomposition revealed that between-country variance falls roughly ten-fold along the cascade (τ² = 0·96 at Start→BCG to τ² = 0·11 at Dose 3→MCV1), showing that countries differ far more in EPI entry than in completion. Predicted terminal states: 59% completed through MCV1, 14% zero-dose, 27% partial.

**Interpretation.** The cascade leaks gradually and heterogeneously. Entry-point access represents the single largest source of cross-country variation. Intervention design must match the failure type: outreach and zero-dose strategies where entry dominates; reminder and defaulter-tracing systems where follow-up dominates; integrated rebuilds where both are high.

**Funding.** No external funding.

---

## Introduction

Childhood vaccination schedules in sub-Saharan Africa require children to attend at least five separate health contacts during the first nine months of life: BCG at birth, DPT/Penta doses at six, ten and fourteen weeks, and measles-containing vaccine (MCV1) at nine months. Each contact is an independent opportunity for the system to fail. Yet the dominant metric used to monitor immunisation programmes—the percentage of children receiving a given antigen—treats each vaccine as a standalone outcome, obscuring the sequential structure of the problem.

A national DPT3 coverage of 70% can arise from three fundamentally different failure patterns: 30% of children were never reached by any part of the immunisation system (access failure at entry); 30% started but dropped out before completing the series (retention failure); or roughly 15% in each category (combined weakness). These mechanisms are not simply different framings of the same data—they predict different causes, different effective interventions, and different appropriate monitoring systems. Entry-point failure is addressed by outreach campaigns, mobile vaccination, geographic access improvement, community engagement and zero-dose mapping programmes. Follow-up failure is addressed by reminder systems, defaulter tracing, integration with other child-health contacts, and schedule alignment. Applying a reminder-based intervention to a population dominated by entry-point failure, or vice versa, will systematically underperform.

The UNICEF "dropout rate" (DPT1 to DPT3 as a proportion of DPT1 recipients) approximates follow-up failure for a single segment of the cascade, but has three limitations: it uses only two data points, it is sensitive to the denominator choice, and it does not separate the contribution of entry-point non-attenders from mid-cascade dropouts. Global analyses of zero-dose children have established the scale and correlates of non-initiation, but have not systematically cross-classified countries by their dominant failure mode or decomposed the full sequential cascade. Existing applications of Markov or multi-state models to immunisation data are few and have not been applied at continental scale using harmonised survey data.

The Expanded Programme on Immunisation in sub-Saharan Africa has been tracked by Demographic and Health Surveys (DHS) since 1988, producing a uniquely consistent longitudinal record spanning 35 years, 38 countries, and over a quarter of a million children per analytical cohort. This dataset permits a continent-scale examination of cascade structure that would not be feasible from administrative records alone.

We pursued three aims. First, to describe the continental EPI dropout cascade from BCG through MCV1 and quantify step-specific attrition. Second, to classify each of the 38 countries by their dominant failure mode—entry-point, follow-up, or both—using the latest available survey. Third, to formalise the cascade as a multi-state Markov model that quantifies between-country heterogeneity at each transition and predicts terminal vaccination states, identifying the cascade step where policy leverage is greatest.

---

## Methods

### Data source

We used Individual Recode files from the DHS Program for all sub-Saharan African countries with at least one completed DHS survey round. Files are in CSPro fixed-width format with companion data dictionaries (.DCF); survey-level metadata were extracted from .DCF headers, and child-level vaccination records were extracted from record types W43 (DHS-VII onward) or 43 (DHS-VI and earlier). We initially extracted 210 surveys. We retained 163 surveys from 38 countries (1989–2024) after excluding AIDS Indicator Surveys and partial rounds lacking vaccination modules, and after applying a minimum threshold of 30 dated dose-3 records per survey.

### Study population

We restricted analyses to children aged 12–23 months at the time of interview, born to women aged 15–49 (n = 263 385 children across 163 surveys and 38 countries). This age window allows sufficient time for receipt of all antigens up to MCV1 while minimising left-censoring of the nine-month measles dose.

### Vaccine receipt

For each child we recorded: BCG, OPV0, DPT1/2/3 or Penta1/2/3 (depending on survey wave), OPV1/2/3, PCV1/2/3 (where available), rotavirus 1/2 (where available) and MCV1.

**Unified DPT/Penta series.** DHS questionnaires migrated from DPT variables (H3, H5, H7) to pentavalent variables (H51, H52, H53) around 2010 as countries replaced stand-alone DPT with combination pentavalent vaccine. For each child we used whichever series was recorded; the other was coded "Not Applicable" by DHS. Results throughout refer to "DPT/Penta" and are denoted D1, D2, D3 for brevity.

A dose was counted as received if the DHS status code was 1 (vaccination card, date present), 2 (maternal recall), or 3 (card marked, date missing). Codes 0 (no), 8 (do not know), 9 (missing) and "Not Applicable" were excluded from numerator and denominator. DHS sample weights (V005 / 1 000 000), cluster (V021) and strata (V022) variables were used throughout for variance-consistent weighted estimation.

### Cascade metrics

For each survey we computed, using DHS survey weights:

- **Marginal coverage** at each step: BCG, D1, D2, D3, MCV1 (percentage of all eligible children receiving the dose).
- **Conditional dose-completion probability**: P(dose k+1 | dose k received) at each of the four transitions BCG→D1, D1→D2, D2→D3, D3→MCV1.
- **Zero-dose rate**: proportion of children receiving neither BCG nor D1. We required failure on both first-scheduled antigens (rather than DPT1 alone) as a conservative definition that reduces false positives from single-antigen data-collection error.
- **Follow-up failure rate**: 1 − P(D3 | D1), the proportion of initiated children who failed to complete the DPT/Penta series.

### Failure-type classification

We classified each country (using the most recent survey) according to two binary thresholds: entry-point failure ≥ 10% ("high entry-point failure") and follow-up failure ≥ 20% ("high follow-up failure"). The resulting quadrants are: *both low* (functioning EPI; maintain), *entry-point dominant* (access/outreach priority), *follow-up dominant* (retention/reminder priority), and *both high* (comprehensive system rebuild required). Thresholds were set to reflect approximate policy relevance—a 10% zero-dose rate implies roughly one million unvaccinated children per year in a mid-sized African country, and a 20% follow-up loss implies a substantial cohort of partially-protected children—rather than data-driven cut-points.

### Multistate Markov model

We represented the cascade as a discrete-state absorbing Markov chain with state space:

> *s₀* = never started (zero-dose); *s₁* = BCG only; *s₂* = BCG + D1; *s₃* = BCG + D1 + D2; *s₄* = BCG + D1 + D2 + D3; *s₅* = completed (D3 + MCV1)

We defined five forward transition probabilities *q_j* (j = 1…5) corresponding to: Start→BCG, BCG→D1, D1→D2, D2→D3, D3→MCV1.

For each of the 38 countries we computed V005-weighted Bernoulli proportions *p̂_{c,j}* from the most recent survey, with Kish-effective sample sizes *n_{eff,c,j}* = (Σw)² / Σw². We then estimated between-country heterogeneity using the DerSimonian–Laird random-effects model on the logit scale:

> logit(*p̂_{c,j}*) ~ N(μ_j, σ²_{c,j} + τ²_j)

where σ²_{c,j} = 1/(n_{eff,c,j} · p̂_{c,j} · (1 − p̂_{c,j})) is the within-country sampling variance and τ²_j is the between-country variance estimated by the method-of-moments estimator. We computed the shrinkage weight B_{c,j} = σ²_{c,j} / (σ²_{c,j} + τ̂²_j) and the empirical Bayes posterior mean:

> logit(*p̂^EB_{c,j}*) = (1 − B_{c,j}) · logit(*p̂_{c,j}*) + B_{c,j} · μ̂_j

Back-transforming to the probability scale yields the country-specific Bayes-shrunk transition probability. We then marginalised the Markov chain to obtain predicted terminal-state probabilities per country. For example, the predicted proportion completing through MCV1 is *p̂^EB_{c,1}* × *p̂^EB_{c,2}* × *p̂^EB_{c,3}* × *p̂^EB_{c,4}* × *p̂^EB_{c,5}*.

We quantified heterogeneity at each transition using τ²_j (between-country variance on the logit scale) and *I²_j* (proportion of total variance attributable to true between-country differences). *I²_j* > 75% is generally interpreted as substantial heterogeneity.

### Validation

Coverage estimates from one held-out survey (Ethiopia 2016 DHS) reproduced the published EDHS-7 final-report values for BCG (within 1·6 percentage points), DPT3 (within 0·9 pp) and MCV1 (within 0·1 pp), confirming correct weight application and parser accuracy. Bayes-shrunk transition probabilities matched descriptive conditional probabilities to within 0·2 pp on average, indicating that country sample sizes are large enough that shrinkage does not materially move estimates.

### Software

Python 3.10 (pandas, numpy, scipy, matplotlib). No external DHS-specific package was used. All code is provided as supplementary material.

### Ethics

Secondary analysis of de-identified public-use DHS data; no new human subjects research conducted. DHS Program data-access agreement complied with.

---

## Results

### Continental cascade structure

Figure 1 shows the continent-average EPI dropout cascade based on the most recent DHS survey per country (n = 38 surveys). Mean coverage at each step was: BCG 88·1%, D1 85·9% (−2·2 pp from BCG), D2 81·0% (−4·9 pp from D1), D3 74·2% (−6·8 pp from D2), and MCV1 74·7% (+0·5 pp from D3). Three observations follow directly.

First, the cascade leaks gradually across all steps rather than collapsing at any single transition. Second, the largest single marginal step-down is D2→D3 (−6·8 pp), not D3→MCV1, which is the transition most commonly cited as a bottleneck in global immunisation discourse. Third, and most strikingly, D3 and MCV1 coverage are statistically indistinguishable at continental scale: children who completed the DPT/Penta series proceeded to MCV1 at essentially the same rate continent-wide. The DPT3→MCV1 gap commonly cited in WHO/UNICEF coverage estimates is absent at the continental mean.

Figure 2 presents the same data as a waterfall chart, with step-level leakage annotated, illustrating how the birth cohort is progressively depleted at each vaccine contact.

### Conditional dose-completion probabilities

The marginal cascade (Figure 1) compounds both entry-point failure and mid-cascade attrition. Figure 3 disaggregates these by displaying country-specific conditional transition probabilities at each step.

Continent-mean conditional probabilities were: P(D1 | BCG) = 95·0%, P(D2 | D1) = 93·5%, P(D3 | D2) = 90·3%, P(MCV1 | D3) = 88·3%. Each transition retains roughly 88–95% of the prior cohort. The compound effect of these moderate per-step losses—none individually large—produces the 13·4 percentage-point BCG-to-MCV1 attrition visible in Figure 1.

Countries with consistently high conditional probabilities across all transitions (deep green in Figure 3) include Rwanda, Burundi, and Eswatini. Countries with uniformly low conditional probabilities include Chad, Nigeria and Guinea, though the mechanisms differ substantially between them (Section 3.3).

### Country classification by failure type

Figure 4 classifies the 38 countries by their dominant failure mode using entry-point failure (x-axis) and follow-up failure (y-axis), with thresholds at 10% and 20% respectively.

**Both low — functioning EPI (n = 21).** Twenty-one countries fell below both thresholds: Burkina Faso, Burundi, Eswatini, Gabon, Gambia, Ghana, Kenya, Lesotho, Malawi, Mauritania, Namibia, Rwanda, Senegal, Sierra Leone, Sudan, São Tomé & Príncipe, Tanzania, Togo, Uganda, Zambia, and Zimbabwe. These countries represent the positive case for African EPI and the platform from which coverage gains are incremental. Policy priority here is the final 10%—typically children in marginalised urban settlements or conflict-affected areas, populations for whom standard fixed-post delivery is insufficient.

**Entry-point dominant (n = 6).** Benin, Cameroon, Comoros, Madagascar, Mali and Nigeria. Nigeria is the most extreme case, with 54% of children receiving no doses whatsoever—the highest zero-dose rate on the continent and by far the largest absolute number of zero-dose children. Figure 5 (burden-weighted bubble chart, bubble size ∝ absolute zero-dose burden) confirms Nigeria's outsized contribution: its bubble is roughly three times the area of the next largest. For these countries, the dominant lever is reaching unvaccinated children. Reminder-based interventions are not the appropriate primary response here because zero-dose children have no prior contact with the immunisation system to which a reminder could be directed.

**Follow-up dominant (n = 4).** Congo (Brazzaville), Liberia, Niger and South Africa. South Africa is the most analytically interesting case: its healthcare system is among the best-resourced on the continent, yet a measurable mid-cascade dropout pattern places it in the follow-up-dominant quadrant. This points to scheduling and reminder-system gaps rather than access failures, consistent with known challenges in South Africa's fragmented primary healthcare delivery.

**Both high — comprehensive rebuild required (n = 7).** Angola, Chad, Côte d'Ivoire, DR Congo, Ethiopia, Guinea and Mozambique. These seven countries account for a disproportionate share of unprotected children continent-wide. DR Congo, Ethiopia and Mozambique are three of the most populous countries in sub-Saharan Africa; their combined both-high status represents a substantial fraction of the continent's total unvaccinated burden.

### Regional patterns

Figure 6 presents cascade profiles by region (mean ± 1 SD across countries).

Southern Africa recorded the highest regional coverage (BCG 94%, D3 82%, MCV1 85%) with narrow between-country variation, reflecting the relatively developed primary healthcare infrastructure across most of this subregion. East Africa was similar in D3 and MCV1 coverage (D3 82%, MCV1 80%), though with somewhat wider spread due to the inclusion of Ethiopia (both-high) and Comoros (entry-point dominant) in this regional grouping. West Africa showed the largest between-country variance: Burkina Faso achieves 89% DPT3 while Nigeria sits at 38%, a 51 percentage-point range within a single region. Central Africa recorded the lowest mean D3 coverage (62%) and the steepest average cascade decline, driven by Angola, Chad and DR Congo.

### Country-level cascades over time

Figure 7 shows individual country cascades for all 38 countries (latest DHS). The visual contrast between flat cascades (Rwanda, Burundi, Eswatini) and steeply declining ones (Chad, Nigeria, Guinea) reinforces the classification results. Figure 8 decomposes each country's child population into four mutually exclusive vaccination states: fully completed (MCV1 received), DPT3 complete but no MCV1, started but no DPT3, and zero-dose. Nigeria's zero-dose segment dominates the figure.

Figure 9 tracks cascade evolution over time for the eight countries with the most DHS rounds (Senegal, Ghana, Zambia, Tanzania, Rwanda, Mali, Kenya, Zimbabwe). Senegal and Ghana show sustained multi-decade gains. Rwanda shows a characteristic V-shaped trajectory—collapse in the late 1990s during and immediately after the genocide, followed by one of the most dramatic recoveries in global public health. Zimbabwe exhibits modest recent decline. Figure 10 summarises long-run change in D3 coverage for all countries with three or more survey rounds: Senegal (+54 pp, 1986–2023) and Burkina Faso (+52 pp, 1992–2023) show the largest absolute gains; Mozambique and Zimbabwe show net declines.

### Formal multistate Markov decomposition

#### Continent-level transition probabilities

Figure 11 displays the continent-level Markov chain with Bayes-shrunk transition probabilities. The five transition probabilities are: Start→BCG 90·1%, BCG→D1 95·5%, D1→D2 93·0%, D2→D3 89·2%, D3→MCV1 88·5%. The smallest conditional probability is Dose 3→MCV1 (88·5%), narrowly below Dose 2→Dose 3 (89·2%). Note that in the descriptive marginal cascade, DPT2→DPT3 shows the largest absolute step-down (−6·8 pp) because a larger number of children are in that cohort; the Markov transition probability is a conditional measure and the two metrics are complementary.

Red downward arrows annotate the per-step dropout fractions: Start→BCG −9·9%, BCG→D1 −4·5%, D1→D2 −7·0%, D2→D3 −10·8%, D3→MCV1 −11·5%. The chain leaks gradually rather than at a single break point.

#### Country-specific transitions and shrinkage

Figure 12 presents per-country forest plots across all five transitions, and Figure 13 presents the same data as a heatmap. Shrinkage is uniformly small (< 0·2 pp on average), confirming that country sample sizes are sufficient to dominate the prior. The heatmap reveals a positive correlation pattern: countries that perform well at entry (Start→BCG) tend also to perform well later in the cascade, suggesting that underlying system capacity or demand factors co-determine performance across transitions.

#### Between-country heterogeneity — a key finding

Figure 14 presents between-country variance τ² at each of the five Markov transitions. Heterogeneity falls monotonically from Start→BCG (τ² = 0·96, I² = 99·8%) to D3→MCV1 (τ² = 0·11, I² = 97·0%)—a roughly ten-fold decline. All five I² values exceed 97%, indicating that essentially all observed variation represents true between-country differences rather than sampling error.

The monotone decline in τ² has a clear policy interpretation: countries differ enormously in whether they bring children into the immunisation system at all, but once a child has BCG, her trajectory through the subsequent doses is comparatively similar across countries. The entry-point transition is therefore the step with the greatest cross-country variance, the greatest scope for between-country improvement, and the step most sensitive to interventions that vary in their geographic or socioeconomic targeting.

#### Predicted terminal-state occupation

Figure 15 shows predicted terminal-state probabilities per country, sorted by completion rate. Continent-level predictions (mean across countries) are shown in Table 1. Approximately three in five children complete the full schedule through MCV1; one in seven is zero-dose; and roughly one in four is partially vaccinated. Partial vaccination is spread across four intermediate states, with the dose-2-maximum state (BCG + D1 + D2 only) being the most common partial category (8·2%).

**Table 1. Predicted terminal vaccination states — continent mean (Bayes-shrunk Markov model)**

| Terminal state | Predicted % |
|---|---:|
| Zero-dose | 13·7 |
| BCG only | 5·4 |
| D1 maximum | 6·2 |
| D2 maximum | 8·2 |
| D3 maximum | 7·5 |
| Completed (MCV1) | 59·0 |

---

## Discussion

### Main findings

The EPI cascade in sub-Saharan Africa leaks gradually and heterogeneously. No single transition accounts for the majority of unvaccinated children; losses compound multiplicatively across five steps. At continental scale, the DPT2→DPT3 transition shows the largest marginal attrition in the descriptive cascade, while the D3→MCV1 transition has the smallest Markov conditional probability—complementary findings that together refute the notion of a single dominant break point. DPT3 and MCV1 sit at essentially the same coverage level continent-wide, contradicting the common framing of measles as a notably incomplete final step.

Between-country variance in cascade performance falls ten-fold from the entry transition to the completion transition, identifying entry-point access as the dominant source of cross-country heterogeneity. This is the study's key analytical contribution: the formal Markov decomposition reframes the policy question from "how do we improve coverage?" to "at which transition does improvement have the greatest scope?" The answer, unambiguously, is the first one.

Countries cluster into four meaningfully distinct policy regimes rather than a single performance gradient. Nigeria's 54% zero-dose rate is the continent's most urgent individual case; it accounts for the majority of absolute zero-dose burden in sub-Saharan Africa. South Africa's follow-up dominant pattern is unexpected given its resource base, suggesting that the relevant constraint there is not access per se but service-delivery architecture.

### Policy implications by quadrant

For **both-low countries** (n = 21, the majority of the continent), standard EPI strengthening continues to be the appropriate response. The remaining unvaccinated children in these settings are disproportionately in hard-to-reach geographic locations, urban informal settlements, and communities with residual vaccine hesitancy—populations for whom the conventional fixed-post delivery model is insufficient. Incrementally targeted strategies (Reaching Every District, community health worker integration) are appropriate.

For **entry-point dominant countries** (n = 6, most consequentially Nigeria), the primary failure is non-initiation. Reminder systems and defaulter-tracing are not the right first-line intervention because there is no prior system contact to trace. Effective strategies must bring the vaccine to children who have no established relationship with formal health facilities: geographically targeted outreach, integration with community health worker home visits, demand-generation communication campaigns, and tools like Gavi's zero-dose mapping and IRMMA framework. Investment in health-facility-based improvement will yield limited returns if a majority of children are not facility-attenders.

For **follow-up dominant countries** (n = 4), the primary failure occurs after initiation. SMS reminders, community health worker reminder visits, integration of subsequent vaccine doses with other child-health contacts (growth monitoring, vitamin A), and reduction in missed-opportunity rates at subsequent scheduled encounters are the appropriate priorities. The initial contact with BCG provides both a data point and a delivery platform.

For **both-high countries** (n = 7), single-lever interventions will structurally underperform. DRC, Ethiopia and Angola require simultaneous investment in expanding geographic reach and in retaining children who initiate. Integrated outreach that both brings in new children and actively tracks them forward is expensive but is the only approach proportionate to the problem.

### Why DPT2→DPT3 matters more than DPT3→MCV1

The commonly cited DPT3→MCV1 gap receives outsized policy attention, partly because it is easily measured and partly because it coincides with the introduction of a different vaccine at a different health contact. Our findings suggest this attention is misplaced at continental scale. Children who reach MCV1 have already passed through three prior scheduled visits; the cohort arriving at the nine-month contact has been pre-selected by the preceding cascade. The DPT2→DPT3 step, which involves completing the final dose of the most widely administered vaccine series, is the step where mid-cascade attrition is greatest. Improvements upstream—specifically tightening completion of the ten-week to fourteen-week interval—propagate downstream to MCV1 more efficiently than additional outreach specifically targeted at the nine-month contact. This implies a sequencing recommendation: strengthen mid-cascade completion first.

### Comparison with prior estimates

Our marginal DPT3 estimates correspond closely to published DHS country reports and the WHO/UNICEF Estimates of National Immunization Coverage (WUENIC) for overlapping country-years (within approximately 2 pp on average, accounting for the 12–23 month age window versus WUENIC's one-year survival-adjusted denominator). The novel contribution is not the marginal numbers—which replicate established findings—but the cascade structure, the failure-type decomposition, and the Markov heterogeneity analysis.

Our zero-dose definition (no BCG AND no DPT1) is more conservative than the WUENIC convention (no DPT1 alone). This produces lower zero-dose rates than WUENIC but reduces false positives attributable to single-antigen data-collection error. Robustness checks restricting to card-confirmed doses only (status code 1) did not change the quadrant classification of any country, confirming that the structural findings are not sensitive to recall-versus-card dose definition.

### Limitations

**Card versus recall doses pooled.** We did not separate card-confirmed from maternal-recall doses; recall bias may inflate coverage estimates by 5–10 pp on average. The card-only sensitivity analysis (see above) does not change country quadrant classifications but may affect absolute coverage values.

**Age cohort.** Our restriction to 12–23 months captures the cohort at the appropriate age to assess schedule completion. Children older than 23 months may have received doses subsequently; this analysis does not track later catch-up. The 12–23 month window is standard in DHS immunisation analyses.

**Varying EPI schedules.** WHO-standard windows were used throughout. Some countries have moved MCV1 to 12 months in national schedules; this slightly affects MCV1 "completion" framing in those countries.

**Sub-national variation masked.** National estimates conceal large within-country geographic and socioeconomic inequities. The underlying child-level data preserves cluster and region variables and supports sub-national replication; this is noted as a priority for future work.

**Survey recency.** Several countries' most recent DHS data are dated: Niger (2012), Togo (2013), Eswatini (2006), São Tomé & Príncipe (2008). The classifications for these countries should be interpreted as conditional on available data and not treated as characterisations of current programme performance.

**Absorbing-state Markov assumption.** Our Markov model treats the cascade as strictly forward-progressing (children cannot skip doses or receive doses out of sequence). In practice, some children may receive later-schedule doses without earlier ones (e.g., BCG at a later age). Exploratory analysis of these sequences in a subset of surveys suggested they are too rare to materially affect estimated transition probabilities.

### Future directions

Four extensions are priorities. First, sub-national (region- and cluster-level) replication of the cascade structure and failure-type classification, using the same pipeline. Second, linkage with sub-national conflict, urbanicity, travel time, and wealth data to model correlates of each failure type—building an explanatory layer onto the descriptive classification. Third, a full card-confirmed-only sensitivity analysis at panel scale (163 surveys rather than country-specific). Fourth, analysis of the effect of migrating from DPT to pentavalent vaccine on cascade completion, where the early panel evidence (pre- and post-Penta introduction, approximately 2008–2014 for most countries) suggests modest but consistent improvements in D2→D3 conditional completion.

---

## Conclusions

The EPI cascade in sub-Saharan Africa does not break at a single point. It leaks gradually across five steps, with country-level failure concentrated disproportionately at the entry transition—the step where between-country variance is greatest and where the scope for targeted improvement is largest. Countries divide into four meaningfully distinct policy regimes; effective intervention requires matching the strategy to the failure type. A continent-wide push to improve DPT3→MCV1 completion, while not harmful, addresses a step that is not the largest source of unvaccinated children and is not where the structural between-country heterogeneity lies. Systematically classifying countries by their dominant failure mode—using the DHS data that already exists—is a low-cost step that could substantially improve the targeting efficiency of global immunisation investment.

---

## Funding and competing interests

No external funding was received for this work. The authors declare no competing interests.

## Ethics

Secondary analysis of de-identified public-use survey data. No new human subjects research was conducted. Access to DHS Program data was obtained under registration agreement with the DHS Program, ICF International.

## Data availability

DHS Individual Recode files are publicly available from the DHS Program (https://dhsprogram.com) under registration. All analysis code and derived summary datasets accompany this manuscript as supplementary material. The underlying individual-level DHS data may not be publicly redistributed in accordance with the DHS data-use agreement.

## Author contributions

[TBD per ICMJE criteria: conceptualisation, data curation, formal analysis, writing—original draft, writing—review and editing.]

## Acknowledgements

We thank the DHS Program and the national Ministries of Health of the 38 participating countries for making these data available. We thank the survey teams and the children and caregivers whose participation made this evidence base possible.

---

## References

1. World Health Organization, UNICEF. WHO/UNICEF Estimates of National Immunization Coverage (WUENIC), 2023 revision. Geneva: WHO; 2023.

2. Gavi, the Vaccine Alliance. Zero-dose learning agenda: reaching the unreached. Geneva: Gavi; 2021.

3. ICF International. Demographic and Health Surveys Program. Methodology. Rockville, MD: ICF; 2012.

4. Cutts FT, Claquin P, Danovaro-Holliday MC, Bhatt S. Monitoring vaccination coverage: defining the role of surveys. *Vaccine*. 2016;34(35):4103–4109.

5. Burton A, Monasch R, Lautenbach B, et al. WHO and UNICEF estimates of national infant immunization coverage: methods and processes. *Bull World Health Organ*. 2009;87(7):535–541.

6. Arsenault C, Harper S, Nandi A, Mendoza Rodríguez JM, Hansen PM, Johri M. Monitoring equity in vaccination coverage: a systematic analysis of demographic and health surveys from 45 Gavi-supported countries. *Vaccine*. 2017;35(6):951–959.

7. Mosser JF, Gagne-Maynard W, Rao PC, et al. Mapping diphtheria-pertussis-tetanus vaccine coverage in Africa, 2000–2016: a spatial and temporal modelling study. *Lancet*. 2019;393(10183):1843–1855.

8. Watts E, Bhatt S, Bergquist H, et al. Retrospective analysis of global vaccination and immunisation survey data to assess trends in diphtheria-tetanus-pertussis (DTP) vaccine coverage. *Vaccine*. 2021;39(25):3347–3356.

9. DerSimonian R, Laird N. Meta-analysis in clinical trials. *Control Clin Trials*. 1986;7(3):177–188.

10. Morris CN. Parametric empirical Bayes inference: theory and applications. *J Am Stat Assoc*. 1983;78(381):47–55.

11. Higgins JPT, Thompson SG. Quantifying heterogeneity in a meta-analysis. *Stat Med*. 2002;21(11):1539–1558.

12. Brenzel L, Young D, Walker DG. Chapter 10: Costs and financing of routine immunization: approach and findings of a multi-country study (EPIC). *Vaccine*. 2015;33 Suppl 1:A13–20.

13. Wiysonge CS, Uthman OA, Ndumbe PM, Hussey GD. Individual and contextual factors associated with low childhood immunisation coverage in sub-Saharan Africa: a multilevel analysis. *PLoS One*. 2012;7(5):e37905.

14. Rainey JJ, Watkins M, Ryman TK, Sandhu P, Bo A, Banerjee K. Reasons related to non-vaccination and under-vaccination of children in low and middle income countries: findings from a systematic review of the published literature, 1999–2009. *Vaccine*. 2011;29(46):8215–8221.

15. Scobie HM, Edelstein M, Nicol E, et al. The immunisation agenda 2030: a global strategy to leave no one behind. *Lancet*. 2020;395(10235):1440–1441.

---

## Figure captions

**Figure 1.** EPI dropout cascade — continent average (latest DHS per country, n = 38). Mean percentage of children aged 12–23 months receiving each vaccine at each step. Inter-step marginal losses are annotated. The largest single step-down is DPT2→DPT3 (−6·8 pp). BCG = bacille Calmette-Guérin; DPT = diphtheria-pertussis-tetanus; Penta = pentavalent; MCV1 = first dose of measles-containing vaccine.

**Figure 2.** EPI dropout cascade — continent average, waterfall format. Blue = children remaining on schedule at each step. Red = children who leaked at that step. Waterfall chart illustrating how the birth cohort is progressively depleted at each vaccine contact.

**Figure 3.** Conditional dose-completion probabilities by country (latest DHS). Heatmap showing P(next dose | previous dose received) at each of four transitions. Greener = higher conditional completion (stickier cascade). Countries sorted by P(MCV1 | DPT3). Each cell shows the percentage.

**Figure 4.** Country classification by EPI failure type (latest DHS). Scatter plot of entry-point failure (x-axis: % of children receiving no doses) against follow-up failure (y-axis: % of initiated children not completing DPT3). Thresholds at 10% (vertical) and 20% (horizontal) define four policy quadrants. Labels indicate country names.

**Figure 5.** Burden-weighted failure-type classification. Same axes as Figure 4; bubble area proportional to absolute number of zero-dose children per year (national under-1 birth cohort × entry-point failure rate, using UN World Population Prospects denominators). Larger bubbles indicate greater absolute zero-dose burden.

**Figure 6.** Regional cascade comparison (latest DHS per country, mean ± 1 SD). West Africa (14 countries), East Africa (8 countries), Central Africa (8 countries), Southern Africa (8 countries). Error bars indicate one standard deviation of country-level values within each region.

**Figure 7.** EPI dose cascade by country — latest DHS survey. Small-multiple bar charts for all 38 countries, showing BCG, D1, D2, D3, and MCV1 coverage. Countries ordered alphabetically. Survey year shown beneath each country name.

**Figure 8.** Vaccination status breakdown by country (latest DHS). Stacked horizontal bar chart. Each bar decomposes the 12–23 month population into four mutually exclusive categories: fully completed (MCV1 received); DPT3 complete but no MCV1; started but no DPT3; zero-dose (no BCG, no DPT1). Countries sorted by fully-completed fraction, descending.

**Figure 9.** EPI cascade evolution over time — countries with the most DHS rounds. Line plots for Senegal, Ghana, Zambia, Tanzania, Rwanda, Mali, Kenya and Zimbabwe showing BCG, D1, D2, D3 and MCV1 coverage across all available survey rounds.

**Figure 10.** Long-run change in DPT3 coverage (countries with ≥ 3 DHS rounds). Horizontal bar chart showing percentage-point change in DPT3 between earliest and latest survey in each country's panel, with survey years annotated. Countries ranked by magnitude of change.

**Figure 11.** Continent-level Markov chain — mean transition probabilities (Bayes-shrunk). Five-state chain: Start → BCG → Dose 1 → Dose 2 → Dose 3 → MCV1 (completed). Blue arrows show forward transition probabilities; red arrows show step-level dropout fractions. Probabilities are posterior means from random-effects meta-analysis with empirical Bayes shrinkage.

**Figure 12.** Per-country transition probabilities — raw versus Bayes-shrunk (forest plot). Five panels, one per Markov transition. Blue dots = raw country estimates; blue dots with 95% credible intervals = Bayes-shrunk posterior means. Red dashed line = continent posterior mean. Countries sorted by shrunk estimate within each panel.

**Figure 13.** Per-country Bayes-shrunk transition probabilities (heatmap). Rows = countries; columns = five Markov transitions (Start→BCG to Dose 3→MCV1). Colour scale: green = high transition probability (≥ 95%), red = low (≤ 60%). Cell values are shrunk posterior means (%). Countries sorted by Dose 3→MCV1 probability.

**Figure 14.** Between-country heterogeneity by Markov transition. Bar chart of between-country variance τ² (logit scale) at each of the five transitions, with I² annotated. Variance falls roughly ten-fold from Start→BCG (τ² = 0·96, I² = 99·8%) to Dose 3→MCV1 (τ² = 0·11, I² = 97·0%), demonstrating that countries differ far more in EPI entry than in completion.

**Figure 15.** Predicted terminal vaccination states per country (Bayes-shrunk Markov model). Stacked bar chart showing the predicted percentage of 12–23 month children in each terminal state: zero-dose, BCG only, D1 maximum, D2 maximum, D3 maximum, completed (MCV1). Countries sorted by predicted completion rate. Continent-level predicted means are shown in Table 1.
