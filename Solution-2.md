These are solutions to the exercises found at
<http://r-tutorials.com/r-exercises-61-70-string-manipulation-gsub-regex-regular-expressions/>

### 2.1

    college.names=row.names(College)
    texas.colleges=str_match(college.names, "Texas")
    summary(texas.colleges)

    ##      V1     
    ##  Texas: 11  
    ##  NA's :766

    texas.colleges.index=which(texas.colleges[,1]=="Texas")
    texas.colleges.index

    ##  [1] 179 582 583 584 585 586 587 658 685 686 687

    texas.college.details = College[texas.colleges.index,]
    head(texas.college.details)

    ##                                    Private  Apps Accept Enroll Top10perc
    ## East Texas Baptist University          Yes   379    341    265        10
    ## Texas A&M Univ. at College Station      No 14474  10519   6392        49
    ## Texas A&M University at Galveston       No   529    481    243        22
    ## Texas Christian University             Yes  4095   3079   1195        33
    ## Texas Lutheran College                 Yes   497    423    215        27
    ## Texas Southern University               No  4345   3245   2604        15
    ##                                    Top25perc F.Undergrad P.Undergrad
    ## East Texas Baptist University             36        1050         151
    ## Texas A&M Univ. at College Station        85       31643        2798
    ## Texas A&M University at Galveston         47        1206         134
    ## Texas Christian University                64        5064         660
    ## Texas Lutheran College                    57         895         429
    ## Texas Southern University                 85        5584        3101
    ##                                    Outstate Room.Board Books Personal PhD
    ## East Texas Baptist University          4950       2780   530     1500  62
    ## Texas A&M Univ. at College Station     5130       3412   600     2144  89
    ## Texas A&M University at Galveston      4860       3122   600      650 103
    ## Texas Christian University             8490       3320   650     2400  81
    ## Texas Lutheran College                 7850       3410   490     1700  54
    ## Texas Southern University              7860       3360   600     1700  65
    ##                                    Terminal S.F.Ratio perc.alumni Expend
    ## East Texas Baptist University            62      15.7           7   5619
    ## Texas A&M Univ. at College Station       91      23.1          29   8471
    ## Texas A&M University at Galveston        88      17.4          16   6415
    ## Texas Christian University               93      14.8          23   9158
    ## Texas Lutheran College                   58      13.8          24   7002
    ## Texas Southern University                75      18.2          21   3605
    ##                                    Grad.Rate
    ## East Texas Baptist University             38
    ## Texas A&M Univ. at College Station        69
    ## Texas A&M University at Galveston         43
    ## Texas Christian University                64
    ## Texas Lutheran College                    50
    ## Texas Southern University                 10

### 2.2

    college.names = str_split(college.names,"\\s", n=Inf)
    head(college.names)

    ## [[1]]
    ## [1] "Abilene"    "Christian"  "University"
    ## 
    ## [[2]]
    ## [1] "Adelphi"    "University"
    ## 
    ## [[3]]
    ## [1] "Adrian"  "College"
    ## 
    ## [[4]]
    ## [1] "Agnes"   "Scott"   "College"
    ## 
    ## [[5]]
    ## [1] "Alaska"     "Pacific"    "University"
    ## 
    ## [[6]]
    ## [1] "Albertson" "College"

    college.names = str_to_lower(college.names)
    head(college.names)

    ## [1] "c(\"abilene\", \"christian\", \"university\")"
    ## [2] "c(\"adelphi\", \"university\")"               
    ## [3] "c(\"adrian\", \"college\")"                   
    ## [4] "c(\"agnes\", \"scott\", \"college\")"         
    ## [5] "c(\"alaska\", \"pacific\", \"university\")"   
    ## [6] "c(\"albertson\", \"college\")"

    college.names = casefold(college.names, upper=TRUE)
    head(college.names)

    ## [1] "C(\"ABILENE\", \"CHRISTIAN\", \"UNIVERSITY\")"
    ## [2] "C(\"ADELPHI\", \"UNIVERSITY\")"               
    ## [3] "C(\"ADRIAN\", \"COLLEGE\")"                   
    ## [4] "C(\"AGNES\", \"SCOTT\", \"COLLEGE\")"         
    ## [5] "C(\"ALASKA\", \"PACIFIC\", \"UNIVERSITY\")"   
    ## [6] "C(\"ALBERTSON\", \"COLLEGE\")"

