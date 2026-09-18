# NPTEL Exam Guide — Python for Data Science

For an **NPTEL-style exam**, I would prepare differently from a normal college MCQ exam: focus on **concept recognition, code/output prediction, exact Python syntax, and calculation-based questions**. Your four uploaded assignment sheets are particularly useful because they show the question style and the concepts being tested.

Your assignments contain both **single-correct and multiple-correct questions**, so do not assume every question has exactly one answer. For example, Week 2 has multiple valid options in tuple/dictionary questions, and Week 4 does the same for regression/classification questions.  

---

# 1. What to prioritize for NPTEL

Based on your four assignments:

| Priority     | Topic                  | What to master                                  |
| ------------ | ---------------------- | ----------------------------------------------- |
| 🔴 Very High | Python basics          | Output prediction, operators, data types        |
| 🔴 Very High | Lists/Tuples/Sets/Dict | Indexing, mutability, methods                   |
| 🔴 Very High | NumPy                  | Array dimensions and indexing                   |
| 🔴 Very High | Pandas                 | `loc`, `iloc`, `describe`, nulls, selection     |
| 🔴 Very High | Regression/Classific.  | Identify problem type                           |
| 🔴 Very High | Logistic regression    | Classification, encoding, confusion matrix      |
| 🟠 High      | Visualization          | Identify correct graph                          |
| 🟠 High      | Control structures     | `if`, loops, `break`, functions                 |
| 🟠 High      | Data preprocessing     | Missing values, categorical encoding            |
| 🟡 Medium    | Spyder                 | Working directory, scripts, console/environment |

The assignments repeatedly test Python outputs and syntax rather than just definitions.  

---

# 2. NPTEL EXAM MINDSET

When you see a question, classify it immediately:

### Type A — Direct concept

Example:

> Which data type is immutable?

Answer: **Tuple**. 

### Type B — Output prediction

Example:

```python
a = 5
b = 3
print(a // b)
```

Calculate exactly rather than relying on intuition.

### Type C — Multiple correct

Look at **every option independently**.

Your assignments contain questions where several options are correct. 

### Type D — Numerical ML question

Example:

$$
y=60+5.2x
$$

If `x` increases by 30:

$$
\Delta y=5.2(30)=156
$$

Your Week 4 assignment uses exactly this style. 

---

# 3. WEEK 1 — ABSOLUTE MUST-KNOW

## Operators

Memorize this table:

| Operator | Meaning        |            |
| -------- | -------------- | ---------- |
| `+`      | addition       |            |
| `-`      | subtraction    |            |
| `*`      | multiplication |            |
| `/`      | division       |            |
| `//`     | floor division |            |
| `%`      | remainder      |            |
| `**`     | power          |            |
| `==`     | equality test  |            |
| `=`      | assignment     |            |
| `&`      | bitwise AND    |            |
| `        | `              | bitwise OR |
| `^`      | bitwise XOR    |            |

### Biggest traps

```python
5 / 2     # 2.5
5 // 2    # 2
5 % 2     # 1
5 ** 2    # 25
```

And:

```python
2 * "12"
```

gives:

```text
"1212"
```

because a string can be repeated by an integer. Your Week 1 assignment explicitly tests this kind of behavior. 

---

# 4. DATA TYPES

You should be able to identify these instantly:

```text
10          → int
10.5        → float
"10"        → str
True        → bool
[1,2,3]     → list
(1,2,3)     → tuple
{1,2,3}     → set
{"a":1}     → dict
```

### Conversion

```python
int("5")       # 5
float("5")     # 5.0
str(5)         # "5"
```

But:

```python
float("Mayur")
```

cannot convert the non-numeric string to a float; this exact concept appears in your Week 1 assignment. 

---

# 5. VARIABLE NAMING

### Valid

```python
name
name1
_my_name
```

### Invalid

```python
1name
my name
name#
```

Your assignment explicitly asks this. 

### Important

