# Python for Data Science — Tomorrow Exam Guide

### MCQ-focused last-minute revision

I’ve built this from your **course outline + all four uploaded weekly assignment PDFs**, so the emphasis is on the kinds of questions your instructor has already used. The assignment pattern strongly suggests that **output prediction, data types, indexing, pandas syntax, preprocessing, and basic ML concepts** are important.    

---

# 1. WEEK 1 — PYTHON BASICS

## 1.1 Spyder basics

Know these terms:

**Spyder** = Python development environment commonly used for data science.

Important concepts from your outline:

* **Working directory** → folder where Python looks for/read/writes files by default.
* **Script file** → `.py` file containing Python code.
* **Console** → where commands execute and results appear.
* **Variable Explorer / Environment** → shows variables currently stored.
* **Clear console** ≠ **clear variables**.
* **Comments** → begin with `#`.

Example:

```python
x = 10        # variable
print(x)
```

Everything after `#` on that line is a comment.

---

# 2. VARIABLES

Python variables do not require explicit declaration of type.

```python
x = 10
name = "RK"
price = 15.5
```

Python determines the type from the assigned value.

### Valid names

```python
name
variable1
my_variable
_price
```

### Invalid names

```python
1variable
my variable
variable#
```

Your Week 1 assignment specifically tests invalid variable names and marks `1 variable` and `variable#` as invalid. 

### Remember

A Python variable name:

* cannot start with a digit
* cannot contain spaces
* should use letters, digits and `_`
* is **case-sensitive**

```python
age
Age
AGE
```

These are three different names.

---

# 3. PYTHON DATA TYPES

Know these extremely well:

| Data type | Example         |
| --------- | --------------- |
| `int`     | `10`            |
| `float`   | `10.5`          |
| `str`     | `"Python"`      |
| `bool`    | `True`, `False` |
| `list`    | `[1,2,3]`       |
| `tuple`   | `(1,2,3)`       |
| `set`     | `{1,2,3}`       |
| `dict`    | `{"a":1}`       |

### Check the type

```python
type(x)
```

Example:

```python
x = 10
type(x)
```

Output:

```python
int
```

Your Week 3 assignment also contains a question where the expected sequence of types is:

```text
bool, int, float, float, str
```

so **type identification from values/code is clearly an exam pattern**. 

---

# 4. TYPE CONVERSION

Important functions:

```python
int()
float()
str()
bool()
```

Examples:

```python
int("10")       # 10
float("10")     # 10.0
str(10)         # "10"
```

### Important trap

```python
x = "Mayur"
float(x)
```

The syntax for conversion is `float(x)`, but `"Mayur"` is not a numeric string, so it cannot actually be converted to a float and raises a conversion error.

Your assignment presents this exact situation and marks the "cannot convert" option. 

---

# 5. ARITHMETIC OPERATORS

Memorize:

| Operator | Meaning        | Example     |
| -------- | -------------- | ----------- |
| `+`      | addition       | `5+2 = 7`   |
| `-`      | subtraction    | `5-2 = 3`   |
| `*`      | multiplication | `5*2 = 10`  |
| `/`      | division       | `5/2 = 2.5` |
| `//`     | floor division | `5//2 = 2`  |
| `%`      | remainder      | `5%2 = 1`   |
| `**`     | exponent       | `5**2 = 25` |

## Extremely important MCQ trap

```python
6 / 3.3
6 // 3.3
```

Both produce **float** values because one operand is a float.

Your Week 1 assignment explicitly tests this and gives:

> normal division → float
> floor division → float



---

# 6. STRING × INTEGER

A very common Python MCQ trick:

```python
12 * 2
```

→ `24`

But:

```python
12 * "2"
```

→ `"222222222222"`? **No.**

More specifically, integer × string repeats the string:

```python
2 * "12"
```

→

```text
"1212"
```

Your Week 1 assignment tests exactly this kind of operation; the answer given is `121212`. 

So:

```python
"abc" * 3
```

→ `"abcabcabc"`

---

# 7. LOGICAL OPERATORS

Know:

```python
and
or
not
```

Examples:

```python
True and False   # False
True or False    # True
not True         # False
```

### Comparison operators

```python
==   equal
!=   not equal
>    greater than
<    less than
>=   greater/equal
<=   less/equal
```

### Very important

```python
=
```

means **assignment**

while

```python
==
```

means **comparison**

---

# 8. BITWISE OPERATORS

Your Week 1 assignment explicitly tests bitwise AND. 

Example:

```text
5 = 101
3 = 011
---------
    001
```

Therefore:

```python
5 & 3
```

→ `1`

Important operators:

```python
&   AND
|   OR
^   XOR
~   NOT
```

For MCQs, especially understand `&`, `|`, `^`.

---

# 9. WEEK 2 — SEQUENCE DATA TYPES

Your syllabus covers:

* String
* List
* Array
* Tuple
* Dictionary
* Set
* Range
* NumPy `ndarray`

The Week 2 assignment heavily focuses on **indexing, mutability, dictionary operations, tuple operations and NumPy indexing**. 

---

# 10. STRING

A string is a sequence of characters.

```python
s = "PYTHON"
```

Indexes start from **0**.

```text
 P  Y  T  H  O  N
 0  1  2  3  4  5
```

Therefore:

```python
s[0]   # P
s[2]   # T
```

Negative indexes:

```python
s[-1]  # N
s[-2]  # O
```

### Slicing

```python
s[1:4]
```

takes indexes:

```text
1, 2, 3
```

The ending index is **excluded**.

---

# 11. STRING METHODS

Know the common ones:

```python
upper()
lower()
strip()
replace()
split()
```

Example:

```python
"python".upper()
```

→ `PYTHON`

```python
"PYTHON".lower()
```

→ `python`

### `format()`

Your Week 2 assignment has a question on producing:

> My friend's house is in Chennai

using string formatting. 

Example:

```python
place = "Chennai"

print("My friend's house is in {}".format(place))
```

---

# 12. LIST

Example:

```python
a = [10, 20, 30]
```

Lists are:

* ordered
* indexed
* mutable
* allow duplicate values

### Common methods

```python
append()
extend()
insert()
remove()
pop()
sort()
reverse()
```

Example:

```python
a.append(40)
```

→ `[10,20,30,40]`

---

# 13. TUPLE

Example:

```python
t = (1,2,3)
```

Tuple is:

* ordered
* indexed
* **immutable**

This is one of the most important Week 2 facts.

Your assignment explicitly asks which datatype is immutable and gives **tuple** as the answer. 

Therefore:

```python
t.append(5)
```

→ error, because tuples cannot be modified.

But tuples can be combined:

```python
t1 = (1,2)
t2 = (3,4)

t3 = t1 + t2
```

→ `(1,2,3,4)`

Your assignment tests this distinction. 

---

# 14. SET

Example:

```python
s = {1,2,3}
```

A set:

* does not support normal indexing
* does not allow duplicate values
* is mutable

### HUGE MCQ POINT

Which does **not support indexing**?

```text
tuple
list
dictionary
set
```

Your assignment's answer is **set**. 

So don't write:

```python
s[0]
```

for a set.

---

# 15. DICTIONARY

Dictionary stores **key-value pairs**.

```python
d = {
    "name": "Jane",
    "age": 25
}
```

Access:

```python
d["name"]
```

→ `Jane`

Add/update:

```python
d["age"] = 26
```

Add new key:

```python
d["phone"] = "123-456"
```

### `update()`

```python
d.update({"age":26, "phone":"123-456"})
```

can update existing values and add new keys.

Your assignment explicitly tests this operation. 

### Dictionary indexing

Technically, dictionaries are accessed by **keys**, not positional indexes.

```python
d["name"]
```

not

```python
d[0]
```

unless `0` itself is a key.

---

# 16. RANGE

Example:

```python
range(5)
```

generates:

```text
0,1,2,3,4
```

End value is excluded.

```python
range(1,5)
```

→ `1,2,3,4`

```python
range(1,10,2)
```

→ `1,3,5,7,9`

