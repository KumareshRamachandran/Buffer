# Python for Data Science — Exam Study Guide (Weeks 1–4)

This guide is built from your course outline **and** the tricky points your Week 1–4 assignments actually tested. Read top to bottom the night before; skim the "⚠️ Watch out for" boxes right before the exam.

---

## WEEK 1 — Python Basics, Variables, Data Types, Operators

### Spyder / Environment basics
- Spyder = IDE with editor + console + variable explorer panes.
- **Working directory** must be set correctly so relative file paths (e.g., `pd.read_csv('file.csv')`) work.
- Console commands: `%reset` or "remove variables" clears the environment; "clear console" just clears the display, not variables.
- Comments: `#` for single line; `'''...'''` or `"""..."""` for multi-line/docstring-style comments.

### Variable naming rules
- Must start with a **letter or underscore**, not a digit.
- Can contain letters, digits, underscore — **no other special characters** (`#`, `-`, `@`, etc.).
- Invalid special characters → **SyntaxError**.
- ✅ Valid: `variable1`, `variable_1`, `_var`
- ❌ Invalid: `1_variable` (starts with digit), `variable#` (special char)

### Data types
| Type | Example | Notes |
|---|---|---|
| `int` | `5` | whole numbers |
| `float` | `3.3` | decimals |
| `str` | `"hello"` | text, immutable |
| `bool` | `True`/`False` | subclass of int (`True==1`) |

**Type conversion:**
- `str(float(15))` → `'15.0'` → type is **str** (outermost function wins).
- A string like `"Mayur"` **cannot** be converted to float — `float("Mayur")` throws a `ValueError`. Only numeric-looking strings (e.g., `"12.5"`) convert successfully.
- `int * str` → **repeats the string** that many times: `3 * "12"` → `"121212"` (NOT an error, NOT multiplication of values).

### Arithmetic operators — ⚠️ Watch out for
- `/` → **true (float) division**, always returns float.
- `//` → **floor division** (rounds toward negative infinity, not toward zero!)
  - `-9 // 7` = **-2** (not -1). Floor division rounds *down*, and for negative results "down" means more negative.
- `%` → modulus. Follows sign of the divisor.
- Operator precedence: `%` and `*`, `/`, `//` bind **tighter than `+`/`-`**.
  - `x + y % z` → compute `y % z` first, then add `x`.
  - Example: `10 + 5 % 3` = `10 + 2` = **12**
- `j / g` (normal division) and `j // g` (floor division) on `int / float` → **both return float** (division always upgrades to float when a float is involved, and even `//` on floats gives a float result).

### Bitwise operators — ⚠️ Watch out for
- `&` = bitwise AND, `|` = bitwise OR, `^` = XOR, `~` = NOT.
- Convert to binary, then AND bit by bit.
  - `5 = 101`, `3 = 011` → AND → `001` = **1**
- Don't confuse `&`/`|` (bitwise, work on ints bit-by-bit) with `and`/`or` (logical, work on booleans).

### Libraries (recognize names & purpose)
- **NumPy** → numerical computing, arrays.
- **Pandas** → data wrangling/manipulation, dataframes.
- **Matplotlib / Seaborn** → visualization.
- **scikit-learn (sklearn)** → machine learning.
- Pandas = the answer whenever a question says "data wrangling/manipulation."

---

## WEEK 2 — Sequence Data Types & NumPy

### Core sequence types — know what supports what

| Type | Ordered? | Mutable? | Indexed? | Duplicates? | Syntax |
|---|---|---|---|---|---|
| **list** | Yes | Yes | Yes | Yes | `[1,2,3]` |
| **tuple** | Yes | **No** (immutable) | Yes | Yes | `(1,2,3)` |
| **dictionary** | Yes (insertion order) | Yes (values) | By **key**, not position | Keys unique | `{k:v}` |
| **set** | **No** | Yes | **No indexing** | **No duplicates** | `{1,2,3}` |
| **string** | Yes | **No** (immutable) | Yes | Yes | `"abc"` |
| **range** | Yes | No | Yes | — | `range(0,10)` |

⚠️ **Set does NOT support indexing** — this is a classic trick question. `s[0]` on a set → TypeError.

### Tuples — immutability rules
- Since tuples are immutable: **cannot** append, insert, remove, or modify elements → `t.append(5)` → **AttributeError**.
- **Concatenation is fine** (creates a new tuple): `t1 + t2` works.
- **Indexing into a tuple** to use as an index elsewhere works fine: `t2[t1[1]]` is valid as long as indices are in range.
- Nesting tuples is fine: `t3 = (t1, t2)` works — this creates a tuple *of* tuples, not an error.
- Converting to lists and combining also works: `(list(t1), list(t2))`.

