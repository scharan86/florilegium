---
tags:
  - cs/lang/python
created: 2026-03-18
status: draft
type: concept
---
---

>[!Definition]
Pandas reduction methods aggregate along an axis. The result typically has one fewer dimension.

| Method                              | Description                                                                  | Example                                 |
| ----------------------------------- | ---------------------------------------------------------------------------- | --------------------------------------- |
| `df.sum(axis=0, skipna=True)`       | Sum per column (axis=0) or row (axis=1); NaN skipped by default              | `df.sum()` → one sum per column         |
| `df.mean(axis=0, skipna=True)`      | Arithmetic mean                                                              | `df.mean(axis=1)` → mean per row        |
| `df.cumsum(axis=0)`                 | Cumulative sum                                                               | `df.cumsum()`                           |
| `df.cumprod(axis=0)`                | Cumulative product                                                           | `df.cumprod()`                          |
| `df.describe()`                     | Summary stats for all numeric columns: count, mean, std, min, quartiles, max | `df.describe()`                         |
| `df.count()`                        | Number of non-NaN values                                                     | `df.count()` → per column               |
| `df.min(axis=0)` / `df.max(axis=0)` | Minimum / maximum                                                            | `df.min(axis=1)` → min per row          |
| `df.argmin()` / `df.argmax()`       | Integer position of min / max                                                | `df.argmax()`                           |
| `df.idxmin()` / `df.idxmax()`       | **Label** of the min / max element — more useful than argmin                 | `df.idxmax()` → label of max per column |
| `df.median()`                       | 50th percentile                                                              | `df.median()`                           |
| `df.var(ddof=1)`                    | Variance — ddof=1 by default in Pandas (sample variance)                     | `df.var()`                              |
| `df.std(ddof=1)`                    | Standard deviation — ddof=1 default                                          | `df.std()`                              |
| `df.skew()`                         | Third moment — skewness                                                      | `df.skew()`                             |
| `df.kurt()`                         | Fourth moment — kurtosis                                                     | `df.kurt()`                             |
| `df.quantile(q=0.5)`                | Sample quantile at probability q                                             | `df.quantile(0.25)` → first quartile    |
| `df.diff(periods=1)`                | First discrete difference                                                    | `df.diff()`                             |
| `df.pct_change(periods=1)`          | Percent change between elements                                              | `df.pct_change()`                       |

python

```python
df = pd.DataFrame([[1.4, np.nan],
                   [7.1, -4.5],
                   [np.nan, np.nan],
                   [0.75, -1.3]],
                  index=['a','b','c','d'],
                  columns=['one','two'])

df.sum()                          # NaN skipped by default
df.sum(axis=1)                    # sum per row
df.mean(axis=1, skipna=False)     # NaN propagates when skipna=False
df.idxmax()                       # label of max value per column
df.describe()                     # full numeric summary
```

---

## Correlation and Covariance

|Method|Description|Example|
|---|---|---|
|`s1.corr(s2)`|Pearson correlation between two Series (aligned by index)|`returns['MSFT'].corr(returns['IBM'])`|
|`s1.cov(s2)`|Covariance between two Series|`returns['MSFT'].cov(returns['IBM'])`|
|`df.corr()`|Pairwise correlation of all columns → square DataFrame|`returns.corr()`|
|`df.cov()`|Pairwise covariance of all columns → square DataFrame|`returns.cov()`|
|`df.corrwith(s)`|Correlation of each column with a Series|`returns.corrwith(returns['IBM'])`|
|`df.corrwith(other_df)`|Pairwise column correlations between two DataFrames|`returns.corrwith(volume)`|

---

## Unique Values, Value Counts, and Membership

|Method|Description|Example|
|---|---|---|
|`s.unique()`|Array of unique values in order of first appearance|`obj.unique()` → `array(['c','a','d','b'])`|
|`s.value_counts(normalize=False, sort=True)`|Frequency of each unique value, sorted descending by default|`obj.value_counts()` → `a 3, c 2, ...`|
|`s.isin(values)`|Boolean Series — is each element in the given list?|`obj.isin(['b','c'])` → `[F,T,T,F,...]`|
|`pd.value_counts(arr)`|Standalone function — same as above|`pd.value_counts(arr, sort=False)`|

python

```python
obj = pd.Series(['c','a','d','a','a','b','b','c','c'])
obj.unique()         # array(['c', 'a', 'd', 'b'])
obj.value_counts()
# a    3
# c    3
# b    2
# d    1

mask = obj.isin(['b', 'c'])
obj[mask]            # only 'b' and 'c' values
```

