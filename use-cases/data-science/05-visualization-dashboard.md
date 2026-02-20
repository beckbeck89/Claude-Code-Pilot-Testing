# Use Case: Visualization and Dashboard

## Objective

Ask the AI tool to build publication-quality visualizations and an interactive dashboard from a dataset. Tests the tool's knowledge of visualization best practices, charting libraries, and ability to produce polished output.

## The Task

Using a public dataset (suggestions below), create:

### Part 1: Static Visualizations (matplotlib/seaborn)

Create **5 publication-quality charts** that tell a story about the data:

1. A distribution plot with meaningful annotations
2. A multi-variable comparison (grouped bar, faceted plot, or similar)
3. A time series or trend chart
4. A correlation or relationship visualization
5. A summary/overview chart (e.g., heatmap, treemap, or composite)

### Part 2: Interactive Dashboard (Plotly, Streamlit, or Panel)

Build a simple interactive dashboard with:
- At least 3 interactive charts
- A filter or selector that updates the charts
- A clear layout with a title and section headers

### Suggested Datasets

- **Gapminder**: `plotly.express.data.gapminder()`
- **Tips**: `seaborn.load_dataset('tips')`
- **Your own data**: Any dataset with at least 4-5 columns and 100+ rows

## Acceptance Criteria

### Static Charts
- [ ] All 5 charts render without errors
- [ ] Charts have titles, axis labels, and legends where appropriate
- [ ] Color choices are accessible (colorblind-friendly)
- [ ] Charts tell a story — they're not just random plots
- [ ] Figure sizes and font sizes are appropriate

### Interactive Dashboard
- [ ] Dashboard runs locally
- [ ] At least 3 interactive charts display correctly
- [ ] Filters/selectors work and update charts
- [ ] Layout is clean and organized
- [ ] Charts are responsive and informative

## Suggested Prompt

> "Using the Gapminder dataset, create 5 publication-quality static charts using matplotlib/seaborn that tell a story about global development. Then build a Streamlit dashboard with interactive charts and filters. Make everything look polished and professional."

## What to Observe

- Does it choose appropriate chart types for the data?
- Are the charts genuinely insightful or just defaults?
- Does it customize aesthetics (colors, fonts, spacing) or leave defaults?
- Does it annotate charts with meaningful callouts?
- How well does it handle the Streamlit/Plotly interactive components?
- Does the dashboard have a logical flow and narrative?
- Does it handle responsive layout and user interactions smoothly?
- Can it iterate on chart design when asked ("make it more colorblind-friendly")?