Python is **case-sensitive**:

```python
age
Age
AGE
```

are different variables.

---

# 6. BOOLEAN LOGIC

Memorize:

```text
True and True   → True
True and False  → False
True or False   → True
False or False  → False
not True        → False
not False       → True
```

For comparisons:

```python
5 > 3     # True
5 == 3    # False
5 != 3    # True
```

---

# 7. WEEK 2 — SEQUENCE TYPES

This is one of your highest-yield areas.

| Type       | Ordered   | Indexed   | Mutable |
| ---------- | --------- | --------- | ------- |
| String     | Yes       | Yes       | No      |
| List       | Yes       | Yes       | Yes     |
| Tuple      | Yes       | Yes       | No      |
| Set        | No        | No        | Yes     |
| Dictionary | Key-based | Key-based | Yes     |

### Memorize this sentence:

> **List = mutable, Tuple = immutable, Set = no indexing, Dictionary = key-value.**

Your Week 2 assignment directly tests these distinctions.  

---

# 8. LIST — NPTEL TRAPS

```python
a = [10,20,30]
```

### Common methods

```python
a.append(40)
a.insert(1,15)
a.remove(20)
a.pop()
a.sort()
a.reverse()
```

Remember:

```text
append → adds one item
insert  → adds at position
remove  → removes specified value
pop     → removes/returns item by position
```

---

# 9. TUPLE

```python
t = (1,2,3)
```

Cannot do:

```python
t.append(4)
```

But you can combine tuples:

```python
t1 = (1,2)
t2 = (3,4)

t3 = t1 + t2
```

→ `(1,2,3,4)`

This exact distinction is tested in your assignment. 

---

# 10. SET

```python
s = {1,2,3}
```

Key points:

* duplicates are removed
* no ordinary indexing

Thus:

```python
s[0]
```

is not valid.

This is explicitly tested in Week 2. 

---

# 11. DICTIONARY

```python
d = {"name":"Jane", "age":25}
```

Access:

```python
d["name"]
```

Modify:

```python
d["age"] = 26
```

Add:

```python
d["phone"] = "123"
```

Update multiple:

```python
d.update({"age":26, "phone":"123"})
```

Your Week 2 assignment directly tests `update()` and dictionary mutation.  

---

# 12. STRING INDEXING — VERY IMPORTANT

Given:

```python
s = "PYTHON"
```

```text
P Y T H O N
0 1 2 3 4 5
```

Therefore:

```python
s[0]    → P
s[2]    → T
s[-1]   → N
```

### Slicing

```python
s[1:4]
```

→ `YTH`

Remember:

> **Start included, stop excluded.**

This is a common NPTEL-style code question.

---

# 13. RANGE

Memorize:

```python
range(5)
```

means:

```text
0 1 2 3 4
```

Not 5.

```python
range(2,8)
```

means:

```text
2 3 4 5 6 7
```

```python
range(1,10,2)
```

means:

```text
1 3 5 7 9
```

---

# 14. NUMPY — VERY IMPORTANT

Import:

```python
import numpy as np
```

Create:

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

Then:

```python
arr[0]
```

→ `[1 2 3]`

```python
arr[1]
```

→ `[4 5 6]`

The Week 2 assignment tests nested array indexing, so carefully track one index at a time. 

---

# 15. PANDAS — EXTREMELY IMPORTANT

Import:

```python
import pandas as pd
```

Read CSV:

```python
df = pd.read_csv("cars.csv")
```

Know:

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

### What they do

| Command      | Purpose                 |
| ------------ | ----------------------- |
| `head()`     | first rows              |
| `tail()`     | last rows               |
| `shape`      | rows and columns        |
| `info()`     | structure/data types    |
| `describe()` | descriptive statistics  |
| `dtypes`     | data types              |
| `isnull()`   | identify missing values |

Your Week 3 assignment specifically tests `describe()`. 

---

# 16. `LOC` vs `ILOC`

