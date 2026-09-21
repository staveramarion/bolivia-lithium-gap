# Bolivia's Lithium Gap: Reserves vs. Reality
### A Comparative Analysis with Chile and Argentina (2017-2023)

## Overview
Bolivia holds what is identified as the world's largest lithium resource base by the U.S. Geological Survey. An estimated 23 million metric tons. Yet despite this advantage, Bolivia converts almost none of it into actual exports, falling far behind its neighbors Chile and Argentina. Both of them have built substantial commercial lithium industries from comparatively smaller reserves. Chile has built the region's largest lithium export economy while Argentina even by starting from smaller reserves has attracted major international investment like Gangfeng, Livent, POSCO, Eramet, Rio Tinto and others. 

This project aims to investigate the gap directly: **why has Bolivia been unable to convert its lithium resource base advantage into meaningful export performance, and what would closing that gap look like for their economy?**

## Research Question
*Given Bolivia's substantial lithium resource base, why has it converted so little of that into actual exports compared to Chile and Argentina, and what would meaningful export growth mean for Bolivia's economy?*

## Data & Methods
- **Trade data**: UN Comtrade export data (HS codes 283691: lithium carbonates, and 282520: lithium oxide/hydroxide), accessed through World Bank WITS, 2017-2023.
- **Reserve figures**: USGS Mineral Commodity Summaries
- **Tools**: SQLite (SQL queries for aggregation, year-over-year change, price-per-unit, and market share calculations) and Chart.js (interactive dashboard visualization).
- **Qualitative sourcing**: Industry and policy reporting on Bolivia's lithium sector (YLB operations, extractions chemistry, political and regulatory structure)

## Data Limitations
- Argentina's Comtrade export data was only available for the years 2020 and 2023 within the HS codes used, the trend analysis for Argentina should be interpreted with this gap in mind.
- Bolivia's data was not available for the years 2019 and 2020.
- Neither Argentina or Bolivia have lithium hydroxide (282520) reported exports. Only Chile's data covers both of these products.
- USGS does not list Bolivia among the countries with official lithium reserves as in economically extractable under current tech/prices only as resources. This is central to the anlysis.

## Findings
Despite holding the world's largest lithium resource base of 23 million metric tons, Bolivia converts almost none of it into *formal* exports. Between the years 2017 and 2023, Bolivia's lithium carbonate export value ranged from the low $491,791 in (2017) to a high peal of $37.8 million in (2022). Yet this peak still represents only 5.6% of Chile's worst year in the same dataset used ($674 million in 2020). Chile confined 91.8% and 100% of the combined export value of the three countries in every year that was examined. 

This is not only to point at Chile's dominance but what surprisingly Argentina has in place, despite starting from a smaller estimated reserve base than Bolivia, they have attracted a lot of private investment across six active operations, which makes them the fifth-largest lithium producer of the world reaching 130,800 tons of production in the year of 2025, found outside my dataset. This implies that the underperformance of Bolivia is not simply a function of starting reserve size but instead the path that each of these countries has taken to develop that resource. 

Now, Bolivia's gap does not appear to be a pricing problem, actually their price per kilogram of lithium carbonate exceeded Chile's in most of the years studied. For example, at the 2022 peak Bolivia was a t $60.06/kg and Chile's at $41.58/kg, meaning that Bolivia's constraint is within the production and export capacity not the market demand or negotiating position.
This capacity gap is due to a few compunding factors:
- **Geology and chemistry**: Bolivia's lithium sits in magnesium rich brine under the Uyuni salt flats, which is a chemistry that is far more costly to purify than in Chile's Atacama brine.
-  **Climate**: Bolivia's five-month rainy season disrupt the extraction in ways that both Chile and Argentina's operations are not exposed to.
-  **Political and Institutional structure**: Bolivia's legal framework has historically reserved the lithium exploration and industrialization exclusively for the state through YLB (Yacimientos de Litio Bolivianos), this restricts the foreign direct investment and technology transfer that has enabled Chile and Argentina's private sector drive scale-up. As of 2024, YLB's first industrialized facility produced only 2,000-3,500 metric tons annually against a stated 15,000-ton capacity.
With the two partnerships of a $970 million from Russia's Uranium One and $1.03 billion with China's CBC, a target combined would reach ~90,000 metric tons of additional annual capacity. As stated in the Projected Impact section below, this capacity could represent a huge increase in Bolivia's export value but as of late 2025 neither contract has reached production. Highlighting that Bolivia's gap is currently political and institutional alongside geological.  

