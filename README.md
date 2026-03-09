# US Wage Distribution Chart (2023)

An interactive visualization of the distribution of US wage earners by net compensation, built from publicly available Social Security Administration (SSA) data.

## Live Site

Hosted via GitHub Pages. Open `index.html` in any browser — no server required.

## What This Shows

This chart visualizes how **net compensation** (take-home pay after taxes, Social Security, Medicare, and other deductions) is distributed across ~173.7 million US wage earners.

**Important:** All figures reflect **net (take-home) pay**, not gross income. This is what actually hits your bank account.

## Features

### Interactive Chart
- **Bar chart** showing the number of wage earners in each income bracket
- **Cumulative percentage line** ("% of Earners at or Below") showing what percentage of all earners fall at or below each bracket
- **Crosshair on hover** — a vertical guide line follows your cursor to help trace bars to the cumulative line
- **Tooltips** — hover any bar to see the exact earner count, percentage of total, cumulative %, and top X% ranking

### Color-Coded Zones
Bars are colored by percentile zone for quick visual identification:
- 🔵 **Blue** — Below Median (bottom 50%)
- 🟢 **Green** — Median to Top 10%
- 🟠 **Orange** — Top 10% to Top 5%
- 🟣 **Purple** — Top 5% to Top 1%
- 🔴 **Red** — Top 1%

### Annotation Lines
Dashed vertical lines mark key thresholds:
- **Median** (~$40-45K) — 50th percentile
- **Mean** (~$63,933) — average wage (skewed higher by top earners)
- **Top 10%** (~$125K+)
- **Top 5%** (~$175K+)
- **Top 1%** (~$350K+)

### "Where Do You Fall?" Calculator
Enter your take-home pay (the amount deposited to your bank after all deductions) in any time period:
- Per year, per month, per 2 weeks, per week, or per hour

The calculator converts to annual and shows which bracket you fall in, what percentage of earners make less, and your top X% ranking.

### Key Takeaways
Six callout cards below the chart highlight notable insights from the data, color-coded to match their corresponding zone on the chart.

### Download as PNG
A button at the bottom exports the entire page — title, chart, legend, and callout cards — as a high-resolution PNG image.

## Data Source

- **Source:** [Social Security Administration (SSA)](https://www.ssa.gov/cgi-bin/netcomp.cgi) — "Wage Statistics" → "Distribution of Net Compensation"
- **Year:** 2023 (most recent available as of March 2026)
- **Total wage earners:** 173,670,935
- **Mean net compensation:** $63,933
- **Median bracket:** $40,000–$44,999

The SSA typically publishes updated data around October each year.

## Updating the Data

When new SSA data is released, update these sections in `index.html`:

1. **`data` array** — each entry is `["label", earnerCount, cumulativePercent]`
2. **`brackets` array** — income range boundaries for the calculator
3. **Annotation indices** — `median`, `top10`, `top5`, `top1`, `meanIdx` (the array index where each threshold is crossed)
4. **Mean wage** — recalculate from total aggregate compensation ÷ total earners
5. **Header stats** — total earners, mean, and median displayed above the chart
6. **Title/subtitle** — update the year
7. **Callout cards** — update any stats referenced in the takeaways

Then commit and push:
```bash
git add index.html
git commit -m "Update to [YEAR] data"
git push
```

The site updates automatically within a few minutes.

## Tech Stack

Single self-contained HTML file. No build step, no dependencies to install.

- [Chart.js](https://www.chartjs.org/) — charting library
- [chartjs-plugin-annotation](https://www.chartjs.org/chartjs-plugin-annotation/) — annotation lines
- [html2canvas](https://html2canvas.hertzen.com/) — full-page PNG export

All libraries loaded via CDN.

## License

This project uses publicly available US government data from the SSA, which is in the public domain.
