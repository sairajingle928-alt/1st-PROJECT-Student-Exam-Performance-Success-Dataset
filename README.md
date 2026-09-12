# 1st-PROJECT-Student-Exam-Performance-Success-Dataset
<br>
Completed my first Data Analytics project: Student Exam Performance &amp; Success Dataset. Analyzed student performance using Python, Pandas, NumPy, data cleaning, descriptive statistics, correlation analysis, and data interpretation to identify key factors influencing exam outcomes and demonstrate practical data-driven insights.
<br>
import random

N = 21060

sample_data = {
    "student_id": list(range(1, N + 1)),
    "age": [random.randint(18, 80) for _ in range(N)],
    "gender": [random.choice(["Male", "Female"]) for _ in range(N)],
    "school_type": [random.choice(["Private", "Public"]) for _ in range(N)],
    "education_level": [
        random.choice(["High School", "Undergraduate"])
        for _ in range(N)
    ],
    "family_income": [
        random.choice(["Middle class", "Higher class", "Lower class"])
        for _ in range(N)
    ],
    "previous_exam_score": [
        round(random.uniform(30, 100), 2)
        for _ in range(N)
    ],
    "urban_rural": [
        random.choice(["urban", "suburban", "rural"])
        for _ in range(N)
    ],
    "parent_education": [
        random.choice([
            "Docterate",
            "Bachelors",
            "High school",
            "Associate",
            "Master"
        ])
        for _ in range(N)
    ],
}

sample_data
<br>
{'student_id': [1,
  2,
  3,
  4,
  5,
  6,
  7,
  8,
  9,
  10,
  11,
  12,
  13,
  14,
  15,
  16,
  17,
  18,
  19,
  20,
  21,
  22,
  23,
  24,
  25,
...
  'Master',
  'Bachelors',
  'High school',
  'Master',
  ...]}
  <br>
  sample_data
  <br>
  {'student_id': [1,
  2,
  3,
  4,
  5,
  6,
  7,
  8,
  9,
  10,
  11,
  12,
  13,
  14,
  15,
  16,
  17,
  18,
  19,
  20,
  21,
  22,
  23,
  24,
  25,
...
  'Master',
  'Bachelors',
  'High school',
  'Master',
  ...]}
  <br>
  PANDAS
  <br>
  #https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.loc.html
  <br>
  import pandas as pd
<br>
pd_sr = pdSeries(sample_data['gender'])
pd_sr
<br>
0          Male
1          Male
2          Male
3          Male
4        Female
          ...  
21055    Female
21056    Female
21057      Male
21058    Female
21059      Male
Length: 21060, dtype: str
<br>
pd_sr = pd.eries(sample_data['gender'])
pd_sr
<br>
import pandas as pd

pd_df = pd.DataFrame(sample_data)

pd_df
pd_df
<br>
			student_id	age	gender	school_type	education_level	family_income	previous_exam_score	urban_rural	parent_education
0	1	50	Male	Public	Undergraduate	Middle class	99.07	urban	Docterate
1	2	56	Male	Private	Undergraduate	Higher class	64.37	urban	High school
2	3	57	Male	Public	Undergraduate	Higher class	87.09	rural	Bachelors
3	4	55	Male	Private	High School	Higher class	94.01	rural	Associate
4	5	74	Female	Public	Undergraduate	Lower class	59.45	rural	Associate
...	...	...	...	...	...	...	...	...	...
21055	21056	20	Female	Public	Undergraduate	Higher class	94.89	suburban	High school
21056	21057	33	Female	Public	High School	Lower class	45.89	suburban	High school
21057	21058	78	Male	Public	Undergraduate	Middle class	55.01	urban	Docterate
21058	21059	78	Female	Private	High School	Lower class	68.85	rural	Docterate
21059	21060	64	Male	Private	Undergraduate	Higher class	37.49	urban	Docterate
21060 rows × 9 columns
<br>
type(pd_df)
pandas.DataFrame
<br>
type(sample_data)
<br>
dict
<br>
pd_df.info()
<br>
<class 'pandas.DataFrame'>
RangeIndex: 21060 entries, 0 to 21059
Data columns (total 9 columns):
 #   Column               Non-Null Count  Dtype  
---  ------               --------------  -----  
 0   student_id           21060 non-null  int64  
 1   age                  21060 non-null  int64  
 2   gender               21060 non-null  str    
 3   school_type          21060 non-null  str    
 4   education_level      21060 non-null  str    
 5   family_income        21060 non-null  str    
 6   previous_exam_score  21060 non-null  float64
 7   urban_rural          21060 non-null  str    
 8   parent_education     21060 non-null  str    
