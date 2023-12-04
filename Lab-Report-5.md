# Part 1: Scenario - Finding the car model with the highest price from a CSV file 

The video shown in Quiz9 inspired this idea: https://www.youtube.com/watch?v=dogmDTc6so8  
This video is of Dev Gulati showing how to extract and apply commands to a genomics dataset. The commands I came up with are similar to the ones he use.

## Important Context - Task instructions
Prompt to student: The file ```cars.csv``` contains information about the cars stored in a general car dealership here in San Diego. They just hired you to write some code that looks at their data and gives them the model name of the most expensive car. You may assume ```cars.csv``` is stored in their system's home directory and all your code can be stored in the same directory. Download the ```cars.csv``` file from our github repository.
1. Use a bash script to access the CSV file and extract just the price information from the 'Price' column (be careful to not include the column header). Save this in a file called ```onlyValues.txt```. Then, in Java, open this file, loop through the prices and find the most expensive one. Output this information to the terminal.
2. Adding to your bash script: compile and run the Java code you wrote. Use the extracted highest price information to find the corresponding model name. Hint: use ```grep``` to find the row that contains that price (You may assume every car has a unique price).
3. Output to the terminal the price and the model of the most expensive car
4. Here is an overview of the information flow you should have: ```cars.csv``` --> bash script --> ```onlyValues.txt``` --> Java code --> highest price --> bash script --> car model with highest price

## 1. Original post from a student showing a symptom and a description of a guess at the bug/some sense of what the failure-inducing input is
Hi CSE15L staff, I finished the most recent assignment, but when I run my code I get an bug. Here is the symptom I observed:  
<img width="702" alt="image" src="https://github.com/ThiagoDonato/cse15l-lab-reports/assets/130107055/6b1bb83b-5645-4d66-b893-fe2cf91e9f6c">  
This seems to indicate that the error is in my Java program. The only input to that program is the file ```onlyValues.txt```. I think that can be the failure-inducing input. So maybe my bash script didn't properly process the ```cars.csv``` file. It is worth noting that I was having some trouble downloading the CSV file from you guys' repo, so I just copied the contents line by line into my own computer.

## 2. A response from a TA asking a leading question or suggesting a command to try
Hello, I like your hypothesis that the file ```onlyValues.txt``` may be the failure-inducing input. Still, you are correct that it is generated from your bash script, meaning we should also look at that.  
Lets review the information flow of the assignment: ```cars.csv``` --> bash script --> ```onlyValues.txt``` --> Java code --> highest price ... To really understand what is going on, we might need to take a look at your ```cars.csv``` file **before** entering the bash script and the ```onlyValues.txt``` file **after** the script ran. This is especially important since you said you had to copy the contents of the CSV value yourself.  
To do that, I suggest using the following commands:  
1. ```cat cars.csv```   #Use this to see the entire file
2. ```head -n 1 cars.csv | cut -d ',' -f 1-```   #Use this to see all the columns in the file
3. ```cat cars.csv | cut -d ',' -f 7```   #Use this to see just the Price column in the CSV file
4. ```bash extract-price.sh```   #Run your bash script to process the csv file and create the onlyValues.txt file
5. ```cat onlyValues.txt```   #Use this to see what you have in the onlyValues.txt file

## 3. Another screenshot/terminal output showing what information the student got from trying that, and a clear description of what the bug is.
Trying the command ```cat cars.csv``` I got the following output:  
<img width="476" alt="image" src="https://github.com/ThiagoDonato/cse15l-lab-reports/assets/130107055/09b5b332-ec7b-457b-8f9e-0656e69d2752">  
This seemed pretty correct and I didn't find anything wrong here.  

Trying the commands ```head -n 1 cars.csv | cut -d ',' -f 1-``` and ```cat cars.csv | cut -d ',' -f 7```
<img width="665" alt="image" src="https://github.com/ThiagoDonato/cse15l-lab-reports/assets/130107055/cd369414-b032-4140-b799-0c4fa0d25de1">  
The 8 columns seem pretty resonable, but when I ran the command to get just the 'Price' one, the last row seemed off. The 'Green' value should be part of the Color column.  
  
