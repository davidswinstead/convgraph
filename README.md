# A/B Test Performance Analyzer

A privacy-focused, client-side A/B test analysis tool that visualizes conversion data and statistical significance. All processing happens locally in your browser - no data is ever sent to a server.

## Features

- **100% Local Processing** - All data remains in your browser, stored in localStorage
- **Flexible Data Input** - Supports both raw conversion data (4 columns) and pre-calculated rates (2 columns)
- **Automatic Configuration** - Intelligently detects data format and sets appropriate defaults
- **Statistical Analysis** - Calculates lift percentages with 95% confidence intervals
- **Responsive Design** - Adapts to any screen size with a 2×2 grid layout on wide screens
- **Configurable Series** - Create custom series from any combination of columns or ratios

## Data Format

### Tab-separated input with date in first column:

**4-Column Format** (Recommended for accurate cumulative analysis):
```
2025-01-01	1000	1050	120	140
2025-01-02	980	1020	115	135
```
Columns: `Date | Visits Control | Visits Variant | Conversions Control | Conversions Variant`

**2-Column Format** (Pre-calculated rates):
```
2025-01-01	12.5	13.8
2025-01-02	11.9	13.2
```
Columns: `Date | Control Rate % | Variant Rate %`

### Default Behavior

- **2 columns**: Series 1 = Control (Column 2), Series 2 = Variant (Column 3)
- **4 columns**: Series 1 = Control (Col 4 ÷ Col 2), Series 2 = Variant (Col 5 ÷ Col 3)
- **Other counts**: No defaults - configure manually

## Charts Displayed

### Day-by-Day Charts (Always shown)
1. **Conversion Rate** - Daily conversion rates for configured series
2. **Relative Lift %** - Percentage difference between variant and control with confidence intervals

### Cumulative Charts (Only for 4-column data)
3. **Cumulative Conversion Rate** - Running conversion rate showing stabilization over time
4. **Cumulative Relative Lift %** - How the statistical significance evolves as data accumulates

## Configuration Options

- **Series Type**: Direct column or ratio (one column divided by another)
- **Custom Labels**: Name your series anything you want
- **Custom Colors**: Choose colors for each series
- **Baseline Selection**: For lift charts, choose which series to use as the baseline

## Local Storage

Your data and configuration are automatically saved to browser localStorage:
- Last data input
- Series configuration
- Baseline preference

Click "Clear Storage" to reset everything.

## Privacy & Security

- No external API calls (except Chart.js CDN for rendering)
- No analytics or tracking
- No server-side processing
- Data never leaves your browser
- Perfect for confidential business data

## Deployment

Includes `.cpanel.yml` for automated deployment to cPanel hosting:
```yaml
deployment:
  tasks:
    - Syncs to ~/public_html/convgraph/
    - Sets permissions to 755
```

## Technical Stack

- Pure HTML/CSS/JavaScript
- [Chart.js](https://www.chartjs.org/) for visualizations
- CSS Grid for responsive layout
- LocalStorage API for persistence

## Browser Compatibility

Works in all modern browsers that support:
- ES6 JavaScript
- CSS Grid
- LocalStorage API
- Canvas (for Chart.js)

## License

Feel free to use and modify for your own purposes.
