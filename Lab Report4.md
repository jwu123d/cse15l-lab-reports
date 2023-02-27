**The Tournament: CLDQ**

Tasks: 
1. Setup Delete any existing forks of the repository you have on your account
2. Setup Fork the repository
3. The real deal Start the timer!
4. Log into ieng6
5. Clone your fork of the repository from your Github account
6. Run the tests, demonstrating that they fail
7. Edit the code file to fix the failing test
8. Run the tests, demonstrating that they now succeed
9. Commit and push the resulting change to your Github account (you can pick any commit message!)


First, to set up the race, we delete the existing fork of the repository.

![image](https://user-images.githubusercontent.com/71479254/221697296-a0593139-de25-45e5-910d-155044a1ce1b.png)

as well as delete the existing lab7 file on the remote ieng6:

![image](https://user-images.githubusercontent.com/71479254/221697690-279765f5-d8c3-447d-8f15-f39d0682ce6f.png)

Second, we make a new fork:

![image](https://user-images.githubusercontent.com/71479254/221697968-a8f7fc16-cd35-4ec5-b1de-5749713f6049.png)

Third, here the timer already: 

![image](https://user-images.githubusercontent.com/71479254/221698242-2f7809ee-9c74-4ef7-97a2-5c571273b857.png)

Fourth, we click `<up>` once to found `ssh cs15lwi23anb@ieng6.ucsd.edu`, and press `<enter>`

![image](https://user-images.githubusercontent.com/71479254/221699468-c683674d-5d4f-4b3a-8830-7a1f06d871b6.png)

Fifth, since we can copy commands in advance, we copied this command sequences: 

![image](https://user-images.githubusercontent.com/71479254/221699711-d9866702-1b91-4efb-830f-9b58e39e2660.png)

Which is we clone the lab7 from github, then go to lab7 directory, run the test, and open vim:
we paste it into the terminal by `<rightclick>`:

![image](https://user-images.githubusercontent.com/71479254/221700221-a466e0c5-da62-492a-8e64-e94796610138.png)
this step also finishes step six.

Seventh, we have vim ListExamples.java already in the command line because we pasted the sequence, we hit `<enter>` to open vim:
then we click `<up><up><up><up><up><up>` to go to line 43 in the file, and hit `<left><left><left><left><left><left><left><left><left><left><left><left>` to get the cursor after `index1`
we hit `i` to open edit mode, `backsaace` to delete the 1, hit `2` to change index1 to index2, hit `esc` to exit edit mode, hit `:wq` to quit vim and write to the file.

![image](https://user-images.githubusercontent.com/71479254/221701766-7e0a27e8-6fd4-4ee0-90d5-8245615df75e.png)

Lastly, we copy the rest of the command sequence from outside file using `ctrl+c` 

![image](https://user-images.githubusercontent.com/71479254/221701984-2a33adea-9c3a-4ba1-91e8-d444a35f2046.png)

and paste it into the terminal using `<rightclick>` and finishes the whole task:

![image](https://user-images.githubusercontent.com/71479254/221702696-dabd87a8-1c09-4675-8087-2779be12a1bb.png)

**Conclusion: **

It can be done even more faster if I use different command that edit the file directly using command line, instead of open vim and move the cursor to the index1 and edit it. 
It costs the most time to do it because vim needs more command inside to access and exit. But I didn't have time to figure out how to edit the file from outside the file using command in lab, so this is what I have when I was doing the tournament.