### Dictionaries
- Access by key: `d[1]`. Accessing a **non-existent key** (like `d[0]` when only keys `1,2` exist) → **KeyError**.
- Adding a new key: `d["one"] = 1` works fine (dicts can grow).
- `d.update({...})` → adds new keys / **overwrites existing keys'** values — doesn't error even if keys already exist.
- If a value inside a dict is itself a mutable object (e.g., a list), you can mutate it in place: `d[2].append(4)` works if `d[2]` is a list.
- To update **multiple keys/add new + modify** at once, `.update()` with a multi-key dict, or a combination of direct assignment + `.update()`, both work.

### Strings
- Strings are **immutable** — like tuples, no in-place modification.
- `.format()` method: `"text {}".format(value)` — inserts `value` where `{}` is.
- ⚠️ If your **string literal itself contains an apostrophe** (e.g., "friend's"), and you also use single quotes `'...'` to define the string, Python breaks at the apostrophe → **SyntaxError**. Fix: use **double quotes** for the outer string when the content has an apostrophe, or escape it (`\'`).
- String methods: `.capitalize()` → capitalizes first letter only, lowercases rest. Looping character-by-character with `.capitalize()` capitalizes **each individual character** (since each is a 1-letter string, "capitalizing" it = uppercase that one letter).

### Loops with sequences
- `for i in range(len(s))`: iterates over **index positions** `0, 1, 2, ...len(s)-1`, NOT over the set's actual values.
  - So `l += [1+i]` for `i` in `range(4)` → appends `1,2,3,4` → **`[1,2,3,4]`**, regardless of what's actually in the set `s`.
- Iterating directly `for i in name` (a string) → `i` takes each **character** in turn.

### NumPy arrays — indexing
- `arr[0][1]` for a 3D-style nested array `[[[1,2,3],[4,5,6],[7,8,9]]]`:
  - `arr[0]` → strips outer bracket → `[[1,2,3],[4,5,6],[7,8,9]]`
  - `[0][1]` → the **second** inner list (index 1) → `[4,5,6]`
  - ⚠️ Remember indexing starts at **0**, so index `[1]` = the *second* item.
- `np.arange(0,15)` → generates `0` through `14` (15 numbers, stop value excluded).
- `.reshape(3,5)` → reshapes into 3 rows × 5 columns, **filling row-wise, values unchanged (0–14)**:
  ```
  [[ 0  1  2  3  4]
   [ 5  6  7  8  9]
   [10 11 12 13 14]]
  ```
  ⚠️ Common wrong answers shift the numbers by ±1 or drop the leading 0 — reshape does **not** change the values, only their arrangement.

---

## WEEK 3 — Pandas, EDA, Data Prep, Visualization, Control Structures

### Handling missing values
- **Categorical** variable → fill with **Mode** (most frequent category).
- **Numerical** variable → fill with **Mean** or **Median** (median is more robust to outliers).
- ⚠️ Mean/median don't make sense for categories — always **Mode** for categorical.

### DataFrame selection — `[]`, `.loc`, `.iloc`
| Method | Selects by | Example |
|---|---|---|
| `df[['col']]` | column name, double brackets → **returns a DataFrame** | `df_cars[['Type']]` ✅ |
| `df['col']` | column name, single bracket → returns a **Series** |  |
| `df.loc[:, ['col']]` | label-based | `df_cars.loc[:, ['Type']]` ✅ |
| `df.iloc[:, 1]` | position-based (integer) | `df_cars.iloc[:, [1]]` returns DataFrame; note bracket placement matters |

⚠️ `df.iloc[[:, 1]]` (bad bracket nesting) is a **syntax error** — watch bracket placement in options.

### Useful DataFrame methods
- `.describe()` → summary stats (count, mean, std, min, max, quartiles) for **numeric columns only** (e.g., "Price," not "Car name" or "Brand" which are text/categorical).
- `pd.concat()` → stacks/combines DataFrames **vertically (or horizontally with axis=1)**.
- `pd.merge()` → combines DataFrames based on **key/column values** (like SQL join) — different from concat.
- `.isnull().sum()` → count of nulls per column.
- `.dtypes` / checking data summary → reveals if a column needs **type conversion** (e.g., a numeric-looking column stored as `object`/string, such as dates, needs conversion to `datetime`).

### Libraries recap
- Pandas, NumPy, Matplotlib — all are Python libraries (a classic "all of the above" question).

### Data type quirks (`type()` on a mixed list)
- `True` → `bool` (even though bool behaves like int arithmetically, `type()` reports `bool`).
- `2` → `int`
- `3.0` → `float`
- `np.nan` → `float` (NaN is always represented as a float in NumPy/Pandas!)
- `"False"` (the **string** "False", not the boolean) → `str`
- ⚠️ Don't assume "False" as text is a boolean — quotes make it a string.

