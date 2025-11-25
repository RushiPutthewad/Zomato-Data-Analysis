# Data Cleaning Operations

## RATING Column Cleaning

### Issue Identified
The RATING column contained mixed data types including:
- Numeric values: '4.8', '4.3', '4.4', etc.
- Text values: 'NEW', 'Opening', 'Temporarily', '-'

### Cleaning Steps Performed

1. **Data Type Conversion**
   ```python
   df['RATING'] = pd.to_numeric(df['RATING'], errors='coerce')
   ```
   - Converted all values to numeric
   - Text values automatically became NaN

2. **Missing Value Imputation**
   ```python
   mean_rating = df['RATING'].mean()
   df['RATING'] = df['RATING'].fillna(mean_rating)
   ```
   - Calculated mean of numeric values only
   - Replaced NaN values (originally text) with mean value
   - Mean rating used: 3.48

### Result
- All text values ('NEW', 'Opening', 'Temporarily', '-') replaced with mean value (3.48)
- RATING column now contains only numeric values
- No null values remaining in RATING column

### Data Quality Check
- Before cleaning: Mixed data types (numeric + text)
- After cleaning: All numeric values
- Null values: 0