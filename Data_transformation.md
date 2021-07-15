## Data transformation

1. R cannot return an infinite number.
```
sqrt(2) ^ 2 == 2
#> [1] FALSE
1 / 49 * 49 == 1
#> [1] FALSE
```

Use near() to make it true.
```
near(1 / 49 * 49, 1) # Note this comma.
```

2.  
* filter(dataframe, conditions of colname) # filter rows by conditions
* arrange(dataframe, colname) or arrange(dataframe, desc(colname)) # re-order rows according to one or several columns.
* select(dataframe, conditions) # select columns
  * conditions:  
    starts_with("")  
    ends_with("")  
    contains("")  
    matches("regular expression") # See regular expression  
    num_range("x", 1:3) # Matches x1, x2, x3.  
    everything(**empty!**) # the rest of columns  
    any_of(c("", "",...))  
* rename(dataframe, old colname = new colname)
* mutate(dataframe, new colname = old colnames +-*/...) # add new columns
* transmute(dataframe, new colname = old colnames +-*/...) # keep only new columns

3. cumulative and rolling aggregates: cumsum(), cumprod(), cummean()

4. Convert time to a more convenient representation.
```
transmute(flights,
  dep_time,
  hour = dep_time %/% 100,
  minute = dep_time %% 100
)
```

5. summarise(dataset, new variable = old variable +-*/...)is useful when grouped with group_by(). n() counts the number of counts in each group. n_distinct() counts the number of counts in each unique group.

6. ungroup(dataset)

7. control+option+enter: run the whole script before the cursor.

8. Don't include any ```install.packages()``` or ```setwd()``` in the R script. It's antisocial to change settings on other people's computer.
