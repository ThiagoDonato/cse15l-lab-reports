#Part 1: StringServer

## Code for StringServer:  

<img width="779" alt="image" src="https://github.com/ThiagoDonato/cse15l-lab-reports/assets/130107055/639371e4-bcb6-4b06-a93d-cf8b73003d63">

## Screenshot1:  

<img width="506" alt="image" src="https://github.com/ThiagoDonato/cse15l-lab-reports/assets/130107055/89c956fc-af71-4f6b-910d-0e1d0f3d553e">

After the Server is alreay created (using the main method in StringServer, which calls the start() method), the url from this specific screen-shot is used as an argument to the method handleRequest(URI url). The relevant fields of the class are ```String output``` and ```int size```. These start off as ```""``` and ```0``` respectively. So, after this specific request, when the handleRequest method is run, output uses (size+1 = 1) and (parameters[1] = "CSE11") to becomes "1. CSE11\n". parameters[1] comes from a couple string modifications: 1. getQuery(add-message?s=CSE11) --> "s=CSE11"; 2. .split("=") creates parameters array == {"s", "CSE11"}; 3. parameters[1] = "CSE11". Notice that the "\n" is also added to output so that it skips to the next line in case any new strings get concatenated. After all this, size is increased by 1 (becomes 0+1=1). A value that didn't change after all this was the url, which was an URI object that, in a conceptual level, represented this: http://localhost:2300/add-message?s=CSE11. This didn't change because there was no other request made while this one was being processed. Also, there is no code in the method that changes this value.

## Screenshot2:  

<img width="449" alt="image" src="https://github.com/ThiagoDonato/cse15l-lab-reports/assets/130107055/5165bcfb-97ad-4285-bcd9-e1e93cf3b7bd">

In this screenshot, the method handleRequest(URI url) was called again. The relevant field of the class are ```String output``` and ```int size```. These are now ```"1. CSE11\n"``` and ```1``` respectively. In the exact same fashion that I described above, by concatenating the new request to its existing value, output ends up with value ```"1. CSE11\n2. Thiago\n"``` and size ends up being ```2```. 
