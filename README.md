# ECE-2112-PA-4
**Made by: Jomari Josh V. Barrientos | 2ECE-C**

The content of this repository contains the Programming Assignment 4 for the course ECE2112 or Advanced Computer Programming and Algorithms, this 1st semester of the A.Y. 2026 - 2027. This covers the 3 coding problems under Module 4 - Data Wrangling and Visualization

The following objectives of this assignment are to:
1. filter tabular data using several categorical and numerical conditions;
2. construct focused DataFrames by selecting relevant features;
3. summarize the relationship between categorical features and a numerical variable; and
4. communicate a data comparison using clear and correctly labeled plots.

Note: In this assignment the data will be based from the file `board2.xlsx` that was given. Furthermore the following libraries are used:
```python
import pandas as pd
import matplotlib.pyplot as plt
```

# A. Visayas Communication DataFrame
In this part, the task is to create a DataFrame named `VisComm` that contains the data for the students whose `Hometown` is `Visayas` and whose `Track` is `Communication`. It must also retain these columns in this order: `Name`, `Gender`, `Math`, `Electronics`, `Average`.

```python
df['Average'] = df[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1)
VisComm = df.loc[(df['Hometown'] == 'Visayas') &
           (df['Track'] == 'Communication'), ['Name', 'Gender', 'Math', 'Average']]
```

Afterward, display the result and its number of rows using `VisComm.shape[0]`
```python
print(VisComm)
print('\nNumber of rows:', VisComm.shape[0])
```
# B. Visayas Female DataFrame
This is to create a DataFrame named `VisFemale` and has a similar problem to the one earlier, but with the parameters of which `Hometown` is `Visayas`, `Gender` is `Female`, and retains only the columns of: `Name`, `Track`, `GEAS`, `Electronics`, and `Average`.

```python
VisFemale = df.loc[(df['Hometown'] == 'Visayas') &
           (df['Gender'] == 'Female'), ['Name', 'Track', 'GEAS', 'Electronics', 'Average']]
```

The next step is to display only the entries whose averages are at least 60.
```python
print(VisFemale[VisFemale['Average'] >= 60])
```

# C. Category-Average Visualization
For this part of the assignment, the task is to examine the `Average` among the categories of `Track`, `Gender`, and `Hometown`.

1. Compute the average of each using Pandas
```python
   dft = df.groupby('Track')['Average'].mean()
   dfg = df.groupby('Gender')['Average'].mean()
   dfh = df.groupby('Hometown')['Average'].mean()
```
2. Display the Summary Charts.
```python
   print('Average by Track\n', dft)
   print('Average by Gender\n', dfg)
   print('Average by Hometown\n', dfh)
```
3. Create one figure containing three bar charts.
   In this part of the code, creating three bar charts follows this formula:
```python
# Values
plt.subplot(1, 3, 1)
plt.bar(dft.index, dft.values, color = 'skyblue')
plt.title('Mean Average by Track')
plt.xlabel('Track')
plt.ylabel('Mean Average')
plt.xticks(rotation=20)
```
Wherein changes would be made corresponding to which part of the categories is constructed. In this case, the values for Track are considered.

4. Three concise statements identifying the three highest sample means for each category.
```python
print("1. The Track with the Highest Sample Mean is Communications")
print("2. The Gender with the Highest Sample Mean is Male")
print("3. The Hometown with the Highest Sample Mean is Luzon")
```

# Version History
September 17, 2026 - Initial README.md file was created

September 18, 2026 - README.md file was edited
