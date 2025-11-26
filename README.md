# Zomato Data Analysis

[![Python](https://img.shields.io/badge/Python-3.13+-blue.svg)](https://www.python.org/downloads/)
[![Pandas](https://img.shields.io/badge/Pandas-Latest-green.svg)](https://pandas.pydata.org/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

## Overview

This repository provides a comprehensive solution for merging and analyzing fragmented Zomato restaurant/hotel CSV datasets. The tool consolidates multiple city-specific CSV files into a unified dataset suitable for data analysis, machine learning, and business intelligence applications.

## 🏗️ Project Structure

```
Zomato/
├── README.md
├── csv_merger.py
├── data_preprocessing.ipynb
├── data_cleaning_operation.md
├── Agra/
│   ├── 1-Agrahotels.csv
│   ├── 2-Agrahotels.csv
│   └── ...
├── Mumbai/
│   ├── 1-Mumbaihotels.csv
│   ├── 2-Mumbaihotels.csv
│   └── ...
├── Kolkata/
│   └── ...
└── merged_zomato_data.csv (output)
```

## 🚀 Quick Start

### Prerequisites

- Python 3.8 or higher
- pandas library

### Installation

```bash
# Clone the repository
git clone <repository-url>

# Go inside the project folder
cd Zomato
```

### Basic Usage

Run the csv_merger.py script to automatically merge all CSV files from city folders into a single dataset. The tool will:

- Recursively scan all directories for CSV files
- Add city information based on folder names
- Handle encoding issues automatically
- Remove duplicate records
- Fill missing values with 'Unknown' in categorical columns
- Generate merged_zomato_data.csv output file

## 📊 Features

- **Automated Discovery**: Recursively finds and processes CSV files across city directories
- **Data Integrity**: Handles encoding issues and malformed files gracefully
- **City Tagging**: Automatically adds city information based on folder structure
- **Duplicate Removal**: Eliminates duplicate records during merge process
- **Null Value Handling**: Fills missing values with 'Unknown' for consistency in categorical columns
- **Memory Efficient**: Optimized for large datasets with low memory usage
- **Error Handling**: Robust error handling for corrupted or inconsistent files

## 🛠️ Advanced Usage

### Memory Optimization for Large Datasets

For memory-constrained environments, the tool supports chunked processing to handle large datasets efficiently without running out of memory.

### Data Quality Validation

The merged dataset includes built-in validation that reports:
- Dataset shape and dimensions
- Number of unique cities processed
- Missing value counts
- Duplicate row detection

For detailed data cleaning operations and procedures, see [data_cleaning_operation.md](data_cleaning_operation.md)

## 📈 Data Analysis Examples

After merging, you can perform various analyses on the unified dataset:

- **City-wise restaurant distribution**: Analyze restaurant counts across different cities
- **Rating analysis**: Calculate average ratings and rating distributions
- **Cost analysis**: Examine cost patterns and median prices by city
- **Cuisine analysis**: Study cuisine preferences across different locations

## 🔧 Configuration

The tool supports various configuration options:
- **Encoding**: UTF-8 with fallback error handling
- **Duplicate removal**: Automatic duplicate detection and removal
- **Metadata addition**: Adds source file and city information
- **Chunk processing**: Configurable chunk size for memory optimization

## 📋 Requirements

```txt
pandas>=1.3.0
numpy>=1.21.0
python-dateutil>=2.8.0
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/enhancement`)
3. Commit changes (`git commit -am 'Add new feature'`)
4. Push to branch (`git push origin feature/enhancement`)
5. Create a Pull Request

## 📝 Best Practices

- **Data Validation**: Always validate merged data before analysis
- **Backup**: Keep original files as backup before processing
- **Documentation**: Document any custom preprocessing steps
- **Version Control**: Track changes to merged datasets

## 🐛 Troubleshooting

| Issue | Solution |
|-------|----------|
| Memory Error | Use `chunksize` parameter or process cities individually |
| Encoding Issues | Try different encodings: `latin-1`, `cp1252` |
| Column Mismatch | Use `pd.concat(sort=False)` to handle different schemas |
| Large File Size | Consider using Parquet format for better compression |

## 📊 Output Schema

The merged dataset includes:

- **Original Columns**: All columns from source CSV files
- **city**: City name derived from folder structure
- **source_file**: Original filename for traceability

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👥 Authors

- **Project Maintainer** - Initial work and ongoing maintenance

## 🙏 Acknowledgments

- Zomato for providing the dataset
- Pandas development team for the excellent data manipulation library
- Contributors and users who provided feedback and improvements

---

**Note**: This tool is designed for educational and research purposes. Please ensure compliance with data usage policies and terms of service.