dtypes: float64(1), int64(2), str(6)
memory usage: 1.4 MB
<br>
pd_df.head()
<br>
student_id	age	gender	school_type	education_level	family_income	previous_exam_score	urban_rural	parent_education
0	1	50	Male	Public	Undergraduate	Middle class	99.07	urban	Docterate
1	2	56	Male	Private	Undergraduate	Higher class	64.37	urban	High school
2	3	57	Male	Public	Undergraduate	Higher class	87.09	rural	Bachelors
3	4	55	Male	Private	High School	Higher class	94.01	rural	Associate
4	5	74	Female	Public	Undergraduate	Lower class	59.45	rural	Associate
<br>
pd_df.tail()
<br>
student_id	age	gender	school_type	education_level	family_income	previous_exam_score	urban_rural	parent_education
21055	21056	20	Female	Public	Undergraduate	Higher class	94.89	suburban	High school
21056	21057	33	Female	Public	High School	Lower class	45.89	suburban	High school
21057	21058	78	Male	Public	Undergraduate	Middle class	55.01	urban	Docterate
21058	21059	78	Female	Private	High School	Lower class	68.85	rural	Docterate
21059	21060	64	Male	Private	Undergraduate	Higher class	37.49	urban	Docterate
<br>
pd_df.describe()
<br>
student_id	age	previous_exam_score
count	21060.00000	21060.000000	21060.000000
mean	10530.50000	49.136942	64.937887
std	6079.64267	18.181074	20.284254
min	1.00000	18.000000	30.000000
25%	5265.75000	33.000000	47.070000
50%	10530.50000	49.000000	64.785000
75%	15795.25000	65.000000	82.662500
max	21060.00000	80.000000	100.000000
<br>
type(pd_df.describe())
<br>
pandas.DataFrame
<br>
pd_df.columns
<br>
Index(['student_id', 'age', 'gender', 'school_type', 'education_level',
       'family_income', 'previous_exam_score', 'urban_rural',
       'parent_education'],
      dtype='str')
      <br>
      # Assign all seven column names in the correct order
# Assign all nine column names in the correct order
pd_df.columns = [
    'student_id',
    'age',
    'gender',
    'school_type',
    'education_level',
    'family_income',
    'previous_exam_score',
    'urban_rural',
    'parent_education'
]

pd_df.head()

pd_df.head()
<br>
student_id	age	gender	school_type	education_level	family_income	previous_exam_score	urban_rural	parent_education
0	1	50	Male	Public	Undergraduate	Middle class	99.07	urban	Docterate
1	2	56	Male	Private	Undergraduate	Higher class	64.37	urban	High school
2	3	57	Male	Public	Undergraduate	Higher class	87.09	rural	Bachelors
3	4	55	Male	Private	High School	Higher class	94.01	rural	Associate
4	5	74	Female	Public	Undergraduate	Lower class	59.45	rural	Associate
<br>
pd_df.head()
<br>
student_id	age	gender	school_type	education_level	family_income	previous_exam_score	urban_rural	parent_education
0	1	50	Male	Public	Undergraduate	Middle class	99.07	urban	Docterate
1	2	56	Male	Private	Undergraduate	Higher class	64.37	urban	High school
2	3	57	Male	Public	Undergraduate	Higher class	87.09	rural	Bachelors
3	4	55	Male	Private	High School	Higher class	94.01	rural	Associate
4	5	74	Female	Public	Undergraduate	Lower class	59.45	rural	Associate
<br>
# Restore the correct column names and order
pd_df = pd.DataFrame(sample_data)

# Rename the column
pd_df = pd_df.rename(columns={'school type': 'school_type'})

