These are solutions to the exercises found at:
<https://www.r-exercises.com/2016/11/27/string-manipulation-exercises/>.
I have used the stringr library to solve these exercises

### 4.1

    answer.4.1 = read_lines("http://www.r-exercises.com/wp-content/uploads/2016/11/gambler.txt")
    answer.4.1

    ## [1] "At length I returned from two weeks leave of absence to find that my patrons had arrived three days ago in Roulettenberg. I received from them a welcome quite different to that which I had expected. The General eyed me coldly, greeted me in rather haughty fashion, and dismissed me to pay my respects to his sister. It was clear that from SOMEWHERE money had been acquired. I thought I could even detect a certain shamefacedness in the General's glance. Maria Philipovna, too, seemed distraught, and conversed with me with an air of detachment. Nevertheless, she took the money which I handed to her, counted it, and listened to what I had to tell. To luncheon there were expected that day a Monsieur Mezentsov, a French lady, and an Englishman; for, whenever money was in hand, a banquet in Muscovite style was always given. Polina Alexandrovna, on seeing me, inquired why I had been so long away. Then, without waiting for an answer, she departed. Evidently this was not mere accident, and I felt that I must throw some light upon matters. It was high time that I did so."                                                                                     
    ## [2] "I was assigned a small room on the fourth floor of the hotel (for you must know that I belonged to the General's suite). So far as I could see, the party had already gained some notoriety in the place, which had come to look upon the General as a Russian nobleman of great wealth. Indeed, even before luncheon he charged me, among other things, to get two thousand-franc notes changed for him at the hotel counter, which put us in a position to be thought millionaires at all events for a week! Later, I was about to take Mischa and Nadia for a walk when a summons reached me from the staircase that I must attend the General. He began by deigning to inquire of me where I was going to take the children; and as he did so, I could see that he failed to look me in the eyes. He WANTED to do so, but each time was met by me with such a fixed, disrespectful stare that he desisted in confusion. In pompous language, however, which jumbled one sentence into another, and at length grew disconnected, he gave me to understand that I was to lead the children altogether away from the Casino, and out into the park. Finally his anger exploded, and he added sharply:"
    ## [3] "\"I suppose you would like to take them to the Casino to play roulette? Well, excuse my speaking so plainly, but I know how addicted you are to gambling. Though I am not your mentor, nor wish to be, at least I have a right to require that you shall not actually compromise me.\""                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
    ## [4] "\"I have no money for gambling,\" I quietly replied."

### 4.2

    answer.4.2 = length(answer.4.1)
    answer.4.2

    ## [1] 4

### 4.3

    answer.4.3 = str_length(answer.4.1)
    answer.4.3

    ## [1] 1073 1158  276   50

### 4.4

    data("sentences")

    answer.4.4 = str_c(answer.4.1, sep=" ", collapse=" ")
    answer.4.4

    ## [1] "At length I returned from two weeks leave of absence to find that my patrons had arrived three days ago in Roulettenberg. I received from them a welcome quite different to that which I had expected. The General eyed me coldly, greeted me in rather haughty fashion, and dismissed me to pay my respects to his sister. It was clear that from SOMEWHERE money had been acquired. I thought I could even detect a certain shamefacedness in the General's glance. Maria Philipovna, too, seemed distraught, and conversed with me with an air of detachment. Nevertheless, she took the money which I handed to her, counted it, and listened to what I had to tell. To luncheon there were expected that day a Monsieur Mezentsov, a French lady, and an Englishman; for, whenever money was in hand, a banquet in Muscovite style was always given. Polina Alexandrovna, on seeing me, inquired why I had been so long away. Then, without waiting for an answer, she departed. Evidently this was not mere accident, and I felt that I must throw some light upon matters. It was high time that I did so. I was assigned a small room on the fourth floor of the hotel (for you must know that I belonged to the General's suite). So far as I could see, the party had already gained some notoriety in the place, which had come to look upon the General as a Russian nobleman of great wealth. Indeed, even before luncheon he charged me, among other things, to get two thousand-franc notes changed for him at the hotel counter, which put us in a position to be thought millionaires at all events for a week! Later, I was about to take Mischa and Nadia for a walk when a summons reached me from the staircase that I must attend the General. He began by deigning to inquire of me where I was going to take the children; and as he did so, I could see that he failed to look me in the eyes. He WANTED to do so, but each time was met by me with such a fixed, disrespectful stare that he desisted in confusion. In pompous language, however, which jumbled one sentence into another, and at length grew disconnected, he gave me to understand that I was to lead the children altogether away from the Casino, and out into the park. Finally his anger exploded, and he added sharply: \"I suppose you would like to take them to the Casino to play roulette? Well, excuse my speaking so plainly, but I know how addicted you are to gambling. Though I am not your mentor, nor wish to be, at least I have a right to require that you shall not actually compromise me.\" \"I have no money for gambling,\" I quietly replied."