Trying the command ```cat onlyValues.txt``` after running my bash script:
<img width="521" alt="image" src="https://github.com/ThiagoDonato/cse15l-lab-reports/assets/130107055/660f64da-ed27-4db4-a758-11f6b21ba18a">  
This shows me that my bash script isn't actually doing anything wrong since it is extracting only the values of the Price column. The ```cars.csv``` file is the one that contains the error!  

**Bug description**: I went back and looked at the output of ```cat cars.csv```. Now, paying close attention to the last row where that ```90000 Green``` value was stored. I noticed how all other prices were stored using a comma between Price and Color. I must've copied the file wrong and didn't notice that I needed to add a comma value. I guess that explains the bug later in the Java program. Since my code parses each value in the line to an Integer, it wasn't able to parse the value ```90000 Green```, throwing an ```NumberFormatException```. I will use the ```vim``` command to edit the ```cars.csv``` file and add that sneaky comma!

## 4. All the information about the setup
1. ### The file & directory structure needed
All the files are in the Home Directory, so the set-up you need to run the program is: 
```
   ~/
    extract-price.sh
    HighestPriceFinder.java
    cars.csv
```
To run the code, the people from the car dealership just have to type ```bash extract-price.sh```. Then, the file structure will be:
```
   ~/
    extract-price.sh
    HighestPriceFinder.java
    HighestPriceFinder.class
    cars.csv
    onlyValues.txt
```
3. ### The contents of each file before fixing the bug
**Contents of cars.csv before:**  
<img width="447" alt="image" src="https://github.com/ThiagoDonato/cse15l-lab-reports/assets/130107055/62ef9c2d-128f-4173-b3b2-0bcdb7eeb642">  

**Contents of extract-price.sh:**  
<img width="600" alt="image" src="https://github.com/ThiagoDonato/cse15l-lab-reports/assets/130107055/03895334-d26b-4f2e-90d8-bf991c8fb064">
  
**Contents of HighestPriceFinder.java:**  
<img width="523" alt="image" src="https://github.com/ThiagoDonato/cse15l-lab-reports/assets/130107055/8e9501ef-4c51-464d-8d4c-f31f8bcefbc8">

4. ### The full command line (or lines) you ran to trigger the bug
To trigger the bug, I just ran the bash file ```extract-price.sh``` which is the master file than calls on everything else:  
<img width="695" alt="image" src="https://github.com/ThiagoDonato/cse15l-lab-reports/assets/130107055/a683a1b6-8c06-480d-b3dd-6ba277d3970f">

5. ### A description of what to edit to fix the bug
To edit the bug, you will need to make changes to ```cars.csv```. This can be done by using the command ```vim cars.csv```. Once inside vim, do:  
```10j```-> ```$``` -> ```5h``` -> ```x``` -> ```i``` -> ```,``` -> ```<ESC>``` -> ```:wq```  
This will go to the line where there should be a delimiting comma, delete the white space, insert the comma, then save.  
After doing this, the bash script should run fine and the output should be correct:  
<img width="546" alt="image" src="https://github.com/ThiagoDonato/cse15l-lab-reports/assets/130107055/c2af84c8-ef0a-4abc-b82e-075718705219">

# Part 2 - Reflection  
One thing I learned this quarter was with my Tutor from Lab: Alon. With the 'question of the week' always came some small talk and eventually I got to know a little bit about him. He told me he is a transfer and that he interned at Visa last quarter. Since I am looking for internships, I asked for advice and he recommended RippleMatch, a platform where you are matched with job openings and it increases your chance of getting a response back. I started using the app, got matched with MongoDB, applied for their SWE internship and even got a response back!  

PS: To the grader of this Lab Report: I spent a lot of hours developing the code and testing the idea for this student-TA scene. I was worried that my bug wouldn't be so creative so I made a 
problem from scratch. I really need full marks on this lab to get an A and I tried my best. I hope you can be lenient in case I missed a detail or if you didn't find my approach creative enough. Thanks a lot in advance!