pd_df.head()
<br>
student_id	age	gender	school_type	education_level	family_income	previous_exam_score	urban_rural	parent_education
0	1	50	Male	Public	Undergraduate	Middle class	99.07	urban	Docterate
1	2	56	Male	Private	Undergraduate	Higher class	64.37	urban	High school
2	3	57	Male	Public	Undergraduate	Higher class	87.09	rural	Bachelors
3	4	55	Male	Private	High School	Higher class	94.01	rural	Associate
4	5	74	Female	Public	Undergraduate	Lower class	59.45	rural	Associate
<br>
# pandas was imported as pd in cell 1
pd_df.head()
<br>
student_id	age	gender	school_type	education_level	family_income	previous_exam_score	urban_rural	parent_education
0	1	50	Male	Public	Undergraduate	Middle class	99.07	urban	Docterate
1	2	56	Male	Private	Undergraduate	Higher class	64.37	urban	High school
2	3	57	Male	Public	Undergraduate	Higher class	87.09	rural	Bachelors
3	4	55	Male	Private	High School	Higher class	94.01	rural	Associate
4	5	74	Female	Public	Undergraduate	Lower class	59.45	rural	Associate
<br>
pd_df.shape
<br>
(21060, 9)
<br>
list(pd_df.index)
<br>
[0,
 1,
 2,
 3,
 4,
 5,
 6,
 7,
 8,
 9,
 10,
 11,
 12,
 13,
 14,
 15,
 16,
 17,
 18,
 19,
 20,
 21,
 22,
 23,
 24,
...
 996,
 997,
 998,
 999,
 ...]
 <br>
 pd_df.shape
 <br>
 (21060, 9)
 <br>
 pd_df['gender']#similar to how value of a key accessed in dictionary
 <br>
 0          Male
1          Male
2          Male
3          Male
4        Female
          ...  
21055    Female
21056    Female
21057      Male
21058    Female
21059      Male
Name: gender, Length: 21060, dtype: str
<br>
pd_df[['student_id' , 'age']].head()
<br>
student_id	age
0	1	50
1	2	56
2	3	57
3	4	55
4	5	74
<br>
pd_df.iloc[0:21060,0:890]
<br>
student_id	age	gender	school_type	education_level	family_income	previous_exam_score	urban_rural	parent_education
0	1	50	Male	Public	Undergraduate	Middle class	99.07	urban	Docterate
1	2	56	Male	Private	Undergraduate	Higher class	64.37	urban	High school
2	3	57	Male	Public	Undergraduate	Higher class	87.09	rural	Bachelors
3	4	55	Male	Private	High School	Higher class	94.01	rural	Associate
4	5	74	Female	Public	Undergraduate	Lower class	59.45	rural	Associate
...	...	...	...	...	...	...	...	...	...
21055	21056	20	Female	Public	Undergraduate	Higher class	94.89	suburban	High school
21056	21057	33	Female	Public	High School	Lower class	45.89	suburban	High school
21057	21058	78	Male	Public	Undergraduate	Middle class	55.01	urban	Docterate
21058	21059	78	Female	Private	High School	Lower class	68.85	rural	Docterate
21059	21060	64	Male	Private	Undergraduate	Higher class	37.49	urban	Docterate
21060 rows × 9 columns
<br>
pd_df.iloc[0:21060]
<br>
student_id	age	gender	school_type	education_level	family_income	previous_exam_score	urban_rural	parent_education
0	1	50	Male	Public	Undergraduate	Middle class	99.07	urban	Docterate
1	2	56	Male	Private	Undergraduate	Higher class	64.37	urban	High school
2	3	57	Male	Public	Undergraduate	Higher class	87.09	rural	Bachelors
3	4	55	Male	Private	High School	Higher class	94.01	rural	Associate
4	5	74	Female	Public	Undergraduate	Lower class	59.45	rural	Associate
...	...	...	...	...	...	...	...	...	...
21055	21056	20	Female	Public	Undergraduate	Higher class	94.89	suburban	High school
21056	21057	33	Female	Public	High School	Lower class	45.89	suburban	High school
21057	21058	78	Male	Public	Undergraduate	Middle class	55.01	urban	Docterate
21058	21059	78	Female	Private	High School	Lower class	68.85	rural	Docterate
21059	21060	64	Male	Private	Undergraduate	Higher class	37.49	urban	Docterate
21060 rows × 9 columns
<br>
pd_df.iloc[0:3]
<br>
student_id	age	gender	school_type	education_level	family_income	previous_exam_score	urban_rural	parent_education
0	1	50	Male	Public	Undergraduate	Middle class	99.07	urban	Docterate
1	2	56	Male	Private	Undergraduate	Higher class	64.37	urban	High school
2	3	57	Male	Public	Undergraduate	Higher class	87.09	rural	Bachelors
<br>
pd_df.iloc[:,0:1]
<br>
student_id
0	1
1	2
2	3
3	4
4	5
...	...
21055	21056
21056	21057
21057	21058
21058	21059
21059	21060
21060 rows × 1 columns
<br>
pd_df.iloc[:,:]
<br>
student_id	age	gender	school_type	education_level	family_income	previous_exam_score	urban_rural	parent_education
0	1	50	Male	Public	Undergraduate	Middle class	99.07	urban	Docterate
1	2	56	Male	Private	Undergraduate	Higher class	64.37	urban	High school
2	3	57	Male	Public	Undergraduate	Higher class	87.09	rural	Bachelors
3	4	55	Male	Private	High School	Higher class	94.01	rural	Associate
4	5	74	Female	Public	Undergraduate	Lower class	59.45	rural	Associate
...	...	...	...	...	...	...	...	...	...
21055	21056	20	Female	Public	Undergraduate	Higher class	94.89	suburban	High school
21056	21057	33	Female	Public	High School	Lower class	45.89	suburban	High school
21057	21058	78	Male	Public	Undergraduate	Middle class	55.01	urban	Docterate
21058	21059	78	Female	Private	High School	Lower class	68.85	rural	Docterate
21059	21060	64	Male	Private	Undergraduate	Higher class	37.49	urban	Docterate
21060 rows × 9 columns
<br>
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt

import plotly.express as px
import plotly.io as pio
#Option A: Renders the chart inside a local inline iframe (higly reliable)
pio.renderers.default = "notebook_connected"

pd.set_option('display.float_format', lambda x: '%.4f' % x)
<br>
from pathlib import Path

import plotly.express as px
import plotly.express as px

csv_path = Path.cwd()
data_file = csv_path / "student_data_xlsr.xlsx"

try:
    student_data = pd.read_excel(data_file)
except (FileNotFoundError, PermissionError):
    student_data = pd_df.copy()

student_data.head()

try:
    student_data = pd.read_excel(data_file)
except (FileNotFoundError, PermissionError):
    # Use the already loaded data if the Excel file is open or locked
    student_data = pd_df.copy()

student_data.head()
student_data.head()
<br>
student_id	age	gender	school_type	education_level	family_income	previous_exam_score	urban_rural	parent_education
0	1	50	Male	Public	Undergraduate	Middle class	99.0700	urban	Docterate
1	2	56	Male	Private	Undergraduate	Higher class	64.3700	urban	High school
2	3	57	Male	Public	Undergraduate	Higher class	87.0900	rural	Bachelors
3	4	55	Male	Private	High School	Higher class	94.0100	rural	Associate
4	5	74	Female	Public	Undergraduate	Lower class	59.4500	rural	Associate
<br>
student_data.info()
<br>
<class 'pandas.DataFrame'>
RangeIndex: 21060 entries, 0 to 21059
Data columns (total 9 columns):
 #   Column               Non-Null Count  Dtype  
---  ------               --------------  -----  
 0   student_id           21060 non-null  int64  
 1   age                  21060 non-null  int64  
 2   gender               21060 non-null  str    
 3   school_type          21060 non-null  str    
 4   education_level      21060 non-null  str    
 5   family_income        21060 non-null  str    
 6   previous_exam_score  21060 non-null  float64
 7   urban_rural          21060 non-null  str    
 8   parent_education     21060 non-null  str    
dtypes: float64(1), int64(2), str(6)
memory usage: 1.4 MB
<br>
import pandas as pd
student_data['school type'] = student_data['school_type']

student_data.head()
student_data.head()
<br>
student_id	age	gender	school_type	education_level	family_income	previous_exam_score	urban_rural	parent_education	school type
0	1	50	Male	Public	Undergraduate	Middle class	99.0700	urban	Docterate	Public
1	2	56	Male	Private	Undergraduate	Higher class	64.3700	urban	High school	Private
2	3	57	Male	Public	Undergraduate	Higher class	87.0900	rural	Bachelors	Public
3	4	55	Male	Private	High School	Higher class	94.0100	rural	Associate	Private
4	5	74	Female	Public	Undergraduate	Lower class	59.4500	rural	Associate	Public
<br>
student_data.head()
<br>
student_id	age	gender	school_type	education_level	family_income	previous_exam_score	urban_rural	parent_education	school type
0	1	50	Male	Public	Undergraduate	Middle class	99.0700	urban	Docterate	Public
1	2	56	Male	Private	Undergraduate	Higher class	64.3700	urban	High school	Private
2	3	57	Male	Public	Undergraduate	Higher class	87.0900	rural	Bachelors	Public
3	4	55	Male	Private	High School	Higher class	94.0100	rural	Associate	Private
4	5	74	Female	Public	Undergraduate	Lower class	59.4500	rural	Associate	Public
<br>
student_data.columns = [i.lower() for i in student_data.columns]
<br>
# Use the complete dataframe that contains education_level
student_data = pd_df.copy()

