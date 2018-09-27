These are solutions to the exercises found at:
<https://www.r-exercises.com/2017/07/14/hacking-strings-with-stringr/>.
I have used the stringr library to solve these exercises

### 6.1

    x = "I AM SAM. I AM SAM. SAM I AM"
    y = "THAT SAM-I-AM! THAT SAM-I-AM! I DO NOT LIKE THAT SAM-I-AM!"
    z = "DO WOULD YOU LIKE GREEN EGGS AND HAM?"

    answer.6.1 = str_c(x,y,z, sep=" ")
    answer.6.1

    ## [1] "I AM SAM. I AM SAM. SAM I AM THAT SAM-I-AM! THAT SAM-I-AM! I DO NOT LIKE THAT SAM-I-AM! DO WOULD YOU LIKE GREEN EGGS AND HAM?"

### 6.2

    dat = c(x,y,z,NA)

    answer.6.2.a = paste(dat, sep=" ", collapse=" ")
    answer.6.2.a

    ## [1] "I AM SAM. I AM SAM. SAM I AM THAT SAM-I-AM! THAT SAM-I-AM! I DO NOT LIKE THAT SAM-I-AM! DO WOULD YOU LIKE GREEN EGGS AND HAM? NA"

    answer.6.2.b = str_c(dat, sep=" ", collapse=" ")
    answer.6.2.b

    ## [1] NA

The paste() simply treats NA element of the vector as another string and
concatenates to the other strings in the vector. str\_c() on the other
hand gives an NA output if one of the elements is NA. To convert the NA
to a literal NA we use str\_replace\_na() -
`str_c(str_replace_na(dat), sep=" ", collapse=" ")`

### 6.3

    data("babynames")
    str_length(head(babynames$name)) #The vector length is very large and hence restricting it using the head()

    ## [1] 4 4 4 9 6 8

### 6.4

    dat = "Sanjeev Gadre"
    str_sub(dat, -1L)

    ## [1] "e"

    str_sub(dat, -5L)

    ## [1] "Gadre"

### 6.5

    data("mtcars")
    rownames(mtcars) %>% str_subset("Merc")

    ## [1] "Merc 240D"   "Merc 230"    "Merc 280"    "Merc 280C"   "Merc 450SE" 
    ## [6] "Merc 450SL"  "Merc 450SLC"

### 6.6

    rownames(mtcars) %>% str_count("e") %>% sum()

    ## [1] 25

### 6.7

    j <- "The_quick_brown_fox_jumps_over_the_lazy_dog"
    str_split(j, pattern="_", n=Inf, simplify=FALSE)

    ## [[1]]
    ## [1] "The"   "quick" "brown" "fox"   "jumps" "over"  "the"   "lazy"  "dog"

### 6.8

    str_split(j, pattern="_", n=2, simplify=FALSE)

    ## [[1]]
    ## [1] "The"                                    
    ## [2] "quick_brown_fox_jumps_over_the_lazy_dog"

### 5.9

    str_replace(j, "_", "-")

    ## [1] "The-quick_brown_fox_jumps_over_the_lazy_dog"

    str_replace_all(j, "_", "-")

    ## [1] "The-quick-brown-fox-jumps-over-the-lazy-dog"

### 5.10

    na_string_vec = c("The_quick_brown_fox_jumps_over_the_lazy_dog",NA)
    str_replace_na(na_string_vec, "NA")

    ## [1] "The_quick_brown_fox_jumps_over_the_lazy_dog"
    ## [2] "NA"