## Projected Impact of Announced Partnerships
Two major contracts were done, a $970 million agreement with Russia's Uranium One and $1.03 billion with China's CBC a CATL subsidiary. Combined, around 90,000 metric tons of annual lithium carbonate capacity for Bolivia. By applyong this target capacity against different price-per-ton scenarios it illustrates the scale of a potential export value, by uing Bolivia's own historical pricing (which was calculated from this project's trade data) alongside a current depressed market price to compare it:

| Price Scenario | Price per Ton | Projected Annual Export Value | vs. Bolivia's 2023 Actual ($14.6 million) |
|---|---|---|---|
| Current depressed spot price (~$10,000/ton) | $10,000 | **$900 million** | ~62x increase |
| Bolivia's own 2023 average price | $45,750 | **$4.12 billion** | ~281x increase |
| Bolivia's own 2022 peak price | $60,060 | **$5.4 billion** | ~369x increase |
**Important note:** As of late 2025, the Uranium One and the CBC partnership have not reached a commercial production, both are under parliament review. That means that this projection is a *potential* capacity if these contracts are realized, it is not a forecast of near future outcomes. Lithium prices have also proven to be very volatile in the period studied (see in the Price per kilogram chart) so the actual value could fall anywhere within, above or below this range.

## Further Considerations ##
**A note on Direct Lithium Extraction (DLE):**
- DLE, is a set of technologies that pull lithium straight from brine without evaporation ponds, it is often proposed as a solution to both Bolivia's chemistry problem (high brine impurity) and the water usage concerns that have been raised by local communities near the proposed lithium sites. By practicing DLE they can recycle up to 90% of process water and reduces land usage by 95% compared to the evaporation ponds. Unlike evaporation, its yield is not disrupted by the 5-month range of rain in Bolivia. But Bolivia's experience with DLE has been miscellaneous, because after investing $800 million in extraction methods over prior two years to 2025 the government has acknowledged that there were relatively poor results. So, DLE is a promising path forward but is not a guaranteed one given Bolivia's execution track until today.  

## Analytical Approach ##
1. **Aggregation by country and year** --> combining lithium carbonate (283691) and lithium hydroxide (282520) export values into a single total per country per year using the 'SUM()' and 'GROUP BY()'. This produced the primary comparison metric that was used throughout the analysis.
2. **Year-over-year change** --> used the function 'LAG()' and 'PARTITIONED BY()' country and product code, in order to calculate the dollar change in export value from each year to the next. This showed the sharp lithium price peak in 2022 and the 2023 decline seen in both Chile and Bolivia's data.
3. **Price per kilogram** --> divided trade value by the reported quantity (converted by kilograms), in order to isolate price trends from volume trends. This calculation enabled insights on Bolivia's price per-kilogram upper hand, which consistently exceeded Chile's even as Bolivia has a much more smaller export volume. This redirected the project's central question away from the pricing power and more toward the production capacity.
4. **Market share by year** --> used a correlated subquery to calculate each country's percentage share of the combined three countries export value per year, this showed the clearest single visualization of the dominance of Chile with 91.8%-100% market share in every year that was studied.
5. **Chile's Lithium Hydroxide price per kilogram** --> unlike the carbonate lithium comparison with the three countries, this only includes Chile since Bolivia and Argentina reported no lithium hydroxide (282520) exports in the dataset. It was worth including because: it strengthens the value-chain argument in the findings section; Chile is not only exporting exponentially more lithium than Bolivia and Argentina but also the only one exporting the more heavily processed hydroxide product. Lithium hydroxide requires a more advanced processing than carbonate (battery grade material), so it's complete absence from Bolivia and Argentina's export data suggests another gap beyond volume; a gap in processing capability not just extraction capacity. This table also shows how both carbonate and hydroxide prices moved together across the study period, both bottomed around 2020-2021 and spiked in 2022 (hydroxide: $38.47/kg, carbonate: $41.58/kg) and also declined in 2023. Confirming that Chile's overall swings in export value are driven by the same global lithium price cycle regardless of the product, supporting the year-over-year finding.

## Conclusion ##

This analysis was made to answer the following question: given Bolivia's substantial lithium resource base, why has it converted so little of it into actual exports, and what would meaningful export growth mean economically? The data collected points towards an answer, the gap is not explained by geology, market demand or the pricing power. Bolivia's lithium price has been consistently higher price per kilogram than Chile's throughout the whole study, this reduces the demand side explanation. Actually, the constraint is on the production and export capacity, because of a set of factors: Bolivia's more complex brine chemistry, several months of rainy season that disrupts the extraction and the biggest one is the state monopoly regulatory structure that limits foreign investment and technology transfer. Which by evidence have enabled a smaller resource base like Argentina to become the fifth largest lithium producer.
The scale of this opportunity is very big. By applying the historical pricing to the 90,000 metric tons of capacity that has been targeted by the announced partnerships with Uranium One and CBC it would suggest a potential export value that is tens to hundreds of times larger than Bolivia's 2023 actual number. But undergoing this opportunity depends less on continuing geological discovery and more on execution of resolving the regulatory and investment constrained capacity to date, and as both partnerships remain in parliamentary review as of late 2025, which would alleviate the capacity and commercial production. DLE offers promising results for Bolivia's chemistry and climate problems, but since they have had mixed results with that investment it recommends looking besides technological solutions, but instead at its core, an institutional and execution challenge. 