# Ensure consistent column names
student_data.columns = student_data.columns.str.lower().str.replace(" ", "_")

print(student_data["education_level"].min())
print(student_data["education_level"].max())
<br>
High School
Undergraduate
<br>
TOTAL NUMBER OF STUDENTS
<br>
print('Total number of student_id: {}'.format(student_data['student_id'].nunique()))
<br>
Total number of student_id: 21060
<br>
# -- Underlying question could be: How many HCPs are prescribing pembro each month or in atleast 2 months
grouped_student_data_month = (
    student_data.groupby('school_type', as_index=False)
    .agg(
        total_students=('student_id', 'nunique'),
        average_age=('age', 'mean')
    )
)

print(grouped_student_data_month)

print(
    'Total number of students: {}'.format(
        student_data['student_id'].nunique()
    )
)
print(grouped_student_data_month.head(), end = '\n\n')
student_id_with_no_student_in_either_month = student_data.loc[
    student_data['education_level'].isna(),
    'student_id'
].unique()

no_student = student_data.loc[
    student_data['student_id'].isin(student_id_with_no_student_in_either_month),
    'family_income'
].nunique()

print(
    'Total number of student IDs without an education level: '
    f'{len(student_id_with_no_student_in_either_month)}'
)
print(f'Total number of affected family-income groups: {no_student}')
no_student = student_data.loc[
    student_data['student_id'].isin(student_id_with_no_student_in_either_month),
    'family_income'
].nunique()
print('Total number of student id in either of the months: {}'.format(len(student_id_with_no_student_in_either_month)))
print(
    'Total number of unique student IDs: '
    f"{student_data['student_id'].nunique()}"
)
<br>
school_type  total_students  average_age
0     Private           10481      49.0969
1      Public           10579      49.1766
Total number of students: 21060
  school_type  total_students  average_age
0     Private           10481      49.0969
1      Public           10579      49.1766

Total number of student IDs without an education level: 0
Total number of affected family-income groups: 0
Total number of student id in either of the months: 0
Total number of unique student IDs: 21060
<br>
HOW MANY STUDENTS DAILYU COME IN SCHOOL?
<br>
# -- can be interpreted similar to above question

# Count unique students with a recorded family-income value
no_student_id = student_data.loc[
    student_data['family_income'].notna(),
    'student_id'
].nunique()

print(
    'Total number of Student coming in school anytime in past 4 months: {}'.format(
        no_student_id
        <br>
    )
)

print(
    'Total number of Student coming in school anytime in past 4 months: {}'.format(
        no_student_id
    )
)
<br>
Total number of Student coming in school anytime in past 4 months: 21060
Total number of Student coming in school anytime in past 4 months: 21060
<br>
What are number of student who finally not stable ?
<br>
from pathlib import Path
import pandas as pd

# Prefer the actual workbook already defined in the notebook
# If it doesn't exist, fall back to the generated dataframe
data_file = Path(r"C:\Users\saira\OneDrive\Desktop\PYTHON\student_data_xlsr.xlsx")

try:
    if data_file.exists():
        student_data = pd.read_excel(data_file)
    else:
        student_data = pd_df.copy()
except (FileNotFoundError, PermissionError, ValueError):
    student_data = pd_df.copy()

# Normalize column names
student_data = student_data.copy()
student_data.columns = [str(c).strip().lower().replace(" ", "_") for c in student_data.columns]

student_data.head()
<br>
student_id	age	gender	school_type	education_level	family_income	previous_exam_score	urban_rural	parent_education
0	1	50	Male	Public	Undergraduate	Middle class	99.0700	urban	Docterate
1	2	56	Male	Private	Undergraduate	Higher class	64.3700	urban	High school
2	3	57	Male	Public	Undergraduate	Higher class	87.0900	rural	Bachelors
3	4	55	Male	Private	High School	Higher class	94.0100	rural	Associate
4	5	74	Female	Public	Undergraduate	Lower class	59.4500	rural	Associate
<br>
student_data_family_income = student_data['family_income']
<br>
student_data_family_income.head()
<br>
0    Middle class
1    Higher class
2    Higher class
3    Higher class
4     Lower class
Name: family_income, dtype: str
<br>
Total Number Of lower class student?
<br>
# Total number of students in the "Lower class" income group
total_number_lower_class = (
    student_data[student_data['family_income'] == 'Lower class']
    ['student_id']
    .nunique()
)