### 4.5

    answer.4.5 = str_to_upper(answer.4.4, locale="en")
    write_lines(answer.4.5, path="./gambler-upper.txt", append=FALSE)

### 4.6

    answer.4.6 = str_replace_all(answer.4.1, c("a"="A", "t"="T"))
    answer.4.6

    ## [1] "AT lengTh I reTurned from Two weeks leAve of Absence To find ThAT my pATrons hAd Arrived Three dAys Ago in RouleTTenberg. I received from Them A welcome quiTe differenT To ThAT which I hAd expecTed. The GenerAl eyed me coldly, greeTed me in rATher hAughTy fAshion, And dismissed me To pAy my respecTs To his sisTer. IT wAs cleAr ThAT from SOMEWHERE money hAd been Acquired. I ThoughT I could even deTecT A cerTAin shAmefAcedness in The GenerAl's glAnce. MAriA PhilipovnA, Too, seemed disTrAughT, And conversed wiTh me wiTh An Air of deTAchmenT. NeverTheless, she Took The money which I hAnded To her, counTed iT, And lisTened To whAT I hAd To Tell. To luncheon There were expecTed ThAT dAy A Monsieur MezenTsov, A French lAdy, And An EnglishmAn; for, whenever money wAs in hAnd, A bAnqueT in MuscoviTe sTyle wAs AlwAys given. PolinA AlexAndrovnA, on seeing me, inquired why I hAd been so long AwAy. Then, wiThouT wAiTing for An Answer, she depArTed. EvidenTly This wAs noT mere AccidenT, And I felT ThAT I musT Throw some lighT upon mATTers. IT wAs high Time ThAT I did so."                                                                                     
    ## [2] "I wAs Assigned A smAll room on The fourTh floor of The hoTel (for you musT know ThAT I belonged To The GenerAl's suiTe). So fAr As I could see, The pArTy hAd AlreAdy gAined some noTorieTy in The plAce, which hAd come To look upon The GenerAl As A RussiAn noblemAn of greAT weAlTh. Indeed, even before luncheon he chArged me, Among oTher Things, To geT Two ThousAnd-frAnc noTes chAnged for him AT The hoTel counTer, which puT us in A posiTion To be ThoughT millionAires AT All evenTs for A week! LATer, I wAs AbouT To TAke MischA And NAdiA for A wAlk when A summons reAched me from The sTAircAse ThAT I musT ATTend The GenerAl. He begAn by deigning To inquire of me where I wAs going To TAke The children; And As he did so, I could see ThAT he fAiled To look me in The eyes. He WANTED To do so, buT eAch Time wAs meT by me wiTh such A fixed, disrespecTful sTAre ThAT he desisTed in confusion. In pompous lAnguAge, however, which jumbled one senTence inTo AnoTher, And AT lengTh grew disconnecTed, he gAve me To undersTAnd ThAT I wAs To leAd The children AlTogeTher AwAy from The CAsino, And ouT inTo The pArk. FinAlly his Anger exploded, And he Added shArply:"
    ## [3] "\"I suppose you would like To TAke Them To The CAsino To plAy rouleTTe? Well, excuse my speAking so plAinly, buT I know how AddicTed you Are To gAmbling. Though I Am noT your menTor, nor wish To be, AT leAsT I hAve A righT To require ThAT you shAll noT AcTuAlly compromise me.\""                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                
    ## [4] "\"I hAve no money for gAmbling,\" I quieTly replied."

### 4.7

    answer.4.7 = str_detect(answer.4.4, "lucky")
    answer.4.7

    ## [1] FALSE

### 4.8

    answer.4.8 = str_count(answer.4.4, "\\S*\\s") + 1
    answer.4.8

    ## [1] 473

### 4.9

    answer.4.9 = str_to_lower(answer.4.4, locale="en") %>% str_count("money")
    answer.4.9

    ## [1] 4

### 4.10

    first.number = readline("Enter a number: ")

    ## Enter a number:

    second.number = readline("Enter another number: ")

    ## Enter another number:

    first.number = as.integer(first.number)
    second.number = as.integer(second.number)
    division = round(first.number/second.number, digits=2)

    paste(c(first.number, "/", second.number, "=", division), sep = "")

    ## [1] "NA" "/"  "NA" "="  "NA"