Remember the pattern:

```python
range(start, stop, step)
```

---

# 17. MUTABLE vs IMMUTABLE

This is **very likely MCQ material**.

### Mutable

Can be changed after creation:

```text
list
set
dictionary
```

### Immutable

Cannot be changed:

```text
int
float
str
tuple
bool
```

For your exam, memorize especially:

> **List → mutable**
> **Tuple → immutable**

---

# 18. NUMPY

NumPy is used for numerical computing.

Import:

```python
import numpy as np
```

## ndarray

NumPy's main array structure is:

```python
np.ndarray
```

Example:

```python
arr = np.array([1,2,3])
```

### 2D array

```python
arr = np.array([
    [1,2,3],
    [4,5,6],
    [7,8,9]
])
```

Indexing starts from zero.

```python
arr[0]
```

→ first row

```text
[1 2 3]
```

```python
arr[1]
```

→

```text
[4 5 6]
```

The Week 2 assignment specifically asks:

```python
arr[0][1]
```

and identifies `[4 5 6]` when indexing the given 3D array at those positions. 

For nested arrays, **move through the dimensions one index at a time**.

---

# 19. WEEK 3 — PANDAS

Import:

```python
import pandas as pd
```

Pandas is used for **data manipulation / data wrangling**.

Your Week 1 assignment explicitly identifies **Pandas** for data wrangling and manipulation. 

---

# 20. DATAFRAME

A DataFrame is a two-dimensional tabular data structure.

Think:

```text
Rows    → observations
Columns → variables/features
```

Example:

| Name | Age | Salary |
| ---- | --: | -----: |
| A    |  20 |  30000 |
| B    |  22 |  35000 |

This is a DataFrame.

---

# 21. READING DATA

Common:

```python
pd.read_csv("file.csv")
```

Assign:

```python
df = pd.read_csv("cars.csv")
```

Then:

```python
df.head()
```

shows initial rows.

```python
df.tail()
```

shows final rows.

---

# 22. IMPORTANT PANDAS COMMANDS

Memorize these:

```python
df.head()
df.tail()
df.shape
df.info()
df.describe()
df.columns
df.dtypes
df.isnull()
df.isnull().sum()
```

### `shape`

Returns:

```text
(number_of_rows, number_of_columns)
```

### `describe()`

Gives descriptive statistics for numerical columns by default.

Your Week 3 assignment specifically asks about `df_cars.describe()` and identifies **Price** because it is the numerical column in the shown dataset. 

---

# 23. SELECTING COLUMNS

Suppose:

```python
df_cars
```

has column:

```text
Type
```

### As a Series

```python
df_cars["Type"]
```

### As a DataFrame

```python
df_cars[["Type"]]
```

Also:

```python
df_cars.loc[:, ["Type"]]
```

Your Week 3 assignment explicitly marks:

```python
df_cars[["Type"]]
df_cars.loc[:, ["Type"]]
```

as valid ways to extract the column as a separate DataFrame. 

---

# 24. `loc` vs `iloc`

Very important.

### `loc`

Uses **labels**.

```python
df.loc[:, ["Type"]]
```

### `iloc`

Uses **integer positions**.

```python
df.iloc[:, 1]
```

Think:

> **loc → label**
> **iloc → integer location**

---

# 25. MISSING VALUES

Missing values are often represented as `NaN`.

Check:

```python
df.isnull()
```

Count:

```python
df.isnull().sum()
```

### Filling missing categorical values

Your Week 3 assignment explicitly asks this and gives:

> **Mode**

as the answer. 

Remember:

| Variable    | Typical fill  |
| ----------- | ------------- |
| Numerical   | Mean / Median |
| Categorical | Mode          |

For the exam, especially remember:

> **Categorical → Mode**

---

# 26. DATA PREPROCESSING

Possible preprocessing steps:

* missing-value treatment
* conversion of data types
* encoding categorical variables
* separating features and target
* train/test splitting
* scaling/standardization where required

Your Week 3 assignment asks about converting **Review Date** based on its values, and the answer is **Review Date**. 

---

