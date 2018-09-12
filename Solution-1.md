These are solutions to the exercises available at
<https://www.r-exercises.com/2016/10/30/regular-expressions-part-1/>

I prefer using the "stringr" package to deal with text string
manipulations

    library(stringr)

### 1-1

    text1 = "The current year is 2016"

    my_pattern = "[:digit:]"
    str_detect(text1, my_pattern)

    ## [1] TRUE

### 1-2

    string_position = str_locate_all(text1, my_pattern)
    string_position

    ## [[1]]
    ##      start end
    ## [1,]    21  21
    ## [2,]    22  22
    ## [3,]    23  23
    ## [4,]    24  24

### 1-3

    my_pattern = "[[:upper:][:digit]]"
    str_detect(text1, my_pattern)

    ## [1] TRUE

### 1-4

    first_space = str_locate(text1, "[:space:]")
    first_space[1,1]

    ## start 
    ##     4

### 1-5

    str_detect(text1,"[[:lower:].[:digit:]]")

    ## [1] TRUE

### 1-6

    string_pos_2 = str_locate(text1,"[:lower:].[:digit:]")[[1,1]]
    string_pos_2

    ## [1] 19

### 1-7

    string_pos_3 = str_locate(text1,"\\s[:lower:]{2}\\s")[[1,1]]
    string_pos_3

    ## [1] 17

### 1-8

    text2 = str_replace(text1, "\\s[:lower:]{2}\\s", " is not ")
    text2

    ## [1] "The current year is not 2016"

### 1A-9

    string_pos_4 = str_locate(text2,"\\d{4}$")[[1,1]]
    string_pos_4

    ## [1] 25

### 1-10

    str_sub(text2, string_pos_4, string_pos_4+1)

    ## [1] "20"

------------------------------------------------------------------------
