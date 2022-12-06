# Pandas-Cheatsheet
Useful methods and information for processing data with the pandas library. 

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

## List of time zones 
[Wikipedia](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones)

#### Pandas datetime format
| Code | Meaning                                                                                                                                                                          | Sample                                                                       |
|:----:|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------|
| %a   | Weekday as locale’s abbreviated name.                                                                                                                                            | Sun, Mon, …, Sat (en_US); So, Mo, …, Sa (de_DE)                              |
| %A   | Weekday as locale’s full name.                                                                                                                                                   | Sunday, Monday, …, Saturday (en_US); Sonntag, Montag, …, Samstag (de_DE)     |
| %w   | Weekday as a decimal number, where 0 is Sunday and 6 is Saturday.                                                                                                                | 0, 1, …, 6                                                                   |
| %d   | Day of the month as a zero-padded decimal number.                                                                                                                                | 01, 02, …, 31                                                                |
| %b   | Month as locale’s abbreviated name.                                                                                                                                              | Jan, Feb, …, Dec (en_US); Jan, Feb, …, Dez (de_DE)                           |
| %B   | Month as locale’s full name.                                                                                                                                                     | January, February, …, December (en_US); Januar, Februar, …, Dezember (de_DE) |
| %m   | Month as a zero-padded decimal number.                                                                                                                                           | 01, 02, …, 12                                                                |
| %y   | Year without century as a zero-padded decimal number.                                                                                                                            | 00, 01, …, 99                                                                |
| %Y   | Year with century as a decimal number.                                                                                                                                           | 0001, 0002, …, 2013, 2014, …, 9998, 9999                                     |
| %H   | Hour (24-hour clock) as a zero-padded decimal number.                                                                                                                            | 00, 01, …, 23                                                                |
| %I   | Hour (12-hour clock) as a zero-padded decimal number.                                                                                                                            | 01, 02, …, 12                                                                |
| %p   | Locale’s equivalent of either AM or PM.                                                                                                                                          | AM, PM (en_US); am, pm (de_DE)                                               |
| %M   | Minute as a zero-padded decimal number.                                                                                                                                          | 00, 01, …, 59                                                                |
| %S   | Second as a zero-padded decimal number.                                                                                                                                          | 00, 01, …, 59                                                                |
| %f   | Microsecond as a decimal number, zero-padded to 6 digits.                                                                                                                        | 000000, 000001, …, 999999                                                    |
| %z   | UTC offset in the form ±HHMM[SS[.ffffff]] (empty string if the object is naive).                                                                                                 | (empty), +0000, -0400, +1030, +063415, -030712.345216                        |
| %Z   | Time zone name (empty string if the object is naive).                                                                                                                            | (empty), UTC, GMT                                                            |
| %j   | Day of the year as a zero-padded decimal number.                                                                                                                                 | 001, 002, …, 366                                                             |
| %U   | Week number of the year (Sunday as the first day of the week) as a zero-padded decimal number. All days in a new year preceding the first Sunday are considered to be in week 0. | 00, 01, …, 53                                                                |
| %W   | Week number of the year (Monday as the first day of the week) as a zero-padded decimal number. All days in a new year preceding the first Monday are considered to be in week 0. | 00, 01, …, 53                                                                |
| %c   | Locale’s appropriate date and time representation.                                                                                                                               | Tue Aug 16 21:30:00 1988 (en_US); Di 16 Aug 21:30:00 1988 (de_DE)            |
| %x   | Locale’s appropriate date representation.                                                                                                                                        | 08/16/88 (None); 08/16/1988 (en_US); 16.08.1988 (de_DE)                      |
| %X   | Locale’s appropriate time representation.                                                                                                                                        | 21:30:00 (en_US); 21:30:00 (de_DE)                                           |
| %%   | A literal '%' character.                                                                                                                                                         | %                                                                            |
|      |                                                                                                                                                                                  |                                                                              |
| %G   | ISO 8601 year with century representing the year that contains the greater part of the ISO week (%V).                                                                            | 0001, 0002, …, 2013, 2014, …, 9998, 9999                                     |
| %u   | ISO 8601 weekday as a decimal number where 1 is Monday.                                                                                                                          | 1, 2, …, 7                                                                   |
| %V   | ISO 8601 week as a decimal number with Monday as the first day of the week. Week 01 is the week containing Jan 4.                                                                | 01, 02, …, 53                                                                |

#### Pandas offset aliases

| Date Offset                              | Frequency String | Description                                           |
|------------------------------------------|------------------|-------------------------------------------------------|
| DateOffset                               | None             | Generic offset class, defaults to absolute 24 hours   |
| BDay or BusinessDay                      | 'B'              | business day (weekday)                                |
| CDay or CustomBusinessDay                | 'C'              | custom business day                                   |
| Week                                     | 'W'              | one week, optionally anchored on a day of the week    |
| WeekOfMonth                              | 'WOM'            | the x-th day of the y-th week of each month           |
| LastWeekOfMonth                          | 'LWOM'           | the x-th day of the last week of each month           |
| MonthEnd                                 | 'M'              | calendar month end                                    |
| MonthBegin                               | 'MS'             | calendar month begin                                  |
| BMonthEnd or BusinessMonthEnd            | 'BM'             | business month end                                    |
| BMonthBegin or BusinessMonthBegin        | 'BMS'            | business month begin                                  |
| CBMonthEnd or CustomBusinessMonthEnd     | 'CBM'            | custom business month end                             |
| CBMonthBegin or CustomBusinessMonthBegin | 'CBMS'           | custom business month begin                           |
| SemiMonthEnd                             | 'SM'             | 15th (or other day_of_month) and calendar month end   |
| SemiMonthBegin                           | 'SMS'            | 15th (or other day_of_month) and calendar month begin |
| QuarterEnd                               | 'Q'              | calendar quarter end                                  |
| QuarterBegin                             | 'QS'             | calendar quarter begin                                |
| BQuarterEnd                              | 'BQ              | business quarter end                                  |
| BQuarterBegin                            | 'BQS'            | business quarter begin                                |
| FY5253Quarter                            | 'REQ'            | retail (aka 52-53 week) quarter                       |
| YearEnd                                  | 'A'              | calendar year end                                     |
| YearBegin                                | 'AS' or 'BYS'    | calendar year begin                                   |
| BYearEnd                                 | 'BA'             | business year end                                     |
| BYearBegin                               | 'BAS'            | business year begin                                   |
| FY5253                                   | 'RE'             | retail (aka 52-53 week) year                          |
| Easter                                   | None             | Easter holiday                                        |
| BusinessHour                             | 'BH'             | business hour                                         |
| CustomBusinessHour                       | 'CBH'            | custom business hour                                  |
| Day                                      | 'D'              | one absolute day                                      |
| Hour                                     | 'H'              | one hour                                              |
| Minute                                   | 'T' or 'min'     | one minute                                            |
| Second                                   | 'S'              | one second                                            |
| Milli                                    | 'L' or 'ms'      | one millisecond                                       |
| Micro                                    | 'U' or 'us'      | one microsecond                                       |
| Nano                                     | 'N'              | one nanosecond                                        |