### 2.3

    College %>% rownames() %>% str_which("University")

    ##   [1]   1   2   5  11  18  19  20  21  22  24  26  28  34  39  40  44  46
    ##  [18]  60  62  64  65  66  70  71  73  75  78  80  82  85  88  92  95 103
    ##  [35] 104 105 108 112 113 116 118 119 124 142 145 148 149 153 162 163 164
    ##  [52] 166 167 172 173 175 177 178 179 181 182 190 192 193 197 198 202 204
    ##  [69] 206 208 209 212 214 215 216 219 220 222 224 228 234 244 246 248 249
    ##  [86] 251 258 265 270 271 274 275 276 278 280 283 284 285 289 290 299 304
    ## [103] 305 306 307 310 313 315 316 317 321 325 326 328 329 330 341 345 346
    ## [120] 351 353 356 358 360 366 367 368 370 372 376 377 383 384 386 402 404
    ## [137] 408 410 412 413 416 418 419 420 421 422 425 426 428 431 432 433 434
    ## [154] 435 436 437 439 440 441 442 444 445 447 451 457 458 460 462 464 466
    ## [171] 474 480 485 486 487 488 490 493 496 498 506 507 509 510 511 512 517
    ## [188] 518 519 521 530 531 534 535 536 537 538 541 542 545 548 552 557 575
    ## [205] 577 580 583 584 586 587 590 591 593 597 598 600 604 605 606 607 608
    ## [222] 609 610 611 612 613 614 615 616 617 618 619 620 621 622 623 624 625
    ## [239] 626 627 628 629 630 631 632 633 634 635 636 637 638 639 640 641 642
    ## [256] 643 644 645 646 647 648 649 650 651 652 653 654 655 656 657 658 659
    ## [273] 660 661 662 663 664 665 666 667 668 669 670 671 672 673 674 675 676
    ## [290] 677 678 679 680 681 682 683 684 685 686 687 688 689 690 691 692 693
    ## [307] 694 695 696 697 698 699 700 701 702 703 704 707 708 709 711 712 713
    ## [324] 715 721 722 726 728 729 733 738 739 742 744 747 759 760 761 763 767
    ## [341] 768 770 774 775 776

    College %>% rownames() %>% str_which("University") %>% length()

    ## [1] 345

    College %>% rownames() %>% str_which("College") %>% length()

    ## [1] 405

There is an error in the solution key provided on the page for counting
the number of "College". It uses str\_count() and then sum() to find out
the number of entries with "College" in them. However, "Arkansas College
(Lyon College)" will return a value of 2 as "College" appears twice and
incorrectly increases the number of entries with "College" in them to
406. My solution of str\_which() followed by length() avoids this
"double counting". This error is present also for the code used to count
the number of "University".

### 2.4

    "get" %>% str_pad(10, side="both", pad="0")

    ## [1] "000get0000"

    paddedstring = "Oslo" %>% str_pad(10, side="left", pad=" ")
    paddedstring

    ## [1] "      Oslo"

    paddedstring %>% str_trim(side="left")

    ## [1] "Oslo"

    paddedstring %>% str_trunc(7, side="left")

    ## [1] "...Oslo"

### 2.8

    mtcars.names = rownames(mtcars)
    head(mtcars.names)

    ## [1] "Mazda RX4"         "Mazda RX4 Wag"     "Datsun 710"       
    ## [4] "Hornet 4 Drive"    "Hornet Sportabout" "Valiant"

    mtcars.names %>% str_replace_all("\\d+", "") %>% str_replace_all("[:punct:]", "") %>% str_replace_all("\\s", "") %>% str_replace_all("[:upper:]", "") %>% str_replace_all("[:lower:]", "")

    ##  [1] "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" ""
    ## [24] "" "" "" "" "" "" "" "" ""

### 2.9

    mtcars.names %>% str_replace_all("Merc(?=\\b)", "Mercedes")

    ##  [1] "Mazda RX4"           "Mazda RX4 Wag"       "Datsun 710"         
    ##  [4] "Hornet 4 Drive"      "Hornet Sportabout"   "Valiant"            
    ##  [7] "Duster 360"          "Mercedes 240D"       "Mercedes 230"       
    ## [10] "Mercedes 280"        "Mercedes 280C"       "Mercedes 450SE"     
    ## [13] "Mercedes 450SL"      "Mercedes 450SLC"     "Cadillac Fleetwood" 
    ## [16] "Lincoln Continental" "Chrysler Imperial"   "Fiat 128"           
    ## [19] "Honda Civic"         "Toyota Corolla"      "Toyota Corona"      
    ## [22] "Dodge Challenger"    "AMC Javelin"         "Camaro Z28"         
    ## [25] "Pontiac Firebird"    "Fiat X1-9"           "Porsche 914-2"      
    ## [28] "Lotus Europa"        "Ford Pantera L"      "Ferrari Dino"       
    ## [31] "Maserati Bora"       "Volvo 142E"

### 2.10

    mystring = "Gabriel-Henry.Tedd.-John (Yorkshire)"

    mystring %>% str_replace_all("\\.", " ")

    ## [1] "Gabriel-Henry Tedd -John (Yorkshire)"

    mystring %>% str_replace_all("\\s*\\([^\\)]*\\)", "")

    ## [1] "Gabriel-Henry.Tedd.-John"