This is a **must-memorize NPTEL question**.

### `loc`

Label-based:

```python
df.loc[:, ["Type"]]
```

### `iloc`

Position-based:

```python
df.iloc[:, 1]
```

Memorize:

> **loc = label**
> **iloc = integer position**

Your Week 3 assignment explicitly tests this distinction. 

---

# 17. DATAFRAME COLUMN SELECTION

These are different:

```python
df["Type"]
```

usually gives a **Series**.

```python
df[["Type"]]
```

gives a **DataFrame**.

Your assignment specifically tests the latter. 

This is a very good candidate for an NPTEL question.

---

# 18. MISSING VALUES

Know:

```python
df.isnull()
df.isnull().sum()
```

For a **categorical variable**, your assignment expects:

> **Mode**

For numerical variables, mean/median may be used depending on the situation, but for your exam the categorical → mode association is especially important. 

---

# 19. `PD.CONCAT()`

Question:

> Which function stacks DataFrames vertically?

Answer:

```python
pd.concat()
```

Your Week 3 assignment explicitly tests this. 

---

# 20. VISUALIZATION — MEMORIZE THE PURPOSE

Don't memorize the graph names alone. Memorize **what question each graph answers**.

| Plot      | Think                           |
| --------- | ------------------------------- |
| Scatter   | Relationship                    |
| Line      | Trend                           |
| Bar       | Categories                      |
| Histogram | Distribution                    |
| Box       | Outliers/spread                 |
| Pair plot | Multiple pairwise relationships |

### Typical question

> Which plot is appropriate to examine the relationship between price and mileage?

→ **Scatter plot**

> Which plot shows distribution of price?

→ **Histogram**

> Which plot helps identify outliers?

→ **Box plot**

---

# 21. CONTROL STRUCTURES

## `if`

```python
if x > 10:
    print("yes")
```

## `if-else`

```python
if x > 10:
    ...
else:
    ...
```

## `elif`

```python
if x > 10:
    ...
elif x == 10:
    ...
else:
    ...
```

Python uses **indentation** to define blocks.

---

# 22. FOR LOOP

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

### `break`

Terminates the loop.

```python
for i in range(10):
    if i == 5:
        break
```

### `continue`

Skips the current iteration.

Memorize:

> `break` → stop loop
> `continue` → skip iteration

---

# 23. WHILE LOOP

```python
i = 0

while i < 5:
    print(i)
    i += 1
```

A very common trap is forgetting:

```python
i += 1
```

which can create an infinite loop.

---

# 24. FUNCTIONS

Basic syntax:

```python
def add(a,b):
    return a+b
```

Then:

```python
add(2,3)
```

→ `5`

Important:

```text
print → displays
return → sends value back
```

---

# 25. WEEK 4 — MOST IMPORTANT FOR NPTEL

This section is highly conceptual.

Your assignment asks several direct questions about **regression, classification, logistic regression, preprocessing, confusion matrices, RMSE and correlation**.  

---

# 26. REGRESSION

Predict a **continuous numerical quantity**.

Examples from your assignment:

* house price
* maximum temperature
* sales
* car price
* rainfall

Your Week 4 sheet explicitly categorizes house price, maximum temperature and ice-cream sales as regression examples. 

### Shortcut

> **"How much?" → Regression**

---

# 27. CLASSIFICATION

Predict a **class/category**.

Examples:

```text
Yes / No
Cancer / No cancer
Win / Lose
Spam / Not spam
```

Your Week 4 assignment identifies cancer diagnosis and tournament outcome as binary classification problems. 

### Shortcut

> **"Which class?" → Classification**

---

# 28. BINARY CLASSIFICATION

Exactly two classes.

Examples:

```text
0 / 1
Yes / No
Pass / Fail
```

Don't confuse this with multiclass classification.

For example:

```text
Sports / Entertainment / Technology
```

has **three** classes, so it is not binary. Your assignment tests this distinction. 

