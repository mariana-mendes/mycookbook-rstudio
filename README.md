## Reading files 

To read a single file you can use `read_csv` function.
#### example:
`your_variable_name <- read_csv("<yourpath>/yourfile.csv")`
But if you want to read multiple files from a directory, you can create functions that could read multiple files and turn all into one single file. 
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



## Modifying axis, legend, plot labels, etc


# Análise Descritiva



## Histogram