## References ##
### Trade & Reserve Data
- UN Comtrade Database, accessed via World Bank World Integrated Trade Solution (WITS). https://wits.worldbank.org
- U.S. Geological Survey, *Mineral Commodity Summaries* (Lithium), 2024–2025 editions. https://www.usgs.gov/centers/national-minerals-information-center/lithium-statistics-and-information

### Bolivia's Lithium Sector
- OilPrice.com. "Bolivia's Lithium Ambitions Face Economic and Environmental Headwinds." January 24, 2025. https://oilprice.com/Metals/Commodities/Bolivias-Lithium-Ambitions-Face-Economic-and-Environmental-Headwinds.html
- Americas Market Intelligence. "Bolivia at a Crossroads: Lithium, Gas, and the Search for Economic Stability After the 2025 Election." August 28, 2025. https://americasmi.com/insights/bolivia-2025-lithium-gas-economic-pressure/
- Radwin, Maxwell. "Bolivian communities push back against foreign-backed lithium projects." Mongabay, July 3, 2025. https://news.mongabay.com/2025/04/bolivian-communities-push-back-against-foreign-backed-lithium-projects/
- Radwin, Maxwell. "Rapid growth of Bolivia's lithium industry creating new problems for local communities." Mongabay, April 15, 2024. https://news.mongabay.com/2024/04/rapid-growth-of-bolivias-lithium-industry-creating-new-problems-for-local-communities/
- Wilson Center. "Can Bolivia Jump-Start its Lithium Industry? A Q&A with Analyst Juan Carlos Zuleta." https://www.wilsoncenter.org/blog-post/can-bolivia-jump-start-its-lithium-industry-qa-analyst-juan-carlos-zuleta
- Discovery Alert. "Bolivia Lithium Development: Massive Reserves Meet Production Challenges." October 23, 2025. https://discoveryalert.com.au/bolivia-lithium-development-2025-opportunities-challenges/
- Discovery Alert. "Bolivia Lithium Export Plans: Production & Partnerships." November 7, 2025. https://discoveryalert.com/bolivia-lithium-production-challenges-2025/
- S&P Global Commodity Insights. "Lithium Triangle's potential powerhouses face challenges in project progression." https://www.spglobal.com/commodity-insights/en/news-research/latest-news/metals/032425-lithium-triangles-potential-powerhouses-face-challenges-in-project-progression

### Argentina's Lithium Sector
- Reuters (via Kitco Media). "Argentina aims to boost lithium production by 75% in 2025, sees no risk from trade war." April 9, 2025. https://www.kitco.com/news/off-the-wire/2025-04-09/argentina-aims-boost-lithium-production-75-2025-sees-no-risk-trade-war
- Northern Miner. "Argentina says new projects will boost lithium production fivefold by 2025." https://secure.northernminer.com/news/argentina-says-new-projects-will-boost-lithium-production-fivefold-by-2025/1003854426
- Industrial Info Resources. "Lithium Argentina Plans to Boost Production in 2025." https://www.industrialinfo.com/news/article/lithium-argentina-plans-to-boost-production-in-2025--338043

## Dashboard ##
This repository includes an interactive dashboard (`index.html`) built with Chart.js, visualizing the trends discussed throughout this analysis. To view it:

1. Clone or download this repository
2. Open `index.html` in any web browser

The dashboard includes:

- **Total Export Value by Country (2017–2023)** — a log-scale line chart comparing Chile, Bolivia, and Argentina's combined carbonate and hydroxide export value by year. The log scale makes Bolivia's and Argentina's own trends visible alongside Chile's much larger figures, which would otherwise flatten them to near-invisibility on a standard linear scale.
- **Price per Kilogram (Lithium Carbonate)** — a line chart comparing the three countries' price per kilogram, revealing that Bolivia's price consistently exceeded Chile's despite its far smaller export volume.
- **Share of Combined Export Value by Year** — a stacked bar chart showing each country's percentage share of the three-country total, making Chile's dominance (91.8%–100% every year studied) immediately visible.
- **Chile: Lithium Hydroxide Price per Kilogram** — a supporting data table, included because Chile was the only one of the three countries to report hydroxide exports at all.