---

# 29. LOGISTIC REGRESSION

This is a favorite conceptual trap.

Despite its name:

> **Logistic regression → Classification**

Your car-service problem is:

```text
Service needed?
Yes / No
```

and the assignment uses logistic regression. 

---

# 30. WHICH MODEL FOR WHICH PROBLEM?

| Problem         | Likely model type |
| --------------- | ----------------- |
| Car price       | Regression        |
| House price     | Regression        |
| Temperature     | Regression        |
| Service: Yes/No | Classification    |
| Cancer: Yes/No  | Classification    |
| Win/lose        | Classification    |

The Week 4 assignment specifically states that **linear regression is not appropriate** for the Yes/No service classification problem. 

---

# 31. FEATURES vs TARGET

Suppose:

```text
Age
Salary
Education
Income category
```

If predicting Income category:

```text
X = Age, Salary, Education
y = Income category
```

Remember:

> **X = inputs/features**
> **y = target/output**

Your Week 4 assignment explicitly asks you to separate independent features and dependent target before modelling. 

---

# 32. CATEGORICAL ENCODING

Example:

```text
Service
Yes
No
```

can become:

```text
Yes → 1
No  → 0
```

This conversion is explicitly present in your Week 4 assignment. 

Also know the term:

> **Dummy variables**

Your assignment specifically identifies dummy variables as the preprocessing approach for categorical variables before model building. 

---

# 33. CONFUSION MATRIX

Memorize this perfectly:

|                    | Actual Positive | Actual Negative |
| ------------------ | --------------- | --------------- |
| Predicted Positive | **TP**          | **FP**          |
| Predicted Negative | **FN**          | **TN**          |

### Memory trick

**T** = prediction is correct
**F** = prediction is wrong

**P/N** = predicted/actual positive or negative category.

So:

* TP → correct positive
* TN → correct negative
* FP → incorrect positive
* FN → incorrect negative

Your assignment directly asks students to identify TP, TN and FP. 

---

# 34. ACCURACY

$$
Accuracy =
\frac{TP+TN}{TP+TN+FP+FN}
$$

Think:

> **Correct predictions / all predictions**

The Week 4 assignment's specific logistic model produces an accuracy in the **90–95% range**, but that is a dataset-specific result, not a general rule. 

---

# 35. RMSE

Formula:

$$
RMSE = \sqrt{\frac{1}{n}\sum (y-\hat y)^2}
$$

Remember:

> RMSE is an **error metric for regression**.

Your assignment asks for RMSE and gives **1.06** for its particular Global Happiness Index baseline model. 

---

# 36. LINEAR REGRESSION CALCULATIONS

Suppose:

$$
y=60+5.2x
$$

and `x` increases by 30.

Don't calculate two full equations.

Just calculate:

$$
\Delta y = 5.2\times30
$$

$$
=156
$$

The assignment explicitly uses this calculation. 

---

# 37. CORRELATION

Very important conceptual distinction:

> **Correlation ≠ causation**

Strong positive correlation means the two variables tend to increase together.

Strong negative correlation means one tends to increase while the other tends to decrease.

Your assignment explicitly identifies statements claiming that there cannot be a negative relationship and that a strong relationship is necessarily causal as incorrect. 

---

# 38. NPTEL-STYLE TRAPS TO WATCH FOR

### Trap 1

```python
5/2
```

→ `2.5`, not `2`.

### Trap 2

```python
5//2
```

→ `2`.

### Trap 3

```python
[1,2,3][0]
```

→ `1`.

### Trap 4

```python
(1,2,3)[0]
```

→ `1`.

### Trap 5

```python
{1,2,3}[0]
```

→ invalid because set doesn't support indexing.

### Trap 6

```python
df["Type"]
```

→ Series

while:

```python
df[["Type"]]
```

→ DataFrame.

### Trap 7

```text
loc  → labels
iloc → integer positions
```

