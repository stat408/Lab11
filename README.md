## Lab 11


## Lab Overview

The entire lab will be worth 20 points. 


### Q1. (7 points)

Use the dataset at <https://raw.githubusercontent.com/stat408/Data/refs/heads/main/MT_Income.csv> to recreate this figure ![MT Income](https://github.com/stat408/Lab11/blob/master/Lab11_fig1.png?raw=true)



### Q2. (7 points)

The following function should take  `county_name`, `start_year`, and `end_year` to return a plot of the per capita over that time period. Fix the R code and use a bullets to list all of the changes you made to the code.

```
#| eval: FALSE
plot_income <- county_name, start_year, end_year{
  MT_Income <- read_csv(https://raw.githubusercontent.com/stat408/Data/refs/heads/main/MT_Income.csv)

    MT_Income |>
    filter(Area = "county_name",
           Year >= start_year,
           Year <= end_year) |>
      mutate(income = parse_number(Income)) +
      ggplot(y = income, x = Year) 
      geom_col() +
      scale_y_continuous(labels = scales::dollar_format()) +
      ylab('Per Capita Income") +
      labs(title = paste("BEA estimated per capita income for", county_name, 'County')) +
      theme_minimal()
}
```



Verify your function works by running the following code. You'd expect your results to look like the following figure

```
#| eval: FALSE
plot_income(county_name = 'Gallatin', start_year = 1980, end_year = 2019)
```

 ![MT Income2](https://github.com/stat408/Lab11/blob/master/Lab11_fig2.png?raw=true)
 
### Question 3 (6 points)
 
 Troubleshoot the following code which should return a table with number of crimes of each crime type on the summer solstice (June 20). Make sure the table is shorted from most common crime type to less common crime type
 
 
```
#| eval: FALSE
seattle <- read_csv('http://math.montana.edu/ahoegh/teaching/stat408/datasets/Seattle_911_062016.csv') 

seattle %|%
  filter(month <- 6, Day == 20) |>
  count(Event.ClearanceGroup) |>
  kable() |>
  arrange(n) |>
``` 
