# Part 1: StringServer

## Code for StringServer:  

<img width="779" alt="image" src="https://github.com/ThiagoDonato/cse15l-lab-reports/assets/130107055/639371e4-bcb6-4b06-a93d-cf8b73003d63">

## Screenshot1:  

<img width="506" alt="image" src="https://github.com/ThiagoDonato/cse15l-lab-reports/assets/130107055/89c956fc-af71-4f6b-910d-0e1d0f3d553e">

After the Server is alreay created (using the main method in StringServer, which calls the start() method), the url from this specific screen-shot is used as an argument to the method handleRequest(URI url). The relevant fields of the class are ```String output``` and ```int size```. These start off as ```""``` and ```0``` respectively. 
Methods run inside the handleRequest method are: getPath(), equals("/add message"), getQuery(), split("="), equals("s"), concat(String.format("%d. %s\n", size+1, parameters[1])).  
  
General Description of Methods and Arguments:  
When the handleRequest(URI url) method is run, output uses (size+1 = 1) and (parameters[1] = "CSE11") to become "1. CSE11\n". parameters[1] comes from a couple string modifications: 1. getQuery(add-message?s=CSE11) --> "s=CSE11"; 2. .split("=") creates parameters array == {"s", "CSE11"}; 3. parameters[1] = "CSE11". Notice that the "\n" is also added to output so that it skips to the next line in case any new strings get concatenated.  
After all this, size is increased by 1 (becomes 0+1=1). A value that didn't change after all this was the url, which was an URI object that, in a conceptual level, represented this: http://localhost:2300/add-message?s=CSE11. This didn't change because there was no other request made while this one was being processed. Also, there is no code in the method that changes this value.

## Screenshot2:  

<img width="449" alt="image" src="https://github.com/ThiagoDonato/cse15l-lab-reports/assets/130107055/5165bcfb-97ad-4285-bcd9-e1e93cf3b7bd">

In this screenshot, the method handleRequest(URI url) was called again with the url of this specific screen-shot as its argument. The relevant field of the class are ```String output``` and ```int size```. Before this request, these were ```"1. CSE11\n"``` and ```1``` respectively. In the exact same fashion that I described above, by concatenating the new request to its existing value, output ends being ```"1. CSE11\n2. Thiago\n"``` and size ends up being ```2```. During the duration of this request, the url value, which was an URI object, didn't change. In a conceptual level, it represented this: http://localhost:2300/add-message?s=Thiago. This didn't change because there was no other request made while this one was being processed. Also, there is no code in the method that changes this value.  
  
The methods that ran here were: getPath(), equals("/add message"), getQuery(), split("="), equals("s"), concat(String.format("%d. %s\n", size+1, parameters[1])).

# Part 2: 

<img width="432" alt="image" src="https://github.com/ThiagoDonato/cse15l-lab-reports/assets/130107055/2425733c-86c2-4a18-8b5e-9f563a8f59eb">

id_rsa is my private key, and id_rsa.pub is my public key. The location of both of them can be found by using ```pwd``` as such:

<img width="320" alt="image" src="https://github.com/ThiagoDonato/cse15l-lab-reports/assets/130107055/3bffecb7-560d-4ee2-bdf8-4d46b879f7a7">

Here is a terminal interaction where I log into ieng6 with my course-specific account without being asked for a password:

<img width="782" alt="image" src="https://github.com/ThiagoDonato/cse15l-lab-reports/assets/130107055/32ceea6e-1a43-4df0-9392-025b237b45e5">

# Part 3:

In Lab2/3 I learned how to create and store a key so I don't have to keep using my Passcode when connecting to a server using ssh. Also I learned two new commands: ```scp``` copies files or directories between a local and a remote system or between two remote systems. ```mkdir``` allows me to create directories. Now I also know that the terminal comes with its own instruction manual for certain commands, all I have to do is type ```man <command_name>```.





