---
{"dg-publish":true,"permalink":"/020-programming/python-functions-basics/","created":"2025-03-06T13:53:52.000-05:00","updated":"2025-03-09T22:34:40.000-04:00"}
---


---

## Functions Overview

1. `value_counts()`
2. `sort_values()`
3. `groupby()`
4. `agg()`
5. `pivot_table()`
6. `set_index()`
7. `loc[]`
8. `sort_index()`

## Detailed Breakdown

### 1. `value_counts()`

```python
df['column_name'].value_counts(normalize=True, sort=True)
```

**Key points:**

- Used on a Series, not a DataFrame
- `normalize=True` gives proportions instead of counts
- `sort=True` is default, sorts by frequency descending

**Common mistakes:**

- Trying to use on entire DataFrame instead of a single column
- Forgetting that it returns a Series, not a DataFrame


### 2. `sort_values()`

```python
df.sort_values(by='column_name', ascending=False)
```

**Key points:**

- Can sort by multiple columns using a list: `by=['col1', 'col2']`
- `ascending=False` for descending order
- Returns a new DataFrame unless `inplace=True`

**Common mistakes:**

- Forgetting to assign the result to a variable if not using `inplace=True`
- Using wrong column names


### 3. `groupby()`

```python
df.groupby('column_name')['value_column'].operation()
```

**Key points:**

- Groups data by one or more columns
- Often followed by an aggregation function
- Can group by multiple columns: `groupby(['col1', 'col2'])`

**Common mistakes:**

- Forgetting to specify which column to perform operations on after grouping
- Not chaining an aggregation method after `groupby()`


### 4. `agg()`

```python
df.groupby('column_name').agg({'col1': 'mean', 'col2': 'sum'})
```

**Key points:**

- Can apply multiple functions to different columns
- Works well with `groupby()`
- Can use custom functions or numpy functions

**Common mistakes:**

- Incorrect syntax when specifying multiple functions
- Forgetting to import numpy if using numpy functions


### 5. `pivot_table()`

```python
pd.pivot_table(df, values='value_col', index='index_col', columns='column_col', aggfunc='mean', fill_value=0)
```

**Key points:**

- Creates a spreadsheet-style pivot table
- `aggfunc` defaults to mean if not specified
- Can use multiple columns for index or columns

**Common mistakes:**

- Confusing the roles of index, columns, and values parameters
- Forgetting to specify `aggfunc` when you want something other than mean


### 6. `set_index()`

```python
df.set_index(['col1', 'col2'])
```

**Key points:**

- Creates a new index for the DataFrame
- Can create a MultiIndex by passing a list of column names
- Returns a new DataFrame unless `inplace=True`

**Common mistakes:**

- Forgetting to assign the result to a variable if not using `inplace=True`
- Not realizing that the columns used for the index are removed from the DataFrame body


### 7. `loc[]`

```python
df.loc[row_indexer, column_indexer]
```

**Key points:**

- Uses labels/index values for selection
- Can select both rows and columns
- For slicing on MultiIndex, use tuples: `df.loc[('country', 'city'):, :]`

**Common mistakes:**

- Using integer positions instead of labels (that's what `iloc[]` is for)
- Incorrect syntax for MultiIndex slicing
- Forgetting the comma when selecting all rows or all columns (e.g., `df.loc[:, 'column']`)


### 8. `sort_index()`

```python
df.sort_index(level=['col1', 'col2'], ascending=[True, False])
```

**Key points:**

- Sorts the DataFrame by the index
- For MultiIndex, use `level` parameter to specify which levels to sort by
- Can sort different levels in different directions using `ascending` parameter

**Common mistakes:**

- Confusing `sort_index()` with `sort_values()`
- Incorrect syntax for sorting multiple levels of a MultiIndex
- Forgetting that it returns a new DataFrame unless `inplace=True`

Remember, practice makes perfect! Keep working with these functions, and soon they'll become second nature. Happy coding!