print(f"Total number of students in lower class: {total_number_lower_class}")
<br>
Total number of students in lower class: 7038
<br>
student_per_previous_exam_score = (
    student_data.groupby('previous_exam_score', as_index=False)
    .agg(student_count=('student_id', 'nunique'))
)

print(student_per_previous_exam_score.head(), end='\n\n')

gender_order = (
    student_data.groupby('gender')['age']
    .mean()
    .sort_values(ascending=False)
    .index
)

plt.figure(figsize=(15, 9))
sns.barplot(
    data=student_data,
    x='gender',
    y='age',
    order=gender_order,
    errorbar=None
)
plt.title('Average Age by Gender')
plt.show()

plt.figure(figsize=(15, 9))
sns.countplot(
    data=student_data,
    x='gender',
    hue='school_type'
)
plt.title('Students by Gender and School Type')
plt.show()
print(student_per_previous_exam_score .head(), end = '\n\n')

# previous_exam_score is a column, not a separate DataFrame.
# The score is already expressed as a percentage.
student_data['previous_exam_score_percent'] = (
    student_data['previous_exam_score'].clip(0, 100)
)

print(student_data[['student_id', 'previous_exam_score',
                    'previous_exam_score_percent']].head())
print(student_data.head(), end = '\n\n')

plt.figure(figsize=(15,9))
sns.barplot(
    data=student_data,
    x='gender',
    y='age',
    order=gender_order,
    errorbar=None
)
plt.show()

plt.figure(figsize=(15,9))
sns.countplot(
    data=student_data,
    x='gender',
    hue='school_type',
    order=gender_order
)
plt.title('Students by Gender and School Type')
plt.show()
<br>
previous_exam_score  student_count
0              30.0000              2
1              30.0100              2
2              30.0300              4
3              30.0400              6
4              30.0500              4
<img width="1229" height="778" alt="image" src="https://github.com/user-attachments/assets/d0b9a67e-1e45-474d-a9a2-6669e8387429" />
<img width="1247" height="778" alt="output 2" src="https://github.com/user-attachments/assets/c158462c-79e5-4dfb-96b3-b9a271381f83" />
previous_exam_score  student_count
0              30.0000              2
1              30.0100              2
2              30.0300              4
3              30.0400              6
4              30.0500              4

   student_id  previous_exam_score  previous_exam_score_percent
0           1              99.0700                      99.0700
1           2              64.3700                      64.3700
2           3              87.0900                      87.0900
3           4              94.0100                      94.0100
4           5              59.4500                      59.4500
   student_id  age  gender school_type education_level family_income  \
0           1   50    Male      Public   Undergraduate  Middle class   
1           2   56    Male     Private   Undergraduate  Higher class   
2           3   57    Male      Public   Undergraduate  Higher class   
3           4   55    Male     Private     High School  Higher class   
4           5   74  Female      Public   Undergraduate   Lower class   

   previous_exam_score urban_rural parent_education  \
0              99.0700       urban        Docterate   
1              64.3700       urban      High school   
2              87.0900       rural        Bachelors   
3              94.0100       rural        Associate   
...
2                      87.0900  
3                      94.0100  
4                      59.4500  
<img width="1229" height="756" alt="output 3" src="https://github.com/user-attachments/assets/342e928e-5ec4-4ec1-bcc3-f6841164a2bf" />
<img width="1247" height="778" alt="output 4" src="https://github.com/user-attachments/assets/fd37fc86-fd22-4e6c-b25d-10d499093af7" />
IS STUDENT IN SCHOOL WITH GOODS PREVIOUS MARKS ARE INCREASING ?
# Use the existing column name
student_data_monthly = student_data[
    ['student_id', 'previous_exam_score']
].copy()

# Define "good marks" as a score of 75 or higher
student_data_monthly['good_marks'] = (
    student_data_monthly['previous_exam_score'] >= 75
)

# Sort students and compare each score with the previous student
student_data_monthly = student_data_monthly.sort_values('student_id')
student_data_monthly['score_change'] = (
    student_data_monthly['previous_exam_score'].diff()
)

print(student_data_monthly.head(), end='\n\n')

print(
    f"Students with good marks: "
    f"{student_data_monthly['good_marks'].sum()}"
)

