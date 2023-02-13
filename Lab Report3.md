The first interesting command option of grep I found is this: 

    $ ls | grep -v [pattern]
      
This command combines ls and grep[1], it's interesting to learn that you can combine some of those commands. This command find and print
all the files matching the pattern in current working directory. The ls tells greps which files to target. We notice that we didn't have destination file for the grep command.
-v means filter all the file without the matching pattern. This command is useful when you know you don't want to print some specific files. For example, if I don't want to see any introdution, then I do: 

    [cs15lwi23anb@ieng6-202]:berlitz1:442$ ls |grep -v Intro
    HandRHawaii.txt
    HandRHongKong.txt
    HandRIbiza.txt
    HandRIsrael.txt
    HandRIstanbul.txt
    HandRJamaica.txt
    HandRJerusalem.txt
    HandRLakeDistrict.txt
    HandRLasVegas.txt
    HandRLisbon.txt
    HandRLosAngeles.txt
    HandRMadeira.txt
    HandRMadrid.txt
    HandRMallorca.txt
    HistoryDublin.txt
    HistoryEdinburgh.txt
    HistoryEgypt.txt
    HistoryFWI.txt
    ...
    
If you don't want see any history, intro and HandR, then enter:

    [cs15lwi23anb@ieng6-202]:berlitz1:447$ ls |grep -v 'History\|Intro\|HandR'
    JungleMalaysia.txt
    WhatToDublin.txt
    WhatToEdinburgh.txt
    WhatToEgypt.txt
    WhatToFWI.txt
    WhatToFrance.txt
    WhatToGreek.txt
    WhatToHawaii.txt
    WhatToHongKong.txt
    WhatToIbiza.txt
    WhatToIndia.txt
    WhatToIsrael.txt
    WhatToIstanbul.txt
    WhatToItaly.txt
    ...
    
You can use \| to add more pattern in grep, so you can filter the files with more patterns.

The second command I found is this:

    $ grep "[a-zA-Z][characters][0-9]" file.txt

This command could be a useful command when you want to know how many punctuation marks in a files. We can use the -c to count how many punctuation it has in IntroJapan:

    [cs15lwi23anb@ieng6-202]:berlitz1:481$ grep -c "[-.,?!()]" IntroJapan.txt 
    202
    
Inside the bucket [], we can put any characters we want to find, and grep would found all of the sentences that contains at least one of those character.
and -c count the number of the characters we found. This is useful for people that might want to analyize the document, or have some extra information of the document.
Here is another example using -n:

    [cs15lwi23anb@ieng6-202]:berlitz1:482$ grep -n "[0123456789]" IntroJapan.txt 
    8:        300 km (186 miles) per hour. Its factories feature the latest
    36:        power has in the 1990s created a prolonged slump. A people so
    89:        Earth. Although it was established some 1,700 years ago, the main
    90:        shrine you’ll see today was erected in 1993. Unlike Christianity’s
    92:        permanence, this austere wooden structure is dismantled every 20 years
    105:        Not until a 20th-century Western architect, Frank Lloyd
    111:        withstand the powerful 1995 Hanshin earthquake that struck the Kobe
    122:        southwest. Together with more than 3,900 smaller islands from northeast
    144:        Japan’s 120 million inhabitants have to crowd the coastal plains and
    171:        even — until the postwar US occupation from 1945 to 1952 — foreign
    174:        totally free of social discrimination. The country’s 670,000 Koreans,
    
This command founds all the sentences that contains number and precede each matching line with a line number.
This command might be more useful because sometimes machine learning what to exact information from context, and if they want to filter out all the numerical information, this command could be helpful.

The third command is:

    grep -i "pattern" file.txt
    
 