# 27. `pd.concat()`

Very important question.

Which function stacks DataFrames vertically?

```python
pd.concat()
```

Your Week 3 assignment explicitly gives `pd.concat()` as the answer. 

Think:

```text
concat → concatenate
```

---

# 28. PANDAS vs NUMPY vs MATPLOTLIB

Memorize:

| Library    | Main use                       |
| ---------- | ------------------------------ |
| NumPy      | numerical arrays/calculations  |
| Pandas     | data manipulation/dataframes   |
| Matplotlib | visualization                  |
| Seaborn    | statistical/data visualization |

Your assignment explicitly treats Pandas, Matplotlib and NumPy as Python libraries. 

---

# 29. DATA VISUALIZATION

Your syllabus specifically includes:

* Scatter plot
* Line plot
* Bar plot
* Histogram
* Box plot
* Pair plot

---

# 30. SCATTER PLOT

Used to examine the relationship between **two numerical variables**.

Typical idea:

```python
plt.scatter(x, y)
```

Example:

```text
Age vs Salary
```

Each observation becomes a point.

---

# 31. LINE PLOT

Used to display trends, especially across an ordered variable such as time.

```python
plt.plot(x, y)
```

Think:

> **Trend → line plot**

---

# 32. BAR PLOT

Used to compare categories.

Example:

```text
Toyota
Honda
Ford
```

with each manufacturer's sales.

Think:

> **Category comparison → bar plot**

---

# 33. HISTOGRAM

Used to show the **distribution of numerical data**.

It uses intervals/bins.

Think:

> **Distribution → histogram**

---

# 34. BOX PLOT

Useful for:

* median
* quartiles
* spread
* detecting outliers

Think:

> **Outliers + distribution summary → box plot**

---

# 35. PAIR PLOT

Shows pairwise relationships among multiple variables.

With Seaborn:

```python
sns.pairplot(df)
```

Very useful for visually examining relationships between several numerical variables.

---

# 36. CONTROL STRUCTURES

Your Week 3 outline includes:

* `if-else`
* `for`
* `for` with `if break`
* `while`
* functions

---

# 37. IF / ELSE

```python
if condition:
    statement
else:
    statement
```

Example:

```python
age = 20

if age >= 18:
    print("Adult")
else:
    print("Minor")
```

### Python uses indentation

Indentation is not optional formatting. It defines the block.

---

# 38. `elif`

```python
if x > 10:
    ...
elif x == 10:
    ...
else:
    ...
```

Order matters because Python evaluates the conditions in sequence.

---

# 39. FOR LOOP

```python
for i in range(5):
    print(i)
```

Output:

```text
0
1
2
3
4
```

Again:

> `range(5)` stops before 5.

---

# 40. BREAK

```python
for i in range(10):
    if i == 5:
        break
```

`break` immediately terminates the loop.

Think:

> **break → leave the loop**

---

# 41. CONTINUE

Even though your outline emphasizes `break`, know this difference:

```python
continue
```

means:

> skip current iteration and continue the loop.

So:

```text
break   → terminate loop
continue → skip iteration
```

---

# 42. WHILE LOOP

```python
while condition:
    statement
```

Runs as long as condition is `True`.

Example:

```python
i = 0

while i < 5:
    print(i)
    i += 1
```

### MCQ danger

Forgetting to update the variable can cause an infinite loop.

---

# 43. FUNCTIONS

Syntax:

```python
def function_name(parameters):
    statements
    return result
```

Example:

```python
def add(a, b):
    return a + b
```

Call:

```python
add(2,3)
```

→ `5`

Important distinction:

```python
print()
```

displays something.

```python
return
```

sends a value back from the function.

---

# 44. WEEK 4 — MACHINE LEARNING

This is especially important because your Week 4 assignment has several direct conceptual MCQs. 

Your syllabus has:

### Regression

**Predicting price of pre-owned cars**

### Classification

**Classifying personal income**

---

# 45. REGRESSION

Regression predicts a **continuous numerical value**.

Examples:

```text
car price
house price
temperature
sales
rainfall
```