print(
    f"Average score change: "
    f"{student_data_monthly['score_change'].mean():.2f}"
)
# Keep the existing monthly data sorted by student_id
student_data_monthly = student_data_monthly.sort_values(
    by='student_id'
).reset_index(drop=True)

print(student_data_monthly.head(), end='\n\n')

# Add family income from the existing student_data DataFrame
student_data_monthly = student_data_monthly.merge(
    student_data[['student_id', 'family_income']],
    on='student_id',
    how='left'
)

print(student_data_monthly.head(), end='\n\n')

student_data_monthly['date'] = (
    student_data_monthly['good_marks'].astype(str)
)
print(student_data_monthly.head(), end = '\n\n')

# family_income was already added during the merge above.
# Preserve its categorical values and handle any missing entries.
student_data_monthly['family_income'] = (
    student_data_monthly['family_income'].fillna('Unknown')
)
print(student_data_monthly.head(), end = '\n\n')

student_data_monthly['date'] = student_data_monthly['good_marks'].astype('str')
<br>
student_id  previous_exam_score  good_marks  score_change
0           1              99.0700        True           NaN
1           2              64.3700       False      -34.7000
2           3              87.0900        True       22.7200
3           4              94.0100        True        6.9200
4           5              59.4500       False      -34.5600

Students with good marks: 7495
Average score change: -0.00
   student_id  previous_exam_score  good_marks  score_change
0           1              99.0700        True           NaN
1           2              64.3700       False      -34.7000
2           3              87.0900        True       22.7200
3           4              94.0100        True        6.9200
4           5              59.4500       False      -34.5600

   student_id  previous_exam_score  good_marks  score_change family_income
0           1              99.0700        True           NaN  Middle class
1           2              64.3700       False      -34.7000  Higher class
2           3              87.0900        True       22.7200  Higher class
3           4              94.0100        True        6.9200  Higher class
4           5              59.4500       False      -34.5600   Lower class

   student_id  previous_exam_score  good_marks  score_change family_income  \
0           1              99.0700        True           NaN  Middle class   
...
2   True  
3   True  
4  False  
<br>
plt.figure(figsize=(5,5))
sns.lineplot(
    data=student_data_monthly,
    x='date',
    y='good_marks',
    estimator='mean',
    errorbar=None,
    marker='o'
)
plt.xlabel('Good Marks')
plt.ylabel('Proportion of Students')
plt.title('Students with Good Marks')
plt.show()
<br>
<img width="459" height="470" alt="output 5" src="https://github.com/user-attachments/assets/9e16bd78-16d6-4e96-92d7-fcd11835f372" />
<br>
long_data = student_data.melt(
    id_vars=['student_id', 'age'],
    value_vars=['family_income', 'school_type'],
    var_name='attribute',
    value_name='value'
)
print(long_data.head(10), end = '\n\n')
<br>
student_id  age      attribute         value
0           1   50  family_income  Middle class
1           2   56  family_income  Higher class
2           3   57  family_income  Higher class
3           4   55  family_income  Higher class
4           5   74  family_income   Lower class
5           6   31  family_income  Higher class
6           7   70  family_income  Middle class
7           8   63  family_income  Middle class
8           9   56  family_income   Lower class
9          10   60  family_income  Higher class
<br>
import seaborn as sns

import matplotlib.pyplot as plt

plt.figure(figsize=(5, 5))
import matplotlib.pyplot as plt

# Use student_data if available; otherwise use the existing pd_df DataFrame
source_df = student_data if 'student_data' in globals() else pd_df

school_type = source_df[['age', 'school_type']].rename(
    columns={'school_type': 'value'}
).copy()

school_type['value_num'] = school_type['value'].map({
    'Private': 1,
    'Public': 0
})

plt.figure(figsize=(5, 5))

sns.lineplot(
    data=school_type,
    x='age',
    y='value_num',
    estimator='mean',
    errorbar=None
)

plt.xlabel('Age')
plt.ylabel('Average School Type')
plt.title('School Type by Age')
plt.show()

school_type['value_num'] = school_type['value'].map({
    'Private': 1,
    'Public': 0
})
school_type['value_num'] = school_type['value'].map({'Private': 1, 'Public': 0})

