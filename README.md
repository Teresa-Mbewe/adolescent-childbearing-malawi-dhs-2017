# Project 01: Socioeconomic Inequalities in Adolescent Childbearing in Malawi

**Analysis of the 2017 Malawi Demographic and Health Survey (DHS)**

## Project overview

This project examines whether adolescent childbearing differs across
household wealth groups in Malawi. It uses the 2017 Malawi DHS IPUMS
extract and focuses on girls aged 15--19 years.

The analysis is descriptive. It estimates the weighted prevalence of
having ever given birth to at least one child across the five household
wealth quintiles.

## Research question

Does adolescent childbearing differ across household wealth groups in
Malawi?

## Data

-   **Source:** 2017 Malawi Demographic and Health Survey, accessed
    through IPUMS DHS.
-   **Study population:** Girls aged 15--19 years.
-   **Analytical sample:** 828 girls.
-   **Outcome:** Adolescent childbearing, defined as having ever given
    birth to at least one child.
-   **Explanatory variable:** Household wealth quintile (`WEALTHQ`):
    poorest, poorer, middle, richer and richest.

The outcome measures previous live birth, not pregnancy. Pregnancies
that did not result in a live birth are not captured by this measure.

-   ## Data and Methods

Data were analysed in R using the `survey` package. The complex survey design was specified using:

- `PERWEIGHT`: person sampling weight
- `PSU`: primary sampling unit
- `STRATA`: sampling stratum

The IPUMS DHS documentation was checked, and `PERWEIGHT` was used as supplied, without additional scaling. Weighted prevalence estimates and 95% confidence intervals were calculated for each wealth quintile.

The IPUMS DHS documentation was checked and `PERWEIGHT` was used as
supplied, without additional scaling. Weighted prevalence estimates and
95% confidence intervals were calculated for each wealth quintile.

## Key finding
  ------------------------------------
  | Household Wealth Quintile | Weighted Prevalence (%) | 95% Confidence Interval |
| :--- | :--- | :--- |
| Poorest | 37.25% | 27.71 – 46.79 |
| Poorer | 30.05% | 20.44 – 39.65 |
| Middle | 24.84% | 15.45 – 34.23 |
| Richer | 27.74% | 19.20 – 36.27 |
| Richest | 14.76% | 9.56 – 19.97 |

The highest weighted prevalence was observed in the poorest quintile
(37.25%) and the lowest in the richest quintile (14.76%), an absolute
difference of 22.49 percentage points. The pattern generally declined
with increasing wealth, but was not strictly linear because prevalence
in the richer quintile was slightly higher than in the middle quintile.

These are descriptive estimates. They do not establish that household
wealth causes adolescent childbearing, and no formal statistical test
comparing the quintiles was conducted.

## Figure

![Weighted prevalence of adolescent childbearing by household wealth
quintile](figure1_adolescent_childbearing_by_wealth.png)

*Figure 1. Weighted prevalence of adolescent childbearing among girls
aged 15--19 years by household wealth quintile, Malawi DHS 2017. Error
bars represent 95% confidence intervals.*

## Limitations

-   The cross-sectional, descriptive analysis cannot establish
    causality.
-   The data were collected in 2017 and may not reflect current
    patterns.
-   The outcome captures whether a girl had ever given birth to at least
    one child; it does not capture pregnancies that did not result in a
    live birth.
-   No formal statistical tests comparing prevalence across wealth
    quintiles were conducted.

## Repository contents

-   `Project_01_Adolescent_Childbearing_Report.pdf` --- completed
    project report.
-   `README.md` --- project overview, methods and key findings.
-   `figures/figure1_adolescent_childbearing_by_wealth.png` --- report
    figure.
    
## Tools and Skills Demonstrated
- **R and the survey package:** Used for complex survey-weighted analysis.
- **Survey-weighted descriptive analysis:** Accounted for PSUs, strata, and sampling weights.
- **Data management:** Cleaned and operationalised variables 
- **Estimation:** Calculated weighted prevalence and 95% confidence intervals.
- **Data visualisation:** Created publication-quality bar charts using ggplot2.
- **Public health research writing:** Documented methods, results, and limitations in a formal research report.

## Data access and citation

The DHS microdata are subject to the DHS Program's access and use
conditions. Do not upload restricted microdata to this repository.
Readers should obtain the data through the appropriate DHS/IPUMS access
process.

**References**

National Statistical Office (NSO) \[Malawi\] and ICF. (2017). *Malawi
Demographic and Health Survey 2017*. Zomba, Malawi, and Rockville,
Maryland, USA: NSO and ICF.

Minnesota Population Center. (2020). *Integrated Public Use Microdata
Series, International: Version 7.3* \[Dataset\]. IPUMS DHS.
https://doi.org/10.18128/D020.V7.3

---

# Project 01B: Extended Analysis (Survey-Weighted Logistic Regression)

This extended analysis builds on the descriptive findings of Project 01 by using survey-weighted logistic regression to examine the association between household wealth, age, educational attainment, and adolescent childbearing.

## Methods
- **Sample:** 828 adolescent girls (aged 15–19) from the 2017 Malawi DHS.
- **Design:** Complex survey design was specified using `PSU`, `STRATA`, and `PERWEIGHT`.
- **Models:** Three sequential models were fitted:
  - Model 1: Wealth only.
  - Model 2: Wealth + Age.
  - Model 3: Wealth + Age + Education.

## Key Findings (Model 3)
After adjusting for age and education, adolescents in the richest wealth quintile had lower odds of having ever given birth compared with those in the poorest quintile (AOR = 0.900, 95% CI: 0.191–0.900). However, this estimate is sparse, and the upper confidence limit equals the point estimate due to limited outcome events in this group.

Age was positively associated with childbearing (AOR = 3.046, 95% CI: 2.434–3.814). Secondary education was associated with lower odds of childbearing compared with no education (AOR = 0.163, 95% CI: 0.049–0.540).

## Limitations
This is an observational, cross-sectional analysis. Associations do not imply causation. The wealth estimates are limited by sparse data in the highest wealth quintile.

## Reproducibility
The full R script for this analysis is available in the `DHS_Analysis_Teresa.R` file in this repository.