Your Week 4 assignment identifies:

* house price
* maximum temperature
* ice-cream sales

as regression problems. 

### Easy rule

> **Number/value → Regression**

---

# 46. CLASSIFICATION

Classification predicts a **category/class**.

Examples:

```text
Yes / No
Pass / Fail
Spam / Not Spam
Income category
```

### Binary classification

Exactly **two classes**.

Examples:

```text
Cancer / No cancer
Win / Lose
Yes / No
```

Your assignment explicitly identifies cancer diagnosis and tournament outcome as binary classification problems. 

---

# 47. REGRESSION vs CLASSIFICATION

| Question asks for | Type           |
| ----------------- | -------------- |
| Price             | Regression     |
| Temperature       | Regression     |
| Sales             | Regression     |
| Yes/No            | Classification |
| Category          | Classification |
| Spam/Not spam     | Classification |

This distinction is extremely high-yield.

---

# 48. LINEAR REGRESSION

Simple linear regression:

$$
y = b_0 + b_1x
$$

where:

* `y` = predicted value
* `x` = input/feature
* `b0` = intercept
* `b1` = coefficient/slope

Your Week 4 assignment asks:

$$
y = 60 + 5.2x
$$

and asks how much rainfall changes when humidity increases by 30. 

Calculate:

$$
5.2 \times 30 = 156
$$

So the predicted difference is:

**156 mm**

### MCQ trick

When the question gives a change in `x`, you usually need:

$$
\Delta y = b_1 \Delta x
$$

You **do not need to calculate the intercept** for the difference.

---

# 49. MULTIPLE LINEAR REGRESSION

When there are multiple input variables:

$$
y = b_0+b_1x_1+b_2x_2+\cdots+b_nx_n
$$

Example from your Week 4 assignment:

Global Happiness Score predicted using variables such as:

* Economy
* Family
* Health
* Freedom

The assignment uses a **3:1 train/test split** and a specified `random_state`. 

---

# 50. TRAINING AND TEST DATA

Typical concept:

**Training data** → used to build/train the model.

**Test data** → used to evaluate the trained model.

Do not confuse:

```text
Training → learn
Testing → evaluate
```

---

# 51. FEATURES AND TARGET

Suppose the dataset is:

| Age | Income | Loan |
| --: | -----: | ---- |
|  25 |  30000 | Yes  |
|  40 |  60000 | No   |

Features / independent variables:

```text
Age
Income
```

Target / dependent variable:

```text
Loan
```

Remember:

> **X → features / inputs**
> **y → target / output**

Your Week 4 assignment explicitly instructs separating independent features from the dependent feature before modeling. 

---

# 52. LOGISTIC REGRESSION

Despite its name, **logistic regression is used for classification**, not ordinary continuous-value regression.

Your assignment uses logistic regression for deciding whether cars **need servicing or not**. 

### Very important MCQ

For the car-service classification problem, which is NOT appropriate?

```text
kNN
Random Forest
Logistic Regression
Linear Regression
```

Answer:

**Linear Regression**

Your Week 4 assignment explicitly gives this answer. 

---

# 53. ENCODING CATEGORICAL VARIABLES

Example:

```text
Service = Yes / No
```

can be converted into:

```text
Yes → 1
No  → 0
```

Your Week 4 assignment explicitly describes this encoding. 

### Dummy variables

Categorical variables can also be transformed into **dummy/indicator variables**.

Your Week 4 assignment asks how categorical variables are preprocessed before model building and gives:

> **Dummy variables**

as the answer. 

---

# 54. CONFUSION MATRIX

For binary classification:

|                    | Actual Positive | Actual Negative |
| ------------------ | --------------- | --------------- |
| Predicted Positive | TP              | FP              |
| Predicted Negative | FN              | TN              |

Memorize:

### TP

True Positive

Model says positive, actually positive.

### TN

True Negative

Model says negative, actually negative.

### FP

False Positive

Model says positive, actually negative.

### FN

False Negative

Model says negative, actually positive.

Your assignment's logistic-regression question specifically tests TP/TN/FP values. 

---

