# Pandas-Cheatsheet
Handy methods for processing data with the pandas library. 

#### Search for non-numeric values
```python
column.str.extract(r'([^0-9.])',expand=False).value_counts()
```

#### Convert from one timezone aware to another.
```python
df['date'] = df['date'].dt.tz_convert('Europe/Warsaw')
```

#### Convert from naive to timezone aware.
```python
df['date'] = df['date'].dt.tz_localize('UTC')
```

#### Datetime to timestamp
```python
df['date'] = df['date'].view(int).floordiv(1e9).astype(int)
```

#### Pandas datetime format
| Code | Meaning | Sample |
|------|---------|--------|
| %y   |         |        |
| %Y   |         |        |
| %m   |         |        |
| %b   |         |        |
| %B   |         |        |
| %d   |         |        |
| %a   |         |        |
| %A   |         |        |
| %H   |         |        |
| %I   |         |        |
| %M   |         |        |
| %S   |         |        |
| %p   |         |        |
| %-d  |         |        |
| %e   |         |        |
| %c   |         |        |
| %x   |         |        |
| %X   |         |        |
| %W   |         |        |
| %U   |         |        |
| %j   |         |        |
| %z   |         |        |
| %Z   |         |        |
| %%   |         |        |
