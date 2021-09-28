## Manipulating Data

### Reading files 

To read a single file you can use `read_csv` function.
#### example:
`your_variable_name <- read_csv("<yourpath>/yourfile.csv")`

But if you want to read multiple files from a directory, you can create functions that could read multiple files and turn them all into one single file. 
#### example: 
```
read_folder <- function(folder, file_pattern) {
    df <- list.files(path = folder, pattern = file_pattern)%>% 
      map_df(~read_file(., path=folder))  
  return(df)
}

read_file <- function(flnm, path) {
  return(read_delim(paste(path, flnm, sep=""), ",") %>% 
           mutate(filename = flnm))
}
```
 and then
 
`your_variable_name <- read_folder("<yourpath>", "*csv")`


### Filter 
To filter rows according to a specific value of a given column you can use the **_filter_** function. 

#### example: 

**original dataframe:**

```

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

```

If you want, for example, only the **red** fruits you should do:

```  
fruits_red <- fruits %>% filter(color == "red")
```

your dataset will look like this: 

```
| name       | color  | quantity | size   |
|------------|--------|----------|--------|
| apple      | red    | 1        | medium |
| strawberry | red    | 9        | small  |
| plum       | red    | 2        | medium |

```

Or, if you want all the fruits except the **red** ones you should do:

```  
fruits_red <- fruits %>% filter(color != "red")
```

### New Columns

### Select Columns

### Summarize Data








## Plots


### Axis, legend, plot labels, etc







### Histogram



