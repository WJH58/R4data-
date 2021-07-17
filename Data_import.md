## Data import

1. read_csv(): comma separated table.   
   read_csv2(): semicolon(;) separated table.  
   read_tsv(): tab delimited table.  
   read_delim(): files with **any delimiter** # You need to specify the delimiter.

2. By default, read_xxx() treat the first row as colnames. You can set ```col_names = F``` to prevent that. Or, you can pass a string variable to name columns:
```
read_csv("1,2,3\n4,5,6", col_names = c("x", "y", "z"))
```

3. ```\n``` means adding a new line.
```
read_csv("1,2,3\n4,5,6", col_names = FALSE)
```

4. parse_xxx() functions: 提取出logical, integer, double, number, character, date, time等等，记得加引号！
```
parse_double("1.23")
parse_number("$1")
parse_date("2020-09-07")
```
locale = locale(...) 此处...可为：
* decimal_mark = "," # 荷兰人的小数点表示法
* grouping_mark = “,” # 大数字每三位会有一个grouping mark，一般就是逗号，不需要再specify

**Note:** How to ignore "%" in "20%"?  
```
parse_number(20%)
```

How to extract the number in a sentence?  
```
parse_number("It costs $20.")
```

5. You can even extract date & time from a number string.
e.g.  
```
parse_datetime("20201010T2020")
"2020-10-10 20:00:00 UTC"

parse_date("20201010")
"2020-10-10" # no UTC.

parse_date("January 1, 2010", "%B %d, %Y")
"2010-01-01"
```

**Year**  
%Y (4 digits).  
%y (2 digits); 00-69 -> 2000-2069, 70-99 -> 1970-1999.  
**Month**  
%m (2 digits).  
%b (abbreviated name, like “Jan”).  
%B (full name, “January”).  
**Day**  
%d (2 digits).  
%e (optional leading space).  
**Time**  
%H 0-23 hour.  
%I 0-12, must be used with %p.  
%p AM/PM indicator.  
%M minutes.  
%S integer seconds.  
%OS real seconds.  
%Z Time zone (as name, e.g. America/Chicago). Beware of abbreviations: if you’re American, note that “EST” is a Canadian time zone that does not have daylight savings time. It is not Eastern Standard Time! We’ll come back to this time zones.  
%z (as offset from UTC, e.g. +0800).  
**non-digits**  
%. skips one non-digit character.
%* skips any number of non-digits.
