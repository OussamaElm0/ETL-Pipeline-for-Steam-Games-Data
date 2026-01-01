# ETL Pipeline for Steam Games Data

This project implements an ETL (Extract, Transform, Load) pipeline for analyzing Steam games data from 2021 to 2025.

## Dataset Description

### Overview
The dataset (`a_steam_data_2021_2025.csv`) contains comprehensive information about **65,521 Steam games** released between 2021 and 2025.

### Dataset Structure
The dataset includes the following columns:

| Column Name | Data Type | Description |
|------------|-----------|-------------|
| `appid` | Integer | Unique Steam application ID for each game |
| `name` | String | Title of the game |
| `release_year` | Integer | Year the game was released (2021-2025) |
| `release_date` | String/Date | Specific release date of the game |
| `genres` | String | Game genres (semicolon-separated, e.g., "Action;Adventure;Indie") |
| `categories` | String | Game categories/features (semicolon-separated, e.g., "Single-player;Steam Achievements") |
| `price` | Float | Price of the game in USD |
| `recommendations` | Integer | Number of user recommendations/reviews |
| `developer` | String | Game developer name |
| `publisher` | String | Game publisher name |

### Data Characteristics

- **Total Records**: 65,521 games
- **Date Range**: 2021 - 2025
- **Price Range**: From free-to-play ($0.00) to premium titles
- **Missing Values**: 
  - Developer: 53 missing values
  - Publisher: 183 missing values
  - All other fields: No missing values

### Sample Data

```csv
appid,name,release_year,release_date,genres,categories,price,recommendations,developer,publisher
3057270,Seafarer's Gambit,2024,"Jul 5, 2024",Action;Adventure;Indie;RPG;Strategy,Single-player;Family Sharing,3.99,0,Bouncy Rocket Studios,Bouncy Rocket Studios
3822840,Capitalist Misadventures,2025,"Jul 25, 2025",Casual;Indie;Simulation;Strategy,Single-player;Save Anytime;Family Sharing,7.99,0,Caramelo Studios,Caramelo Studios
```

## ETL Pipeline

The project includes a Jupyter notebook (`ETL.ipynb`) that demonstrates the ETL process:

### Extract
- Loads the Steam games dataset from CSV file using pandas

### Transform
The transformation process includes:

1. **Missing Value Handling**
   - Fill missing `genres` and `categories` with "Other"
   - Fill missing `developer` and `publisher` with "Unknown"

2. **Data Type Conversion**
   - Convert `release_date` from string to datetime format
   - Standardize `release_year` data type

3. **Data Cleaning**
   - Handle semicolon-separated multi-value fields (genres, categories)
   - Standardize formatting across all fields

### Load
- The cleaned and transformed data is ready for analysis or loading into a database

## Usage

### Prerequisites
```bash
pip install pandas jupyter
```

### Running the ETL Pipeline

1. Clone the repository:
```bash
git clone https://github.com/OussamaElm0/ETL-Pipeline-for-Steam-Games-Data.git
cd ETL-Pipeline-for-Steam-Games-Data
```

2. Open the Jupyter notebook:
```bash
jupyter notebook ETL.ipynb
```

3. Run all cells to execute the complete ETL pipeline

### Loading the Dataset in Python

```python
import pandas as pd

# Load the dataset
df = pd.read_csv("a_steam_data_2021_2025.csv")

# Display basic information
print(f"Total games: {len(df)}")
print(f"\nColumns: {df.columns.tolist()}")
print(f"\nFirst few rows:\n{df.head()}")
```

## Data Analysis Opportunities

This dataset enables various analyses:

- **Pricing Trends**: Analyze game pricing patterns over the years
- **Genre Distribution**: Identify most popular game genres
- **Developer/Publisher Analysis**: Study market dominance and indie presence
- **Release Patterns**: Examine seasonal release trends
- **Feature Analysis**: Investigate common game categories and features
- **Recommendation Metrics**: Correlate game characteristics with user recommendations

## File Structure

```
ETL-Pipeline-for-Steam-Games-Data/
│
├── README.md                      # This file
├── ETL.ipynb                      # Jupyter notebook with ETL pipeline
└── a_steam_data_2021_2025.csv    # Raw Steam games dataset
```

## Data Source

The dataset contains Steam game information collected from the Steam platform, covering games released between 2021 and 2025.

## License

Please refer to the repository license for usage terms.

## Contributing

Contributions are welcome! Feel free to:
- Report issues
- Suggest improvements
- Submit pull requests

## Contact

For questions or feedback, please open an issue in the GitHub repository.
