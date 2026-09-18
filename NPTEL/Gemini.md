# Comprehensive MCQ Exam Preparation Guide
## Python for Data Science & Applied Statistics

---

## Module 1: Python Spyder Basics, Environment & Syntax Rules

### 1. Spyder IDE Mechanics
* **Working Directory**: Always set the correct directory in Spyder before loading external scripts or datasets (`.csv`, `.pdf`).
* **Console Operations**:
  * Clear console screen: `cls` or `CTRL + L`.
  * Clear environment variables: `remove` commands or clicking the broom icon in the Variable Explorer.
* **Script Commenting**: Single-line comments start with `#`. Multi-line blocks can be enclosed in triple quotes (`'''` or `"""`).

---

### 2. Variable Creation & Identifiers
* **Rules for Valid Variable Names**:
  1. Must begin with a letter (`a-z`, `A-Z`) or an underscore (`_`).
  2. Can contain letters, digits (`0-9`), and underscores.
  3. **Forbidden**: Starting with a digit (e.g., `1 variable`), spaces (e.g., `variable 1`), and special characters/symbols (`#`, `!`, `@`, `$`, `%`, `.`).
* **Common MCQ Trap**:
  * `ram_2` and `variable1` are **VALID**.
  * `m.n.q = 3500, 3600, 3700` is **INVALID** because periods (`.`) are reserved for attribute and method access in Python. Using periods in variable names throws a **`SyntaxError`**.

---

### 3. Arithmetic Operators, Logical Logic & Precedence
* **Floor Division (`//`)**: Returns the integer quotient rounded down towards negative infinity.
  * *Example*: `-9 // 7` evaluates to `-2` (since $-9 / 7 = -1.2857$, rounding down gives $-2$).
* **Modulo (`%`)**: Returns the remainder of division.
  * *Formula*: `X %= Y` is equivalent to `X = X % Y`.
  * *Example*: `X = 300`, `Y = 17`. `300 % 17`: $17 \times 17 = 289$. Remainder is $300 - 289 = \mathbf{11}$.
* **Operator Precedence**: Modulo (`%`) and multiplication/division (`*`, `/`) have higher precedence than addition (`+`) and subtraction (`-`).
  * *Example*: `x = 10`, `y = 5`, `z = 3`. `ans = x + y % z`.
  * First, evaluate `5 % 3 = 2`. Then `10 + 2 = 12`.
* **String Repetition (`*`)**: Multiplying an integer by a string repeats the string text.
  * *Example*: `a = 3`, `b = "12"`. `print(a * b)` outputs `"121212"`.

---

### 4. Data Type Conversions & Casting
* **Casting Chain**: `x = 15`; `y = str(float(x))`.
  * `float(15)` $\rightarrow$ `15.0`
  * `str(15.0)` $\rightarrow$ `'15.0'` (type is **`str`**).
* **Non-Numeric Strings**: Converting a non-numeric string to a float (e.g., `float("Mayur")`) is impossible and raises a `ValueError`.

---

## Module 2: Sequence Data Types & Data Structures

### 1. Overview of Python Sequences & Mutability
| Data Type | Mutable / Immutable | Key Characteristics |
| :--- | :--- | :--- |
| **Tuple** (`tuple`) | **Immutable** | Ordered collection; elements cannot be modified, added, or deleted after creation. |
| **List** (`list`) | **Mutable** | Ordered collection; supports index replacement, appending, inserting, and deleting. |
| **Set** (`set`) | **Mutable** | Unordered collection of unique items; no duplicates allowed. |
| **Dictionary** (`dict`) | **Mutable** | Key-value mapping; keys must be immutable (hashable), values can be anything. |

---

### 2. Essential String & List Methods
* **`.title()` Method**: Capitalizes the first letter of each word while converting all remaining letters to lowercase.
  * *Example*: `'gOOd moRning'.title()` outputs `'Good Morning'`.
* **`.insert(index, element)` Method**: Places an item at a specific zero-based index.
  * *Example*: `Stationery = [Product, Price, Brand]`. Adding `'Notebook'` to the front of `Product` list: `Stationery[0].insert(0, 'Notebook')`.
* **`.index('item')` Method**: Returns the zero-based index of the **first occurrence** of the element.
  * *Example*: `Mylist = ['a', 'a', 'b', 'b', 'b', 'c', 'c', 'd', 'e']`. `Mylist.index('d')` returns **`7`**.

---

### 3. Set Operations
* **Emptying a Set**: `set.clear()` removes **all** elements from a set at once.
* **Removing Individual Items**: `set.remove(item)` (raises KeyError if absent) or `set.discard(item)` (does not raise error if absent).

---

### 4. Tuples & Dictionary Operations
* **Valid Tuple Operations**:
  * Concatenation: `t3 = t1 + t2`
  * Nesting: `t3 = (t1, t2)`
  * Indexing nested elements: `x = t2[t1[1]]`
  * Conversion: `t3 = (list(t1), list(t2))`
  * *Invalid*: `t1.append(5)` (raises `AttributeError` because tuples are immutable).