# 55. ACCURACY

Basic classification accuracy:

$$
Accuracy =
\frac{TP+TN}{TP+TN+FP+FN}
$$

Remember:

> **Correct predictions / Total predictions**

Your Week 4 assignment reports the test accuracy range for its logistic-regression example as **90–95%**. 

That specific numerical result belongs to the assignment's dataset/model; don't assume every logistic model will have that accuracy.

---

# 56. RMSE

Root Mean Squared Error:

$$
RMSE = \sqrt{\frac{1}{n}\sum (y_i-\hat y_i)^2}
$$

Used for regression evaluation.

Your Week 4 assignment asks for the baseline model's RMSE on the Global Happiness Index dataset and gives:

**1.06**

as the answer for that dataset/model. 

---

# 57. CORRELATION

Your Week 4 assignment also tests interpretation of a strong linear relationship. 

### Positive correlation

As X increases, Y tends to increase.

### Negative correlation

As X increases, Y tends to decrease.

### Important trap

**Correlation does not automatically mean causation.**

Two variables may have a strong relationship without one causing the other.

The assignment marks as incorrect:

* "There cannot be a negative relationship"
* "The relationship is purely causal"



---

# 58. MOST IMPORTANT MCQ TRAPS

## Trap 1 — `/` vs `//`

```python
5 / 2
```

→ `2.5`

```python
5 // 2
```

→ `2`

But with float operands:

```python
6 // 3.3
```

→ float result.

---

## Trap 2 — `=` vs `==`

```python
x = 5
```

assignment

```python
x == 5
```

comparison

---

## Trap 3 — list vs tuple

```text
List   → mutable
Tuple  → immutable
```

---

## Trap 4 — Set indexing

```python
s = {1,2,3}
s[0]
```

Not valid.

Your Week 2 assignment specifically tests this. 

---

## Trap 5 — Dictionary

Dictionary uses keys:

```python
d["name"]
```

not ordinary positional indexing.

---

## Trap 6 — `loc` vs `iloc`

```text
loc  → labels
iloc → integer positions
```

---

## Trap 7 — Mode for categorical missing data

```text
Categorical → Mode
```

Your assignment explicitly tests this. 

---

## Trap 8 — Regression vs classification

```text
Price       → Regression
Temperature → Regression
Yes/No      → Classification
Category    → Classification
```

---

## Trap 9 — Logistic regression

Despite the word "regression":

> Logistic regression → classification

---

## Trap 10 — Linear regression for a Yes/No target

Your Week 4 assignment identifies **linear regression as inappropriate** for its Yes/No car-service classification problem. 

---

# 59. RAPID-FIRE MEMORY TABLE

| Topic               | Remember                    |
| ------------------- | --------------------------- |
| Spyder              | Python IDE                  |
| `#`                 | Comment                     |
| `=`                 | Assignment                  |
| `==`                | Comparison                  |
| `/`                 | Division                    |
| `//`                | Floor division              |
| `%`                 | Remainder                   |
| `**`                | Power                       |
| `&`                 | Bitwise AND                 |
| String              | Immutable                   |
| List                | Mutable                     |
| Tuple               | Immutable                   |
| Set                 | No normal indexing          |
| Dictionary          | Key-value                   |
| `range(5)`          | 0 to 4                      |
| NumPy               | Numerical computing         |
| `ndarray`           | NumPy array                 |
| Pandas              | Data manipulation           |
| DataFrame           | 2D table                    |
| `head()`            | First rows                  |
| `tail()`            | Last rows                   |
| `shape`             | Rows, columns               |
| `describe()`        | Statistics                  |
| `loc`               | Label-based                 |
| `iloc`              | Integer-position based      |
| `pd.concat()`       | Concatenate DataFrames      |
| Categorical missing | Mode                        |
| Scatter             | Relationship of 2 variables |
| Line                | Trend                       |
| Bar                 | Category comparison         |
| Histogram           | Distribution                |
| Box plot            | Spread/outliers             |
| Pair plot           | Pairwise relationships      |
| `break`             | Exit loop                   |
| `continue`          | Skip iteration              |
| Regression          | Continuous value            |
| Classification      | Category                    |
| Logistic regression | Classification              |
| TP/TN/FP/FN         | Confusion matrix            |
| Accuracy            | Correct / Total             |
| RMSE                | Regression error            |

