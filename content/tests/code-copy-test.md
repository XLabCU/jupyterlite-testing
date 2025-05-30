# Code Copy Feature Test

This document tests the new code copy functionality with different programming languages.

## Python Code

```python
# This is a Python example
import pandas as pd
import matplotlib.pyplot as plt

def analyze_data(filename):
    """Load and analyze data from a CSV file."""
    df = pd.read_csv(filename)
    return df.describe()

# Generate sample plot
x = [1, 2, 3, 4, 5]
y = [2, 4, 6, 8, 10]
plt.plot(x, y)
plt.title("Sample Plot")
plt.show()
```

## R Code

```r
# This is an R example
library(ggplot2)
library(dplyr)

# Load data
data <- read.csv("sample_data.csv")

# Create visualization
ggplot(data, aes(x = variable1, y = variable2)) +
  geom_point() +
  geom_smooth(method = "lm") +
  labs(title = "Relationship Analysis",
       x = "Variable 1",
       y = "Variable 2")

# Summary statistics
summary(data)
```

## JavaScript Code

```javascript
// This is a JavaScript example
const data = [1, 2, 3, 4, 5];

function processData(arr) {
    return arr.map(x => x * 2)
              .filter(x => x > 5)
              .reduce((sum, x) => sum + x, 0);
}

const result = processData(data);
console.log(`Result: ${result}`);

// Async example
async function fetchData(url) {
    try {
        const response = await fetch(url);
        const data = await response.json();
        return data;
    } catch (error) {
        console.error('Error fetching data:', error);
    }
}
```

## Bash/Shell Commands

```bash
#!/bin/bash

# Data processing pipeline
echo "Starting data processing..."

# Download data
curl -o data.csv "https://example.com/data.csv"

# Process with Python
python3 process_data.py data.csv > results.txt

# Create backup
cp results.txt "backup_$(date +%Y%m%d).txt"

echo "Processing complete!"
```

## SQL Queries

```sql
-- Customer analysis query
SELECT 
    c.customer_id,
    c.customer_name,
    COUNT(o.order_id) as total_orders,
    SUM(o.order_total) as total_spent,
    AVG(o.order_total) as avg_order_value
FROM customers c
LEFT JOIN orders o ON c.customer_id = o.customer_id
WHERE o.order_date >= '2024-01-01'
GROUP BY c.customer_id, c.customer_name
HAVING COUNT(o.order_id) > 5
ORDER BY total_spent DESC
LIMIT 100;
```

## JSON Configuration

```json
{
  "name": "data-analysis-project",
  "version": "1.0.0",
  "description": "Advanced data analysis tools",
  "dependencies": {
    "pandas": "^2.0.0",
    "numpy": "^1.24.0",
    "matplotlib": "^3.7.0",
    "seaborn": "^0.12.0"
  },
  "scripts": {
    "analyze": "python analyze.py",
    "visualize": "python visualize.py",
    "test": "pytest tests/"
  },
  "config": {
    "data_path": "./data/",
    "output_path": "./results/",
    "plot_format": "png"
  }
}
```

## CSS Styling

```css
/* Data visualization dashboard styles */
.dashboard {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 20px;
    padding: 20px;
    background-color: #f8f9fa;
}

.chart-container {
    background: white;
    border-radius: 8px;
    padding: 16px;
    box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.chart-container h3 {
    margin-top: 0;
    color: #333;
    font-size: 1.2em;
}

.metric-card {
    text-align: center;
    padding: 24px;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
    border-radius: 12px;
}
```

## HTML Structure

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Data Analysis Dashboard</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="dashboard">
        <div class="chart-container">
            <h3>Sales Trend</h3>
            <canvas id="salesChart"></canvas>
        </div>
        <div class="chart-container">
            <h3>User Growth</h3>
            <canvas id="userChart"></canvas>
        </div>
    </div>
    
    <script src="chart.js"></script>
    <script src="dashboard.js"></script>
</body>
</html>
```

## Testing Instructions

1. **Open this file in preview mode** in JupyterLite
2. **Hover over any code block** - you should see a "Copy" button appear in the top-right corner
3. **Check for language labels** - each code block should show its language in the top-left corner
4. **Click the copy button** - it should copy the code to your clipboard and show "Copied!" briefly
5. **Test in a notebook** - create a new notebook, paste the code, and verify it works

## Expected Features

- ✅ **Grey background** for all code blocks
- ✅ **Copy button** appears on hover
- ✅ **Language labels** with color coding:
  - 🐍 Python (blue)
  - 📊 R (blue)
  - 🟨 JavaScript (yellow)
  - 🟢 Bash/Shell (green)
  - 🟧 SQL (orange)
  - ⚫ JSON (dark)
  - 🔵 CSS (blue)
  - 🟠 HTML (orange)
- ✅ **Success feedback** when copy succeeds
- ✅ **Fallback** for browsers without clipboard API

## Inline Code Test

This paragraph contains `inline code snippets` that should have a light grey background but no copy button. Only `block code` gets the copy functionality.

The inline code like `python`, `import pandas`, and `df.head()` should be styled differently from the block code above.