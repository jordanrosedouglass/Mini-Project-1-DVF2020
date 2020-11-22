# Mini Project 1 Data Visualization Fall 2020

This Mini Project analyzes birth data in the United States from 2000-2014.

## The Author:

The author of this project is a second semester graduate student studying Engineering Management; this students undergraduate degree is in __Data Analytics__ with a concentration in __Health Informatics.__ 

The dataset for this project was chosen in part by the fact of its ties to the healthcare industry - in literature, annual live births often coincide with a nations overall health.

## Getting Started:

This project uses _RStudio_ entirely. The data itself pulls from another [Github](https://raw.githubusercontent.com/reisanar/datasets/master/us_births_00_14.csv) repository. 

# The Project:

After loading the required libraries for this project, the data was loaded and renamed as `birth_data` - this was done entirely to make the dataframe name easier to remember and to know clearly what it was to the reader.

Once downloaded, a new variable `season` was created to assign birth months to the established seasons in which they coiincide with. The code snippet used for developing this new variable can be found below:
 ```
 birth_data <- birth_data %>%
  mutate(
    season = case_when(
      month %in% 10:12 ~ "Fall",
      month %in%  1:3  ~ "Winter",
      month %in%  4:6  ~ "Spring",
      TRUE ~ "Summer"))
summary(birth_data)
```

The creation of this variable was successful. 

The next step was the discovery of proportions of births happening between months and days of the week, as well as the proportion in which births happened by year; each of these were done using similar code snippets - an example can be found below:

```
daily_prop <- birth_data %>%
  group_by(day_of_week) %>%
  summarize(total = sum(births)) %>%
  mutate(prop = round(100* total / sum(total),2))
  ```
For example `day_of_week` was interchanged with `year` and `month`; in hindsight, another opportunity was also interchanging with the newly found `season` variable.

---

# Visualizations:

Once the data was aggregated to liking, visualizations were created.

Below, a preliminary example of the visualizations can be viewed. Several were created for this project and there is opportunity for several more.

Visualization one shows births over time

![](https://github.com/jordanrosedouglass/Mini-Project-1-DVF2020/blob/main/Screen%20Shot%202020-11-22%20at%201.19.14%20PM.png)

From this visualization alone, we can see that there is quite a lot of valuable data to be studied - the possibilities are endless.  We can further visualize the variables, as below, by days of the week.

![](https://github.com/jordanrosedouglass/Mini-Project-1-DVF2020/blob/main/Screen%20Shot%202020-11-22%20at%201.25.22%20PM.png)

# Notes:

More visualizations and the complete folder of this __Mini Project 1__ can be found [here](https://github.com/jordanrosedouglass/Mini-Project-1-DVF2020/tree/main/MiniProject1). This folder contains the _report_, the .csv of the data and the _.rmd_ file for RStudio execution.

The feedback overall for this project has been positive, however, the author understands that growth and improvements can be made only through more projects and opportunities can one become an expert in the field.

That being said, some feedback provided includes:
* Refactoring days of the week to order them as we expect them to; for example, beginning on Sundays and work through that way.
* Aviod mixing __<-__ and __=__ when creating variable names.


# Please feel free to leave the author notes on improvements and more.

![](https://media2.giphy.com/media/a3IWyhkEC0p32/giphy.gif?cid=ecf05e472uefiduptdxjrlvzbry4zbw8249km6uwisnxf45t&rid=giphy.gif)




