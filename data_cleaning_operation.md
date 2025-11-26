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

3. **Rating Format Standardization**
   ```python
   df['RATING'] = df['RATING'].round(1)
   df['RATING'] = df['RATING'].apply(lambda x: f"{float(x):.1f}")
   ```
   - Rounded all ratings to 1 decimal place
   - Standardized format to ensure consistent display (e.g., '3.0' instead of '3.')

4. **RATING_TYPE Column Translation**
   ```python
   translation_map = {
       'Sangat Baik': 'Very Good', 'Veľmi dobré': 'Very Good',
       'Baik': 'Good', 'Bom': 'Good', 'Çok iyi': 'Very Good',
       'İyi': 'Good', 'Buono': 'Good', 'Média': 'Average',
       'Dobré': 'Good', 'Velmi dobré': 'Very Good',
       'Ottimo': 'Excellent', 'Bueno': 'Good',
       'Promedio': 'Average', 'Excelente': 'Excellent',
       'Muito bom': 'Very Good', 'Ortalama': 'Average',
       'Vynikajúce': 'Excellent', 'Muy Bueno': 'Very Good',
       'Media': 'Average', 'Skvělá volba': 'Excellent choice',
       'Průměr': 'Average', 'Średnio': 'Average',
       'Wybitnie': 'Outstanding', 'Skvělé': 'Excellent',
       'Eccellente': 'Excellent', 'Biasa': 'Ordinary',
       'Dobrze': 'Good', 'Bardzo dobrze': 'Very Good',
       'Terbaik': 'Best', 'Priemer': 'Average',
       'Nedostatek hlasů': 'Insufficient votes'
   }
   df['RATING_TYPE'] = df['RATING_TYPE'].map(translation_map).fillna(df['RATING_TYPE'])
   ```
   - Translated mixed language rating types to English
   - Covered multiple languages: Indonesian, Slovak, Turkish, Italian, Spanish, Portuguese, Czech, Polish
   - Preserved original values for untranslated terms

5. **VOTES Column Data Type Conversion**
   ```python
   df['VOTES'] = pd.to_numeric(df['VOTES'], errors='coerce').fillna(0).astype(int)
   ```
   - Converted VOTES column from object to numeric (integer) data type
   - Replaced non-numeric values ('NEW', '-', 'Opening', 'Temporarily') with 0
   - Ensured all vote counts are integers for proper numerical analysis

### Data Quality Check
- **RATING Column**: Mixed data types → All numeric values with standardized 1 decimal format
- **RATING_TYPE Column**: Mixed languages → Standardized English translations
- **VOTES Column**: Object type with mixed values → Integer type with numeric values only
- Null values: 0