**Lab Report 5**

In addition to the command options in lab report3, there are many more interesting command options in this complex operating system.
For example, you can use `less` to view a file in one page, in addition, there are more options for `less` to make it more useful.

`less -N <filename>` prints the line name for you:



      6         Oahu (Including Honolulu)
      7         Aston Waikiki Sunset $$$ 229 Paoakalani Avenue, Honolulu, HI
      8         96815; Tel. (808) 922-2700 or (800) 336-5599; fax (808) 922-8785;
      9         <www.aston-hotels.com>. One of Aston<E2><80><99>s many condominium resort
     10         properties, this modern high-rise has large rooms with complete
     11         kitchens. Lanais afford views of the Diamond Head end of Waikiki Beach.
     12         410 rooms.
     13         Halekulani $$$$ 2199 Kalia Road, Honolulu, HI 96815; Tel.
     14         (808) 923-2311 or (800) 367-2343; fax (808) 926-8004;
     15         <www.halekulani.com>. Very large rooms, most facing the ocean,
     16         and luxurious bathrooms with robes, make this a <E2><80><9C>House Befitting
     17         Heaven,<E2><80><9D> the meaning of its Hawaiian name. With plenty of beachfront, a
     18         top French restaurant (La Mer), and the serene House Without A Key
     19         outdoor lounge for sunset drinks, Halekulani is a complete resort. 454
     20         rooms.

If you want to find a specific pattern in this text, you can type `/<pattern>` to search it, for example, if I type `/Honolulu`, it will automaticlly jump to line that this pattern first appears and highlight the pattern.  

      6         Oahu (Including **Honolulu**)
      7         Aston Waikiki Sunset $$$ 229 Paoakalani Avenue, **Honolulu**, HI
      8         96815; Tel. (808) 922-2700 or (800) 336-5599; fax (808) 922-8785;
      9         <www.aston-hotels.com>. One of Aston<E2><80><99>s many condominium resort
     10         properties, this modern high-rise has large rooms with complete
     11         kitchens. Lanais afford views of the Diamond Head end of Waikiki Beach.
     12         410 rooms.
     
     
There are also some interesting options for the `echo` command that are really useful, for example, `-p`: This option prompts the user to enter a value for the output string. This can be useful when you want to ask the user for input in a script.

     $ echo -p "Please enter your name: "
     Please enter your name: John
     John
     
Notice that the user is prompted to enter their name and the input is printed to the console.

`-e`: This option enables the interpretation of backslash escape sequences in the output string.
Example:

    $ echo -e "Hello\tWorld\nHow are you?"
    Hello   World
    How are you?
    
Notice that the `\t` escape sequence is interpreted as a tab character and `\n` as a newline character.

Here are some other interesting command I found from internet.

`wget [option]... [URL]...` is also a useful command to download a file from website

    [cs15lwi23anb@ieng6-203]:berlitz1:532$ wget https://github.com/jwu123d/cse15l-lab-reports/blob/main/Lab%20Report3.md
    --2023-03-13 18:50:54--  https://github.com/jwu123d/cse15l-lab-reports/blob/main/Lab%20Report3.md
    Resolving github.com (github.com)... 140.82.112.3
    Connecting to github.com (github.com)|140.82.112.3|:443... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: unspecified [text/html]
    Saving to: 'Lab Report3.md'

    [ <=>                                                                                                                                                 ] 162,687         887KB/s   in 0.2s   

    2023-03-13 18:50:55 (887 KB/s) - 'Lab Report3.md' saved [162687]
    
`history` would show all the command we used before.
        
        507  ls
        508  less written_2
        509  more written_2/
        510  cd written_2/
        511  ls
        512  cd travel_guides/
        513  ls
        514  cd berlitz1
        515  ls
        516  less HandRHawaii.txt
        517  more HandRHawaii.txt
        518  ls

In conclusion, there are many interesting commands in this linux system, it will make our operation of the computer more convenient, and we will learn more in the future more work experience.