This command ignore uppercase vs. lowercase, so when you want to found all the word but you want both uppercase and lowercase, you can do this command and it should return all the matches. For example:

    [cs15lwi23anb@ieng6-202]:berlitz1:501$ echo | grep -i -n "Japan" IntroJapan.txt
    6:        Japan and Its People
    14:        emerge. In many ways, Japan is not yet a truly modern country. Its
    18:        Japan is still trying to define its place in a world in
    21:        Japan. Truly, any examination of political, economic, and social issues
    25:        Where lies the real Japan? Simply put, it is all around you.
    26:        For Japan is truly a kaleidoscope of lifestyles and images, local
    33:        Japan — one of the world’s most intriguing countries.
    46:        “understand” Japan — if such a thing is indeed possible. After all, the
    47:        Japanese themselves are constantly analyzing their own nature. In fact,
    49:        Japaneseness”), books on which sell millions of copies each year and
    ...
    
So when we search the word "japan", it also return the result with "Japan". -n just slows which line the matching sentences in.

    [cs15lwi23anb@ieng6-202]:berlitz1:502$ echo | grep -i "APPLE" *
    HandRHawaii.txt:        <www.onlanai.com>. A 1923 pineapple plantation guesthouse for
    HandRJamaica.txt:        was once a pineapple plantation, with seaside freshwater pool and
    HistoryHawaii.txt:        Pineapples and War
    HistoryHawaii.txt:        business families were turning vast fields into pineapple plantations
    HistoryHawaii.txt:        After the war, sugarcane and pineapple production remained
    WhatToIbiza.txt:        •almejasbaby clamsmanzanaapple        
    WhatToIbiza.txt:        •cerdoporkpiñapineapple
    WhatToJamaica.txt:        of many tours — is Appleton Distillery, situated in rolling hills just
    WhatToJamaica.txt:        local consumption. Appleton Distillery went one step further and
    WhatToJamaica.txt:        pineapple plantation had fallen into decline before being transformed
    ...
    
Even if we type "APPLE" in uppercase, it also found both result. The echo | doesn't really do anything. * means all the file in current directory. -i ignores the uppercase and lowercase different.

The fourth command is:

    grep -r "pattern" *

This command searches files recursively, which means you can use this command outside of the final directory. This is useful when you don't know the location of the text you are going to search. And you want to search the whole working directory including their sub-directories. For example:

    [cs15lwi23anb@ieng6-202]:written_2:519$ grep -r "hello" *     
    travel_guides/berlitz1/WhereToHongKong.txt:        the local people smile “hello” and, if you’re lucky, point you to a      
    travel_guides/berlitz1/WhereToItaly.txt:        (or Ca’ Grande), while gondoliers claim Othello’s Desdemona lived in

We run this command in written_2 directory, by using -r, we can search the word all the way in travel_guides/berlitz1/WhereToHongKong.txt. It command could save programmer lots of time.
    
    [cs15lwi23anb@ieng6-202]:written_2:520$ grep -r -l "American" *
    non-fiction/OUP/Abernathy/ch1.txt
    non-fiction/OUP/Abernathy/ch14.txt
    non-fiction/OUP/Abernathy/ch15.txt
    non-fiction/OUP/Abernathy/ch2.txt
    non-fiction/OUP/Abernathy/ch3.txt
    non-fiction/OUP/Abernathy/ch8.txt
    non-fiction/OUP/Abernathy/ch9.txt
    non-fiction/OUP/Berk/CH4.txt
    non-fiction/OUP/Berk/ch1.txt
    non-fiction/OUP/Berk/ch2.txt
    non-fiction/OUP/Berk/ch7.txt
    non-fiction/OUP/Castro/chA.txt
    non-fiction/OUP/Castro/chB.txt
    non-fiction/OUP/Castro/chC.txt
    non-fiction/OUP/Castro/chL.txt
    non-fiction/OUP/Castro/chM.txt
    non-fiction/OUP/Castro/chN.txt
    non-fiction/OUP/Castro/chO.txt
    non-fiction/OUP/Castro/chP.txt
    non-fiction/OUP/Castro/chQ.txt
    non-fiction/OUP/Castro/chR.txt
    non-fiction/OUP/Castro/chV.txt
    non-fiction/OUP/Castro/chW.txt
    non-fiction/OUP/Castro/chY.txt
    ...
    
And you can easily location all the files that contains the target word by using -l to only output the file name. So this is a very powerful command to use.

Citation:
[1] https://en.wikibooks.org/wiki/Grep

[2] https://www.gnu.org/software/grep/manual/grep.html#Command_002dline-Options