* **Valid Dictionary Operations**:
  * Mutating an inner list: `d[2].append(4)`
  * Key assignment: `d["one"] = 1`
  * Update method: `d.update({'one': 2, 'age': 26})`

---

## Module 3: Array Operations & Numerical Computing with NumPy

### 1. `ndarray` Creation & Reshaping
* **`np.arange(start, stop)`**: Generates an array of evenly spaced values from `start` up to (but excluding) `stop`.
  * `np.arange(0, 15)` generates 15 integers: `[0, 1, 2, ..., 14]`.
* **`.reshape(rows, cols)`**: Changes array dimensions without altering data.
  * `np.array(np.arange(0, 15)).reshape(3, 5)` creates a 2D array with 3 rows and 5 columns:
    ```python
    [[ 0,  1,  2,  3,  4],
     [ 5,  6,  7,  8,  9],
     [10, 11, 12, 13, 14]]
    ```

---

## Module 4: Data Wrangling & Analysis with Pandas

### 1. Categorical Missing Value Imputation
* Categorical missing values should be filled using the **Mode** (most frequent value). Numerical missing values typically use **Mean** (if symmetric) or **Median** (if skewed).

---

### 2. Column Extraction: Series vs. DataFrame
* **Extract as Series**: `df['Type']`
* **Extract as DataFrame**: `df[['Type']]` or `df.loc[:, ['Type']]` (double square brackets preserve DataFrame structure).

---

### 3. Summary Statistics & Concatenation
* **`df.describe()`**: Automatically computes summary statistics (count, mean, std, min, 25%, 50%, 75%, max) **only for numerical columns** (e.g., `Price`). It skips string/categorical columns like `Car name` or `Brand`.
* **`pd.concat()`**: Used to stack DataFrames vertically (row-wise) or horizontally (column-wise with `axis=1`).

---

## Module 5: Fundamental Statistics & Probability Concepts

### 1. Weighted Arithmetic Mean
$$\bar{X} = \frac{(N_1 \times M_1) + (N_2 \times M_2)}{N_1 + N_2}$$
* *Problem*: Location 1 has $N_1 = 663$ employees at $M_1 = \$13,454$. Location 2 has $N_2 = 504$ employees at $M_2 = \$17,591$.
* *Calculation*:
  $$\text{Total Salary} = (663 \times 13454) + (504 \times 17591) = 8,919,982 + 8,865,864 = 17,785,846$$
  $$\text{Total Employees} = 663 + 504 = 1,167$$
  $$\bar{X} = \frac{17,785,846}{1,167} \approx \mathbf{\$15,240.67}$$

---

### 2. Basic Probability & Compound Events
* *Problem*: Drawing 'A' or 'I' from "STATISTICS AND PROBABILITY" (24 letters).
  * Letter counts: 3 'A's, 4 'I's $\rightarrow$ Total favorable outcomes = $3 + 4 = 7$.
  * $P(\text{'A' or 'I'}) = \mathbf{\frac{7}{24}}$.

---

### 3. Expected Value of Discrete Random Variable
* Formula:
  $$E(X) = \sum_{i=1}^{n} p_i x_i$$
  (Sum of each possible outcome $x_i$ multiplied by its probability $p_i$).

---

### 4. Frequency Distributions & Graphs
* **Histogram**: The standard chart used to plot frequency distributions for **continuous numerical data** (e.g., customer waiting times in minutes).

---

### 5. Joint Probability & Boxplots
* **Joint Probability**: Probability of two independent events occurring simultaneously: $P(A \cap B)$.
* **Boxplot Interpretation**: The horizontal line inside the box represents the **Median** ($Q_2 / 50\text{th percentile}$).

---

## Module 6: Applied Machine Learning & Predictive Modeling

### 1. Classification vs. Regression Tasks
* **Regression**: Target variable is continuous numerical (e.g., Global Happiness Score, rainfall amount in mm, car price).
* **Classification**: Target variable is discrete categorical (e.g., Service requirement: Yes/No, customer churn).

---

### 2. Scikit-Learn Essential Functions
* **Train-Test Split**: `sklearn.model_selection.train_test_split()`
* **KNN Classifier**: `sklearn.neighbors.KNeighborsClassifier()`

---

### 3. Preprocessing & Dummy Variables
* Categorical features must be encoded before fitting regression/classification models using **Dummy Variables** (One-Hot Encoding) or Label Encoding.

---

### 4. Linear Regression Predictions & Interpretation
* *Function*: $y = 60 + 5.2x$ (where $x = \text{humidity}$, $y = \text{rainfall}$).
* *Scenario*: Humidity increases by 30 units ($\Delta x = 30$).
* *Predicted Change*: $\Delta y = 5.2 \times 30 = \mathbf{156\text{ mm}}$.

---

### 5. Correlation vs. Causation & Diagnostic Rules
* Strong linear correlation **does NOT** imply a direct causal relationship. Correlation can be positive or negative.
* **$R^2$ (Coefficient of Determination)**: An $R^2 = 1.0$ represents a perfect linear fit.
* **Heteroscedasticity**: Refers to non-constant variance in linear regression residuals/errors. Standard linear regression assumes homoscedasticity (constant variance).
