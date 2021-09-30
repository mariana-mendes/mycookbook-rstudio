## Manipulating Data

### Reading files 

To read a single file you can use `read_csv` function.
#### example:
``` 
your_variable_name <- read_csv("<yourpath>/yourfile.csv")
```

But if you want to read multiple files from a directory, you can create functions that could read multiple files and turn them all into one single file. 
#### example: 
```
read_folder <- function(folder, file_pattern) {
    df <- list.files(path = folder, pattern = file_pattern)%>% 
      map_df(~read_file(., path=folder))  
  return(df)
}

read_file <- function(flnm, path) {
  return(read_delim(paste(path, flnm, sep=""), ",")
}
```
 and then
 
```
your_variable_name <- read_folder("<yourpath>", "*csv")
```

##### to-do: explicar funções usadas. ou deixar essa forma de ler vários arquivos pra depois
- list.files
- map_df 
- read_file
- read_delim




### Filtering Values - _filter function_
To filter rows according to a specific value of a given column you can use the **_filter_** function. 

#### example: 

**original dataframe:**


| name       | color  | quantity | size   |
|------------|--------|----------|--------|
| apple      | red    | 1        | medium |
| banana     | yellow | 2        | medium |
| grape      | purple | 1        | small  |
| orange     | orange | 5        | medium |
| strawberry | red    | 9        | small  |
| plum       | red    | 2        | medium |
| mango      | yellow | 1        | medium |
| kiwi       | green  | 2        | small  |



If you want, for example, only the **red** fruits you should do:

```  
fruits_red <- fruits %>% filter(color == "red")
```

your dataset will look like this: 


| name       | color  | quantity | size   |
|------------|--------|----------|--------|
| apple      | red    | 1        | medium |
| strawberry | red    | 9        | small  |
| plum       | red    | 2        | medium |



Or, if you want all the fruits except the **red** ones you should do:

```  
fruits_red <- fruits %>% filter(color != "red")
```

### Create, modify, and delete columns - _mutate function_

If you want to add new columns to your dataset or even modifying columns, you could use **_mutate_** function.

```
your_dataframe %>% mutate(name_new_column = <function to caculate values for new column, you could use columns that already exists>)
``` 


[more details about how to use mutate function](https://dplyr.tidyverse.org/reference/mutate.html)

#### example

Let's create a column, using mutate, for a code related to the size, for example: _medium = M_ and _small = S_

``` 
frutis %>% mutate(code_size = ifelse(size == "small", "S", ifelse(size == "medium", "M", NA_real_)))

```
Then, your dataframe will look like this: 


| name       | color  | quantity | size   | code_size |
|------------|--------|----------|--------|-----------|
| apple      | red    | 1        | medium | M         |
| banana     | yellow | 2        | medium | M         |
| grape      | purple | 1        | small  | S         |
| orange     | orange | 5        | medium | M         |
| strawberry | red    | 9        | small  | S         |
| plum       | red    | 2        | medium | M         |
| mango      | yellow | 1        | medium | M         |
| kiwi       | green  | 2        | small  | S         |




### Select Columns - _select function_



### Summarize Data - _group by and summarise_





## Plots - _**basics**_


### Histograms 
- what
- when 
- examples


### Bar plot 
- what
- when
- examples

### Line


### Point



### Adjusting your plot

#### Axis, legend, plot labels, etc










