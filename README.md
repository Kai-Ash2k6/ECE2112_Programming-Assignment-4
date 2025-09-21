# ECE2112_Programming-Assignment-4 

 ###  Advance Computer Programming - S.Y. '24-'25  
 ### Name: `K. A. Gas*ng-n` || Section: `2 ECE - C`

### ----- Contents of this Assignment ----- 
    
  1. Problem 1 – Filtering Data with Multiple Conditions
      - Load `Board2.csv` into pandas.
      - Apply conditions (Visayas + Math, Instrumentation + Luzon + Electronics, Female + Mindanao + Average ≥ 55).
      - Select specific columns to display results.
    
  2. Problem 2 – Data Analysis by Groups
      - Compute `Average` for each student.
      - Group by Gender, Track, and Hometown.
      - Plot bar charts showing mean averages across these categories.
      
### ---------------- Notes ----------------
[Download Board2.csv](https://github.com/Kai-Ash2k6/ECE2112_Programming-Assignment-4/blob/main/Board2.csv) `as 'csv'`

  - I debugged my code several times to ensure the conditions matched 
      the requirements (e.g., multiple `filters` using `&`).
  - I reviewed my lab manual examples and YouTube tutorials for confirmation.
  - This repository is part of my journey in learning how `pandas` can 
      manipulate datasets and visualize patterns using `matplotlib`.


Verified groupby aggregations using pandas.

Created matplotlib bar charts for better data insights.

### .... Analysis / Notes .....
    
1. Problem 1
  - Loads `Board2.csv` into a pandas DataFrame.
  - Applies multiple conditions to filter subsets:
       * Visayas + Math < 70
       * Instrumentation Track + Luzon + Electronics > 70
       * Female + Mindanao + Average ≥ 55
  - Selects only the necessary columns for output.
  - Generalization / Conclusion:
        This problem demonstrates how to apply complex filtering rules
        in pandas to isolate rows of interest, a vital skill for data
        preprocessing and cleaning.

2. Problem 2
  - Calculates average grade per student and stores in a new column.
  - Groups data by Gender, Track, and Hometown using `.groupby()`.
  - Uses matplotlib to display bar charts for each grouping.
  - Generalization / Conclusion:
        Grouped analysis provides insights into performance trends across 
        categories. Visualizing results with plots makes interpretation clearer.


### .... Mini Tutorial .....

## ** Problem 1: Filtering Students with Multiple Conditions **

Step 1 — Import pandas

```python
import pandas as pd
````

Step 2 — Load the dataset

```python
kai = pd.read_csv('Board2.csv')
```

Step 3 — Apply conditions

```python
# a. Students from Visayas with Math < 70
Vis = kai[(kai['Hometown'] == 'Visayas') & (kai['Math'] < 70)]
Vis = Vis[['Name', 'Gender', 'Track', 'Math']]

# b. Instrumentation students from Luzon who passed Electronics
Instru = kai[(kai['Track'] == 'Instrumentation') & 
             (kai['Hometown'] == 'Luzon') & 
             (kai['Electronics'] > 70)]
Instru = Instru[['Name', 'GEAS', 'Electronics']]

# c. Female students from Mindanao with average ≥ 55
kai['Average'] = (kai['Math'] + kai['Electronics'] + kai['GEAS'] + kai['Communication']) / 4
Mindy = kai[(kai['Gender'] == 'Female') &
            (kai['Hometown'] == 'Mindanao') &
            (kai['Average'] >= 55)]
Mindy = Mindy[['Name', 'Track', 'Electronics', 'Average']]

```

Notes:

* Always use parentheses `( )` when combining multiple conditions with `&` or `|`.
* Select multiple columns with double brackets: `[['col1','col2']]`.

---

## \*\* Problem 2: Grouping & Visualization \*\*

### Code (full)


Step 1 — Import matplotlib

```python
import matplotlib.pyplot as plt
````

Step 2 — Group and plot averages

```python
# a. Group by Gender
avg_by_gender = kai.groupby('Gender')['Average'].mean()
plt.bar(avg_by_gender.index, avg_by_gender.values)
plt.title("Average Grade by Gender")
plt.ylabel("Average Grade")
plt.show()

# b. Group by Track
avg_by_track = kai.groupby('Track')['Average'].mean()
plt.bar(avg_by_track.index, avg_by_track.values)
plt.title("Average Grade by Track")
plt.ylabel("Average Grade")
plt.show()

# c. Group by Hometown
avg_by_hometown = kai.groupby('Hometown')['Average'].mean()
plt.bar(avg_by_hometown.index, avg_by_hometown.values)
plt.title("Average Grade by Hometown")
plt.ylabel("Average Grade")
plt.show()

````

Notes:
  - `.groupby()` is a powerful way to aggregate data in pandas.
  - Use `.mean()`, `.sum()`, or `.count()` depending on the analysis needed.
  - Bar charts are ideal for comparing averages across categories.

------------------------------------------------------------
## How to run (step-by-step)

  1. Ensure Board2.csv is in the same directory as your script or notebook.
  2. Put your code in files, e.g.:
     - assignment4_problem1.pynb 
  3. Open a terminal in that folder and run:
````
    python assignment4_problem.ipynb
````


-
---------------- End of Assignment #4 README ----------------










