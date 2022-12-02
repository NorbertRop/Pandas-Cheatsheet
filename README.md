# Pandas-Cheatsheet
Handy methods for processing data with the pandas library. 

#### Search for non-numeric values
```python
column.str.extract(r'([^0-9.])',expand=False).value_counts()
```

#### Datetime to timestamp
```python
df['date'] = df['date'].view(int).floordiv(1e9).astype(int)
```
