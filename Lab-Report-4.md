# Report 4

 - __Step 4: Log into ieng6__  

Screenshot:


```<up><enter>```  
The ssh command to connect to my ieng6 account was the first one in my command history
 - __Step 5: Clone your fork of the repository from your Github account (using the SSH URL)__  
```git clone <command-v>```  
I had the ssh path to the forked la7 repo previously copied (git@github.com:ThiagoDonato/lab7.git)
 - __Step 6: Run the tests, demonstrating that they fail__  
```cd lab7```  
```bash t<tab>```   
This goes into the lab7 directory that was just cloned, and runs the bash script test.sh by auto-completing the name since test.sh is the only file that starts with t inside lab7/
 - __Step 7: Edit the code file to fix the failing test__  
```vim L<tab>.<tab>```  
```x``` -> ```i``` -> ```2``` -> ```<esc>``` -> ```:wq```  
The first <tab> will autocomplete to ListExamples (Since there are two files that match: ListExamples.java and ListExamplesTest.java). Then after the point, the <tab> auto-completes with the java extensions since it narrowed down just to ListExamples.java. When I open the file on vim, my cursor will already be exactly where I need to make the change (on the 1 of index1). This is possible because since I practiced these steps before-hand, my computer remembers that I edited a file with the exact same path at that exact position. So, I can go straight away to the editing commands: x deletes the 1 in index1; i enters insert mode; 2 inserts the number 2 making it index2; <esc> return to vim normal mode: :wq writes the changes to the file and quits vim.
 - __Step 8: Run the tests, demonstrating that they now succeed__  
```bash t<tab>```  
This has the same function as what was explained in step 6. It runs the bash file test.sh
 - __Step 9: Commit and push the resulting change to your Github account (you can pick any commit message!)__  
```git add L<tab>```  
```git commit -m "'"```  
```git push origin```  
The first tab auto-completes to ListExamples.java since it tried to match the name to the files modified and ListExamples.java was the only one. Git add, adds the changes made to the staging area. git commit -m "'" captures a snapshot of the projects changes in the staging area. git push origin transfers the commited versions of my files to the remote repository. Note: origin is the conventional shorthand name of the url for the remote repository.







