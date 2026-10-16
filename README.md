Netflix Titles Exploratory Data Analysis (EDA)
Overview
This project explores the Netflix titles dataset using Python. It cleans selected fields, analyzes the distribution of movies and TV shows, explores release-year patterns, identifies common genres and countries, compares content types across leading countries, and applies a simple linear regression model to estimate content counts for the next two years.
Objectives
- Inspect the dataset structure and identify missing values.
- Clean selected text and date fields.
- Compare the number of Movies and TV Shows.
- Visualize Netflix titles by release year, with a closer look at releases since 1990.
- Find the most common genres and countries represented in the dataset.
- Compare Movies and TV Shows across the five countries with the most listed titles.
- Experiment with linear regression to predict future title counts from release year.
Technologies Used
- Python
- Jupyter Notebook
- pandas
- NumPy
- Matplotlib
- Seaborn
- scikit-learn
Project Files
.
├── Netflix_EDA.ipynb
├── netflix_titles.csv
└── README.md
Place netflix_titles.csv in the same directory as the notebook before running it. The notebook loads the data using:
netflix = pd.read_csv("netflix_titles.csv")
Analysis and Workflow
1. Load and inspect the data
The notebook loads the CSV into a pandas DataFrame and inspects its first rows, dimensions, data types, and missing-value counts.
2. Handle missing values and dates
- Missing values in director, cast, and country are replaced with "Unknown".
- Whitespace is removed from date_added.
- date_added is converted to a datetime value; invalid dates are coerced to missing values.
- Additional columns are created:
  - is_movie: 1 for Movies and 0 otherwise.
  - content_type: a copy of the type column.
  - year_added: year the title was added.
  - month_added: month the title was added.
3. Explore content types and release years
A pie chart compares Movies and TV Shows. Line charts show title counts by release year and focus on release years from 1990 onward.
4. Explore genres and countries
Genre and country values are split where multiple entries appear in a single field, then expanded for counting. The notebook visualizes the top 10 genres and top 5 countries.
5. Compare content by country and type
A cross-tabulation and heatmap compare the number of Movies and TV Shows for the five countries with the highest title counts.
6. Try a two-year prediction
The notebook groups titles by release_year, filters to years from 2000 onward, and fits a LinearRegression model using release year as the input feature. It then predicts counts for the two years after the latest year present in the filtered data.
Important: This is a basic exploratory trend estimate, not a reliable forecast of future Netflix additions or releases. The result depends on the dataset's coverage and the linear-trend assumption.
Setup and Run
1. Download or place the dataset file netflix_titles.csv in the project folder.
2. Install the dependencies:
   python -m pip install pandas numpy matplotlib seaborn scikit-learn jupyter
3. Start Jupyter Notebook:
   jupyter notebook
4. Open Netflix_EDA.ipynb and run the cells from top to bottom.
Notes
- The notebook expects the dataset columns used in its code, including type, release_year, date_added, director, cast, country, and listed_in.
- A later notebook cell references a release_decade column. Ensure that this column exists in the input data or create it before running that cell.
- Install packages in the terminal or a notebook cell using %pip install scikit-learn; a plain pip install scikit-learn line may not run as Python code in every notebook environment.
- Charts and predictions may differ depending on the version and contents of the dataset.
Future Improvements
- Add summary statistics and key findings to the notebook.
- Compare content additions by year and month.
- Improve missing-value handling and standardize country/genre names.
- Evaluate forecasting approaches using a time-based validation split and compare against a simple baseline.
- Add a requirements file and document the dataset source.
Author
Vindhya Vasini
