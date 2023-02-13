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

The third command is 


Citation:
[1] https://en.wikibooks.org/wiki/Grep
