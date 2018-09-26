These are solutions to the exercises found at:
<https://www.r-exercises.com/2017/05/18/character-functions-advanced/>.
I have used the stringr library to solve these exercises

### 5.1

    answer.5.1 = str_remove_all(TEXT1, "[:punct:]")
    answer.5.1

    ##  [1] "    scit bene venator cervis ubi retia tendat"       
    ##  [2] "         scit bene qua frendens valle moretur aper"  
    ##  [3] "    aucupibus noti frutices qui sustinet hamos"      
    ##  [4] "         novit quae multo pisce natentur aquae"      
    ##  [5] "    tu quoque materiam longo qui quaeris amori"      
    ##  [6] ""                                                    
    ##  [7] "         ante frequens quo sit disce puella loco"    
    ##  [8] "    non ego quaerentem vento dare vela iubebo"       
    ##  [9] "         nec tibi ut invenias longa terenda via est" 
    ## [10] "    Andromedan Perseus nigris portarit ab Indis"     
    ## [11] "         raptaque sit Phrygio Graia puella viro"     
    ## [12] ""                                                    
    ## [13] "    tot tibi tamque dabit formosas Roma puellas"     
    ## [14] "         Haec habet ut dicas quicquid in orbe fuit"  
    ## [15] "    Gargara quot segetes quot habet Methymna racemos"
    ## [16] "         aequore quot pisces fronde teguntur aves"   
    ## [17] "    quot caelum stellas tot habet tua Roma puellas"

### 5.2

    answer.5.2 = str_remove_all(answer.5.1, "[:blank:]") %>% str_length() %>% sum()
    answer.5.2

    ## [1] 536

### 5.3

    answer.5.3 = answer.5.1 %>% str_c(sep="", collapse=" ") %>% str_squish() %>% str_split("\\s", n=Inf, simplify=TRUE)
    length(answer.5.3)

    ## [1] 103

### 5.4

    answer.5.4 = answer.5.3 %>% str_to_lower() %>% table()  %>% order(decreasing = TRUE)  %>% .[1]
    table(answer.5.3) %>% names(.) %>% .[answer.5.4]

    ## [1] "quot"

### 5.5

    answer.5.5 = str_which(answer.5.3, "[:upper:]")
    answer.5.3[answer.5.5] %>% unique()

    ## [1] "Andromedan" "Perseus"    "Indis"      "Phrygio"    "Graia"     
    ## [6] "Roma"       "Haec"       "Gargara"    "Methymna"

### 5.6

    answer.5.6 = OVID %>% str_to_lower() %>% str_remove_all("[:punct:]") %>% str_extract_all("\\S{1}", simplify=TRUE) %>% table()
    index = order(answer.5.6, decreasing=TRUE)
    answer.5.6[index[1:5]]

    ## .
    ##   e   a   i   t   s 
    ## 347 241 229 221 200

### 5.7

    answer.5.7 = letters %in% names(answer.5.6)
    letters[answer.5.7 == FALSE]

    ## [1] "j" "k" "w" "z"

### 5.8

    answer.5.8 = str_extract(OVID, c("Chandler", "Phoebe", "Ross", "Monica", "Joey"))
    answer.5.8[!is.na(answer.5.8)]

    ## [1] "Phoebe"

### 5.9

    answer.5.9 = as.character(OVID[[1]])
    str_which(answer.5.9, "Phoebe") %>% answer.5.9[.]

    ## [1] "    non ego, Phoebe, datas a te mihi mentiar artes,"

### 5.10

    answer.5.10 = answer.5.9 %>% str_c(sep="", collapse=" ") %>% str_squish() %>% str_remove_all("[:punct:]") %>% str_to_lower() %>% str_split("\\s", n=Inf, simplify=TRUE)

    str_sub(answer.5.10, start=-1L, end=-1L) %>% .[] %in% c("a","e","i","o","u") %>% sum() #number of words that end in a vowel

    ## [1] 199

    length(answer.5.10) - str_sub(answer.5.10, start=-1L, end=-1L) %>% .[] %in% c("a","e","i","o","u") %>% sum() #number of words that end in a consonants

    ## [1] 284