### Trap 8

```text
Categorical missing → Mode
```

### Trap 9

```text
Price → Regression
Yes/No → Classification
```

### Trap 10

```text
Logistic regression → Classification
```

---

# 39. 25 QUESTIONS TO PRACTICE RIGHT NOW

Try answering these **without looking at the answers**.

### Python

**1. What is the output?**

```python
print(5//2)
```

**2. What is the output?**

```python
print(5%2)
```

**3. What is the output?**

```python
print("Hi"*3)
```

**4. What is the type of `5.0`?**

**5. Which is invalid?**

```text
a. value1
b. _value
c. 1value
d. value_1
```

---

### Sequence types

**6. Which is immutable?**

```text
a. list
b. tuple
c. set
d. dictionary
```

**7. Which does not support ordinary indexing?**

```text
a. list
b. tuple
c. set
d. string
```

**8. What does `range(4)` generate?**

**9. What is `["A","B","C"][1]`?**

**10. What is `"PYTHON"[-1]`?**

---

### NumPy/Pandas

**11. Which library is used for DataFrames?**

**12. What does `df.shape` return?**

**13. `loc` uses what?**

**14. `iloc` uses what?**

**15. Which function combines DataFrames?**

**16. Which statistic is commonly used for missing categorical values in your assignment?**

---

### Visualization

**17. Best plot for relationship between two numerical variables?**

**18. Best plot for distribution?**

**19. Best plot for outliers?**

**20. Best plot for category comparison?**

---

### Machine Learning

**21. Predicting car price = ?**

**22. Predicting Yes/No = ?**

**23. Logistic regression is used primarily for?**

**24. What does TP mean?**

**25. Does correlation automatically imply causation?**

---

# 40. ANSWERS

1. `2`
2. `1`
3. `"HiHiHi"`
4. `float`
5. `1value`
6. `tuple`
7. `set`
8. `0,1,2,3`
9. `B`
10. `N`
11. Pandas
12. `(rows, columns)`
13. Labels
14. Integer positions
15. `pd.concat()`
16. Mode
17. Scatter plot
18. Histogram
19. Box plot
20. Bar plot
21. Regression
22. Classification
23. Classification
24. True Positive
25. No

These answers align with the concepts repeatedly tested in your uploaded assignments.    

---

# 41. YOUR LAST-NIGHT REVISION ORDER

Do **not** spend equal time on every topic.

### First — 45 minutes

**Python code/output**

Study:

```text
data types
operators
strings
lists
tuples
sets
dictionaries
range
indexing
slicing
```

### Second — 35 minutes

**NumPy + Pandas**

Memorize:

```text
np.array
ndarray
head
tail
shape
describe
isnull
loc
iloc
concat
```

### Third — 20 minutes

**Visualization**

Just memorize:

```text
Scatter → relationship
Line → trend
Bar → category
Histogram → distribution
Box → outliers
Pair plot → pairwise
```

### Fourth — 35 minutes

**Machine Learning**

Memorize:

```text
Regression
Classification
Logistic regression
Features
Target
Train/Test
Encoding
Dummy variables
Confusion matrix
Accuracy
RMSE
Correlation
```

### Final 15 minutes

Read only the **trap list** above.

---

## The 10 facts I would absolutely memorize before sleeping

> **1.** `/` → normal division
> **2.** `//` → floor division
> **3.** List → mutable
> **4.** Tuple → immutable
> **5.** Set → no indexing
> **6.** `loc` → labels; `iloc` → integer positions
> **7.** Categorical missing → Mode
> **8.** Price → Regression; Yes/No → Classification
> **9.** Logistic Regression → Classification
> **10.** Correlation ≠ Causation

These ten alone cover a surprisingly large portion of the conceptual traps visible in your assignment material.   

I can also turn your **four assignments into a 50-question NPTEL-style mock test with answers and explanations**, matching the difficulty and question patterns shown in the PDFs.