sns.lineplot(
    data=school_type,
    x='age',
    y='value_num',
    estimator='mean',
    errorbar=None
)
<br>
<img width="468" height="469" alt="output 6" src="https://github.com/user-attachments/assets/7f9f9fca-f779-4f47-a3cf-bb8882fa6a1f" />
<br>
<img width="576" height="432" alt="output 7" src="https://github.com/user-attachments/assets/d6a131d8-1061-412e-8792-d7c15ae9d118" />
<br>
import pandas as pd

# Reuse the dataframe already created in earlier notebook cells.
# This avoids trying to open the nonexistent placeholder file.
if 'student_data' not in globals():
    if 'pd_df' in globals():
        student_data = pd_df.copy()
    elif 'sample_data' in globals():
        student_data = pd.DataFrame(sample_data)
    else:
        # Fallback data if the setup cells have not been executed
        student_data = pd.DataFrame({
            'student_id': [1, 2, 3, 4],
            'previous_exam_score': [60, 70, 80, 90]
        })

    # This column is not present in the original dataset, so create it safely.
    if 'other_student_increase_marks' not in student_data.columns:
        student_data['other_student_increase_marks'] = (
        student_data['previous_exam_score']
        )


# CAGR of Student Exam Scores
def cagr(start_val, end_val, time_months):
    return (end_val/start_val)**(1/(time_months/12)) - 1


student_data_monthly = student_data[

    ['student_id', 'previous_exam_score']
].sort_values('student_id').reset_index(drop=True)

student_cagr = cagr(
    start_val=student_data_monthly['previous_exam_score'].iloc[0],
    end_val=student_data_monthly['previous_exam_score'].iloc[-1],
    time_months=4
)

other_student_cagr = student_cagr

print('Student CAGR:', student_cagr)
print('Other student CAGR:', other_student_cagr)

# Include the required column in the monthly dataframe
# Ensure the required column exists before selecting it
if 'other_student_increase_marks' not in student_data.columns:
    student_data['other_student_increase_marks'] = (
        student_data['previous_exam_score'].copy()
    )

student_data_monthly = (
    student_data[
        ['student_id', 'previous_exam_score', 'other_student_increase_marks']
    ]
    .sort_values('student_id')
    .reset_index(drop=True)
)

other_student_cagr = cagr(
    start_val=student_data_monthly[
        'other_student_increase_marks'
    ].iloc[0],
    end_val=student_data_monthly[
        'other_student_increase_marks'
    ].iloc[-1],
    time_months=4
)

print('public:', student_cagr, 'private:', other_student_cagr)
<br>
Student CAGR: -0.9458099149924727
Other student CAGR: -0.9458099149924727
public: -0.9458099149924727 private: -0.9458099149924727
<br>
import pandas as pd
# how many student are got passes and school is over
# how many are doing jobs 

# Count students who passed and have a valid school record
pass_score = 50

student_data_passes_school = student_data[
    (student_data["previous_exam_score"] >= pass_score)
    & (student_data["school_type"].notna())
].copy()

# Job information is not present in this dataset, so handle it safely
if "job_status" in student_data.columns:
    student_data_doing_job = student_data[
        student_data["job_status"].str.lower().eq("working")
    ].copy()
else:
    student_data_doing_job = pd.DataFrame(columns=student_data.columns)

print(f"Students who passed and school is over: {len(student_data_passes_school)}")
print(f"Students doing jobs: {len(student_data_doing_job)}")
student_data_doing_job_count = len(student_data_doing_job)
stdnet_data = student_data_doing_job.head(675).copy()
<br>
Students who passed and school is over: 14943
Students doing jobs: 0
<br>
# Create a graph for it now
plt
# Create a graph for students who passed and school is over
pass_counts = (
    student_data_passes_school.groupby("school_type", as_index=False)
    .agg(student_count=("student_id", "nunique"))
)

plt.figure(figsize=(6, 5))
sns.barplot(
    data=pass_counts,
    x="school_type",
    y="student_count",
    palette="viridis"
)
plt.title("Students Who Passed and School is Over by School Type")
plt.xlabel("School Type")
plt.ylabel("Number of Students")
plt.show()
<br>
C:\Users\saira\AppData\Local\Temp\ipykernel_10040\613524243.py:10: FutureWarning: 

Passing `palette` without assigning `hue` is deprecated and will be removed in v0.14.0. Assign the `x` variable to `hue` and set `legend=False` for the same effect.

  sns.barplot(
  <br>
  <img width="555" height="470" alt="output 8" src="https://github.com/user-attachments/assets/e04c0ae9-449f-4428-9347-c9a09d7c9220" />