### Data Visualization (know which plot for which purpose)
| Plot | Best for |
|---|---|
| **Scatter plot** | Relationship between 2 continuous variables |
| **Line plot** | Trend over continuous/time-ordered data |
| **Bar plot** | Comparing categories |
| **Histogram** | Distribution/frequency of a single numeric variable |
| **Box plot** | Spread, median, outliers (5-number summary) |
| **Pair plot** | Pairwise relationships across multiple numeric variables at once |

### Control structures (syntax awareness)
- `if / elif / else` — conditional branching.
- `for` loop — iterate over a sequence a known/fixed number of times.
- `for` loop with `if` + `break` — exit loop early once a condition is met.
- `while` loop — repeats **while** a condition is true; used when number of iterations isn't known upfront.
- **Functions** — `def name(params):` — reusable code blocks; remember default arguments, return values.

---

## WEEK 4 — Regression & Classification (ML Case Studies)

### Regression vs. Classification — the #1 conceptual question
- **Regression** → predicting a **continuous numeric** value.
  - Examples: house price, temperature, ice-cream sales — all continuous quantities.
- **Classification** → predicting a **category/class label**.
  - **Binary classification** → exactly **2** classes (Yes/No, Win/Lose, Cancer/No Cancer).
  - **Multi-class classification** → more than 2 categories (e.g., Sports/Entertainment/Technology).
- ⚠️ "Predicting whether it will rain or not" → **classification** (Yes/No), NOT regression, even though rain sounds numeric — the *outcome asked for* is a category.

### Algorithms — appropriate use
- **kNN, Logistic Regression, Random Forest, Decision Trees** → can be used for **classification** (and some, like Random Forest/kNN, also for regression).
- **Linear Regression** → NOT appropriate for a classification problem (predicting a Yes/No category) because it predicts continuous values, not class probabilities/labels. → This is why Linear Regression was marked **wrong** for the "needs service or not" (Yes/No) problem.

### Linear regression fundamentals
- If training error = 0, **all data points lie exactly on the regression hyperplane** in (d+1)-dimensional space (d = number of features, +1 for the target axis). → **True**.
- Model equation form: `y = intercept + slope × x` (simple linear regression).
  - To find the **change in y** for a **change in x**: `Δy = slope × Δx`.
  - Example: `y = 60 + 5.2x`, humidity increases by 30 → Δy = `5.2 × 30` = **156**.
  - ⚠️ You only need the **slope** for a "difference/change" question — ignore the intercept, it cancels out.

### Correlation vs. Causation — classic trap
- Two variables can be **strongly correlated** (linearly related) **without one causing the other**.
- ❌ FALSE statements to recognize as incorrect:
  - "There cannot be a negative relationship" — **false**, correlation can be negative.
  - "The relationship is purely causal" — **false**, correlation ≠ causation.
- ✅ TRUE statements:
  - Variables can be positively or negatively correlated.
  - One variable *may or may not* cause changes in the other (correlation alone doesn't prove causation either way).

### Preprocessing categorical variables
- Convert to numeric via **encoding**: e.g., Yes/No → 1/0 (label encoding), or via **dummy variables** (one-hot encoding) for multi-category features before feeding into ML models.
- **Standardization** — scales *numeric* features (mean 0, std 1) — not the method for encoding categories.

### Model evaluation vocabulary
- **Confusion Matrix** terms:
  - **True Positive (TP)** — correctly predicted positive class.
  - **True Negative (TN)** — correctly predicted negative class.
  - **False Positive (FP)** — predicted positive, actually negative (Type I error).
  - **False Negative (FN)** — predicted negative, actually positive (Type II error).
  - Accuracy = `(TP + TN) / Total`.
- **RMSE (Root Mean Squared Error)** — measures average regression prediction error in the same units as the target; **lower = better**. Used to judge a "baseline" regression model's fit.
- **Train/test split** — always set `random_state` for reproducibility; a common split ratio is 3:1 (75%/25%) or 80/20.

---

## Quick-Fire Formula/Fact Cheat Sheet
- `//` rounds **down** (toward −∞), not toward zero.
- Order of operations: `%`, `*`, `/`, `//` before `+`, `-`.
- `int * str` = repeats the string.
- `set` → unordered, no duplicates, **no indexing**.
- `tuple`/`string` → ordered but **immutable**.
- `np.nan` → always type **float**.
- `df.describe()` → numeric columns only.
- Categorical missing values → fill with **Mode**.
- Regression = continuous output; Classification = categorical output; 2 categories = binary.
- Linear Regression ≠ suitable for classification tasks.
- Correlation ≠ Causation.
- `Δy = slope × Δx` for simple linear regression change questions.

---

### Last-minute tip
Most MCQs in your assignments test **one specific gotcha per question** (an off-by-one index, a sign/rounding rule, an immutability rule, or a "sounds numeric but is really a classification problem" trap). When reading the exam question, ask: *"what's the one rule this question is trying to catch me on?"* — that's usually the fastest way to the right answer.

Good luck tomorrow!