---

# 60. WHAT I WOULD PRIORITIZE TONIGHT

Based on the **actual assignment questions**, these deserve the most attention:

### Priority 1 — Python output questions

Practice mentally evaluating:

```python
print()
+
-
*
/
//
%
**
and
or
not
&
```

The Week 1 assignment repeatedly uses direct code/output MCQs. 

### Priority 2 — Sequence types

Know perfectly:

```text
String
List
Tuple
Set
Dictionary
Range
```

especially:

```text
indexing
slicing
mutable vs immutable
methods
```

Week 2 heavily emphasizes these.  

### Priority 3 — Pandas syntax

Be able to recognize immediately:

```python
pd.read_csv()
df.head()
df.tail()
df.shape
df.describe()
df.info()
df.isnull()
df.loc[]
df.iloc[]
pd.concat()
```

### Priority 4 — Visualization

Match chart → purpose:

```text
Scatter → relationship
Line → trend
Bar → categories
Histogram → distribution
Box → outliers/spread
Pair → many pairwise relationships
```

### Priority 5 — ML concepts

Know:

```text
Regression
Classification
Logistic Regression
Linear Regression
Features
Target
Train/Test
Encoding
Dummy Variables
Confusion Matrix
Accuracy
RMSE
Correlation
```

The Week 4 assignment concentrates heavily on these concepts.  

---

# 61. 15 QUESTIONS YOU SHOULD BE ABLE TO ANSWER INSTANTLY

**1. Which Python structure is immutable?**
→ Tuple

**2. Which does not support ordinary indexing?**
→ Set

**3. What is `5//2`?**
→ `2`

**4. What is `5/2`?**
→ `2.5`

**5. What does `&` mean?**
→ Bitwise AND

**6. Which library is primarily for DataFrames?**
→ Pandas

**7. Which library is primarily for numerical arrays?**
→ NumPy

**8. Which function vertically stacks DataFrames?**
→ `pd.concat()`

**9. How do you generally fill categorical missing values in the assignment?**
→ Mode

**10. What does `iloc` use?**
→ Integer positions

**11. Predicting car price is what kind of problem?**
→ Regression

**12. Predicting Yes/No is what kind of problem?**
→ Classification

**13. Logistic regression is generally used for?**
→ Classification

**14. What does `break` do?**
→ Terminates the loop

**15. What does correlation imply?**
→ Relationship, not necessarily causation

---

# 62. FINAL 5-MINUTE REVISION SHEET

Before entering the exam, memorize this block:

```text
Python
= assignment
== comparison
/ = normal division
// = floor division
% = remainder
** = power
& = bitwise AND

String = immutable
List = mutable
Tuple = immutable
Set = no indexing
Dictionary = key:value

range(n) = 0 to n-1

NumPy = arrays
Pandas = DataFrames
Matplotlib/Seaborn = visualization

loc = labels
iloc = integer positions

Categorical missing value → Mode
pd.concat() → combine DataFrames

Scatter → relationship
Line → trend
Bar → categories
Histogram → distribution
Box → outliers/spread
Pair plot → pairwise relationships

Regression → continuous number
Classification → category
Logistic regression → classification

X → features
y → target

TP = True Positive
TN = True Negative
FP = False Positive
FN = False Negative

Accuracy = (TP+TN)/Total

RMSE → regression error

Correlation ≠ causation
```

The uploaded assignments also show that your exam can contain **multiple-correct-option questions**, not just single-answer MCQs—for example, Week 2 and Week 4 contain questions with multiple valid choices. So read options carefully rather than assuming exactly one answer.  

**Most important strategy:** whenever you see a code-output question, don't guess from memory. Execute it mentally **line by line**, paying special attention to **type, indexing, slicing, and operator precedence**. That is the style used repeatedly across your uploaded assignments.  

