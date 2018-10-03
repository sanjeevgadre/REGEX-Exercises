These are solutions to the exercises found at:
<https://www.r-exercises.com/2018/10/01/pull-the-right-strings-with-stringr-exercises/>.
I have used the stringr library to solve these exercises

### 8.1

    addresses %>% str_to_lower()

    ## [1] "14 pine street, los angeles"      "152 redwood street, seattle"     
    ## [3] "8 washington boulevard, new york"

### 8.2

    addresses %>% str_match("[0-9]*\\s")

    ##      [,1]  
    ## [1,] "14 " 
    ## [2,] "152 "
    ## [3,] "8 "

### 8.3

    addresses %>% str_split("\\,", n=2, simplify=TRUE)

    ##      [,1]                     [,2]          
    ## [1,] "14 Pine Street"         " Los Angeles"
    ## [2,] "152 Redwood Street"     " Seattle"    
    ## [3,] "8 Washington Boulevard" " New York"

### 8.4

    x = addresses %>% str_split("\\,", n=2, simplify=TRUE)
    y = x[,1] %>% str_split("\\s", n=2, simplify=TRUE)
    cbind(y,x[,2]) %>% as.matrix()

    ##      [,1]  [,2]                   [,3]          
    ## [1,] "14"  "Pine Street"          " Los Angeles"
    ## [2,] "152" "Redwood Street"       " Seattle"    
    ## [3,] "8"   "Washington Boulevard" " New York"

    #Alternate, more concise, solution per the key
    addresses %>% str_split("(?<=[0-9])\\s|,\\s", n=Inf, simplify=TRUE)

    ##      [,1]  [,2]                   [,3]         
    ## [1,] "14"  "Pine Street"          "Los Angeles"
    ## [2,] "152" "Redwood Street"       "Seattle"    
    ## [3,] "8"   "Washington Boulevard" "New York"

8.5
---

    first.word = str_extract(long_sentences, "^[A-Z]\\w+")
    last.word = str_extract(long_sentences, "\\w+\\.$") %>% str_sub(.,1,-2)

    ifelse((str_sub(first.word,1,1)=="T" & str_sub(last.word,-1,-1) == "s"), str_c(first.word, " ", last.word), 
           ifelse(str_sub(first.word,1,1)=="T", first.word,
                  ifelse(str_sub(last.word,-1,-1)=="s", last.word,
                         "NA")
                  )
           )

    ##  [1] "The planks" "NA"         "NA"         "These"      "bowls"     
    ##  [6] "The"        "The"        "The"        "us"         "NA"

    #Alternate, more concise solution, per the key
    str_extract_all(string = long_sentences, pattern = "^T[A-z]+|[A-z]+s\\.$")

    ## [[1]]
    ## [1] "The"     "planks."
    ## 
    ## [[2]]
    ## character(0)
    ## 
    ## [[3]]
    ## character(0)
    ## 
    ## [[4]]
    ## [1] "These"
    ## 
    ## [[5]]
    ## [1] "bowls."
    ## 
    ## [[6]]
    ## [1] "The"
    ## 
    ## [[7]]
    ## [1] "The"
    ## 
    ## [[8]]
    ## [1] "The"
    ## 
    ## [[9]]
    ## [1] "us."
    ## 
    ## [[10]]
    ## character(0)

### 8.6

    str_trunc(long_sentences, 20, side="right", ellipsis="..")

    ##  [1] "The birch canoe sl.." "Glue the sheet to .." "It's easy to tell .."
    ##  [4] "These days a chick.." "Rice is often serv.." "The juice of lemon.."
    ##  [7] "The box was thrown.." "The hogs were fed .." "Four hours of stea.."
    ## [10] "Large size in stoc.."

### 8.7

    products %>% str_squish() %>% str_to_upper(locale="en")

    ## [1] "TV"               "LAPTOP"           "PORTABLE CHARGER"
    ## [4] "WIRELESS KEYBORD" "HEADPHONES"

### 8.8

    field_names %>% str_replace_all("_", " ") %>% str_to_title()

    ## [1] "Order Number"   "Order Date"     "Customer Email" "Product Title" 
    ## [5] "Amount"

### 8.9

    field_names %>% 
      str_length() %>% 
        which.max() %>% 
          field_names[.] %>% 
            str_length() %>%
              str_pad(field_names, ., side="left", pad=" ")

    ## [1] "  order_number" "    order_date" "customer_email" " product_title"
    ## [5] "        amount"

### 8.10

    str_match(employee_skills, "([A-z ]*) \\((Pro|Medium)\\)")[,2:3]

    ##      [,1]          [,2]    
    ## [1,] NA            NA      
    ## [2,] "Rita Murphy" "Pro"   
    ## [3,] "Chris White" "Pro"   
    ## [4,] "Sarah Reid"  "Medium"
