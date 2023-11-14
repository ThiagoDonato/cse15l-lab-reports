# CSE15L: Lab Report 4 - Thiago

 - ## __Step 4: Log into ieng6__  
<img width="771" alt="image" src="https://github.com/ThiagoDonato/cse15l-lab-reports/assets/130107055/7782505c-1efc-4be0-83cc-15703b5f97c0">

```<up><enter>```  
The ssh command to connect to my ieng6 account was the first one in my command history
 - ## __Step 5: Clone your fork of the repository from your Github account (using the SSH URL)__
<img width="555" alt="image" src="https://github.com/ThiagoDonato/cse15l-lab-reports/assets/130107055/8138998f-f675-4988-8ac5-729b05d29466">

```git clone <command-v>```  
I had the ssh path to the forked lab7 repo previously copied (git@github.com:ThiagoDonato/lab7.git)
 - ## __Step 6: Run the tests, demonstrating that they fail__
<img width="595" alt="image" src="https://github.com/ThiagoDonato/cse15l-lab-reports/assets/130107055/48c5412b-81a5-45da-98b1-423aa70e7b69">

```cd lab7```  
```bash t<tab>```   
This goes into the lab7 directory that was just cloned, and runs the bash script test.sh by auto-completing the name since test.sh is the only file that starts with t inside lab7/
 - ## __Step 7: Edit the code file to fix the failing test__  
Overall terminal output of fixing ListExamples.java<br>: 
<img width="396" alt="image" src="https://github.com/ThiagoDonato/cse15l-lab-reports/assets/130107055/82d2da65-c814-4f53-9d13-72abb4a72fd5"><br> 
Cursor location right after entering vim:<br> 
<img width="276" alt="image" src="https://github.com/ThiagoDonato/cse15l-lab-reports/assets/130107055/d7c2f455-ab34-40ed-adb6-3054e9f98a53"><br> 
After doing ```x```:<br> 
<img width="270" alt="image" src="https://github.com/ThiagoDonato/cse15l-lab-reports/assets/130107055/584a5226-71ab-4aca-9d0f-78183150ad5c"><br> 
After doing ```i``` and ```2```:<br> 
<img width="279" alt="image" src="https://github.com/ThiagoDonato/cse15l-lab-reports/assets/130107055/1ed31ff5-fc36-4365-92f3-1635e06713ba">

```vim L<tab>.<tab>```  
```x``` -> ```i``` -> ```2``` -> ```<esc>``` -> ```:wq```  
The first ```<tab>``` will autocomplete to ListExamples (Since there are two files that match: ListExamples.java and ListExamplesTest.java). Then after the point, the ```<tab>``` auto-completes with the java extensions since it narrowed down just to ListExamples.java. When I open the file on vim, my cursor will already be exactly where I need to make the change (on the 1 of index1). This is possible because since I practiced these steps before-hand, my computer remembers that I edited a file with the exact same path at that exact position and left my cursor there. So, I can go straight away to the editing commands: ```x``` deletes the 1 in index1; ```i``` enters insert mode; ```2``` inserts the number 2 making it index2; ```<esc>``` return to vim normal mode: ```:wq``` writes the changes to the file and quits vim.
 - ## __Step 8: Run the tests, demonstrating that they now succeed__
<img width="393" alt="image" src="https://github.com/ThiagoDonato/cse15l-lab-reports/assets/130107055/84ab16a2-4a59-4e69-b65a-eeb68da27492">

```bash t<tab>```  
This has the same function as what was explained in step 6. It runs the bash file test.sh
 - ## __Step 9: Commit and push the resulting change to your Github account (you can pick any commit message!)__
<img width="496" alt="image" src="https://github.com/ThiagoDonato/cse15l-lab-reports/assets/130107055/80e943df-d0ca-41bf-957a-7cfded9c60c6">

```git add L<tab>```  
```git commit -m "'"```  
```git push origin```  
The first ```<tab>``` auto-completes to ListExamples.java since it tried to match the name to the files modified and ListExamples.java was the only one I changed. ```git add``` adds the changes made to the staging area. ```git commit -m "'"``` captures a snapshot of the projects changes in the staging area with a message ```'```. I chose this message because it is the key closest to ```"``` that would allow me quickly write a non-empty message. git push origin transfers the commited versions of my files to the remote repository. Note: origin is the conventional shorthand name of the url for the remote repository.








