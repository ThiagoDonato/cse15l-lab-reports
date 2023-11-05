# Part 1 - Bugs
__Instructions:__
- __A failure-inducing input for the buggy program, as a JUnit test and any associated code (write it as a code block in Markdown)__
```
@Test
public void test1Reversed() {
  int[] failureInducingInput = {1,2,3,4,5};
  int[] expected = {5,4,3,2,1};
  assertArrayEquals(expected, ArrayExamples.reversed(failureInducingInput));
}
```
- __An input that doesn’t induce a failure, as a JUnit test and any associated code (write it as a code block in Markdown)__  
```
@Test
public void test2Reversed() {
  int[] notFailureInducingInput = {0};
  int[] expected = {0};
  assertArrayEquals(expected, ArrayExamples.reversed(notFailureInducingInput));
}
```
- __The symptom, as the output of running the tests (provide it as a screenshot of running JUnit with at least the two inputs above)__
<img width="685" alt="image" src="https://github.com/ThiagoDonato/cse15l-lab-reports/assets/130107055/a21af24b-59a9-4b42-9f50-132ea90f403c">

- __The bug, as the before-and-after code change required to fix it (as two code blocks in Markdown)__  

The code before:
```
//Before
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```
The code after:
```
//After
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
  }

```
This fix addresses the issue because now the ```newArray``` is the one being modified, using the values of the input array ```arr```. Also, now  ```newArray``` is being returned.

# Part 2 - Researching Commands: Chose ```grep```

## Option -i: Prints lines with matching criteria while ignores casing (Upper/Lowecase)
- Source: https://docs.rackspace.com/docs/use-the-linux-grep-command  

__Current working directory = ~/techincal__  
example 1: Looking for words matching upper or lowercase variations of 'united states'. Without usint -i, nothing shows up  
COMMAND:
```
cd 911report
grep -i "united states" chapter-1.txt
```
OUTPUT:
```
  Tuesday, September 11, 2001, dawned temperate and nearly cloudless in the eastern United States. Millions of men and women readied themselves for work. Some made their way to the Twin Towers, the signature structures of the World Trade Center complex in New York City. Others went to Arlington, Virginia, to the Pentagon. Across the Potomac River, the United States Congress was back in session. At the other end of Pennsylvania Avenue, people began to line up for a White House tour. In Sarasota, Florida, President George W. Bush went for an early morning run.
    At some point between 9:16 and 9:26, Barbara Olson called her husband, Ted Olson, the solicitor general of the United States. She reported that the flight had been hijacked, and the hijackers had knives and box cutters. She further indicated that the hijackers were not aware of her phone call, and that they had put all the passengers in the back of the plane. About a minute into the conversation, the call was cut off. Solicitor General Olson tried unsuccessfully to reach Attorney General John Ashcroft.
    No one at the FAA or the airlines that day had ever dealt with multiple hijackings. Such a plot had not been carried out anywhere in the world in more than 30 years, and never in the United States. As news of the hijackings filtered through the FAA and the airlines, it does not seem to have occurred to their leadership that they needed to alert other aircraft in the air that they too might be at risk.
NORAD Mission and Structure. NORAD is a binational command established in 1958 between the United States and Canada. Its mission was, and is, to defend the airspace of North America and protect the continent. That mission does not distinguish between internal and external threats; but because NORAD was created to counter the Soviet threat, it came to define its job as defending against external attacks.
    The threat of Soviet bombers diminished significantly as the Cold War ended, and the number of NORAD alert sites was reduced from its Cold War high of 26. Some within the Pentagon argued in the 1990s that the alert sites should be eliminated entirely. In an effort to preserve their mission, members of the air defense community advocated the importance of air sovereignty against emerging "asymmetric threats" to the United States: drug smuggling, "non-state and state-sponsored terrorists," and the proliferation of weapons of mass destruction and ballistic missile technology.
    Prior to 9/11, it was understood that an order to shoot down a commercial aircraft would have to be issued by the National Command Authority (a phrase used to describe the president and secretary of defense). Exercise planners also assumed that the aircraft would originate from outside the United States, allowing time to identify the target and scramble interceptors. The threat of terrorists hijacking commercial airliners within the United States-and using them as guided missiles-was not recognized by NORAD before 9/11. Notwithstanding the identification of these emerging threats, by 9/11 there were only seven alert sites left in the United States, each with two fighter aircraft on alert. This led some NORAD commanders to worry that NORAD was not postured adequately to protect the United States.
    In the United States, NORAD is divided into three sectors. On 9/11, all the hijacked aircraft were in NORAD's Northeast Air Defense Sector (also known as NEADS), which is based in Rome, New York. That morning NEADS could call on two alert sites, each with one pair of ready fighters: Otis Air National Guard Base in Cape Cod, Massachusetts, and Langley Air Force Base in Hampton, Virginia.
    The details of what happened on the morning of September 11 are complex, but they play out a simple theme. NORAD and the FAA were unprepared for the type of attacks launched against the United States on September 11, 2001. They struggled, under difficult circumstances, to improvise a homeland defense against an unprecedented challenge they had never before encountered and had never trained to meet.

...
```
example 2: Recursively searches for variations (uppercase or lowercase) of fire in all files inside ~/technical/government  
COMMAND
```
cd government
grep -ir fire
```
OUTPUT:
```
./About_LSC/commission_report.txt:to their home country. Employers may improperly fire and deport
./About_LSC/commission_report.txt:will be immediately fired for any violation of the rules. Id. at
./About_LSC/State_Planning_Report.txt:addressed. The goal is to light a fire without burning down the
./Env_Prot_Agen/multi102902.txt:2-1. Gas path for coal-fired boiler with FGD
./Env_Prot_Agen/multi102902.txt:3-1. Gas path for coal-fired boiler with SCR, ESP, and
./Env_Prot_Agen/multi102902.txt:4-1. Gas path for coal-fired boiler with SCR, ACI, and ESP
./Env_Prot_Agen/multi102902.txt:4-2. Gas path for coal-fired boiler with SCR, ACI, ESP, and
./Env_Prot_Agen/multi102902.txt:6-5. SCR installations on coal-fired plants in
./Env_Prot_Agen/multi102902.txt:6-7. SCR Catalyst Capacity for Coal-fired Boilers
./Env_Prot_Agen/multi102902.txt:from the coal-fired electricity-generating segment of the electric
./Env_Prot_Agen/multi102902.txt:coal-fired electricity generating power plants. Strategies enabling
./Env_Prot_Agen/multi102902.txt:mercury emissions from coal-fired power plants is appropriate and
./Env_Prot_Agen/multi102902.txt:multiple pollutants from coal-fired power plants in the United
./Env_Prot_Agen/multi102902.txt:systems to remove SO2 are examined for existing coal-fired electric
./Env_Prot_Agen/multi102902.txt:Figure 2-1. Gas path for coal-fired boiler with FGD.
./Env_Prot_Agen/multi102902.txt:scrubber capacity built on coal-fired power plants in the US. Over
./Env_Prot_Agen/multi102902.txt:In this chapter, retrofit of SCR will be assessed for coal-fired
./Env_Prot_Agen/multi102902.txt:Figure 3-1. Gas path for coal-fired boiler with SCR, ESP, and
./Env_Prot_Agen/multi102902.txt:catalyst for each MWe of coal-fired boiler capacity.18,21,22 For
./Env_Prot_Agen/multi102902.txt:plate catalyst,19 or about 1.33 m3 per MWe. This unit fires 2.5
...
```
## Option -l: Prints filenames only
- Source: https://docs.rackspace.com/docs/use-the-linux-grep-command  

__Current working directory = ~/techincal__  
example 1: Lists the files matching the pattern rr* in the working directory that contains the word 'this'.  
COMMAND
```
cd biomed
grep -l this rr*

```
OUTPUT:
```
rr166.txt
rr167.txt
rr171.txt
rr172.txt
rr191.txt
rr196.txt
rr37.txt
rr73.txt
rr74.txt
```
example 2: Searches recursively in the current working directory for files that contain the word acl  
COMMAND
```
cd biomed
grep -rl acl

```
OUTPUT:
```
./gb-2002-4-1-r2.txt
./1471-2202-2-9.txt
./1471-2202-2-8.txt
./1471-2202-4-11.txt
./1471-2415-3-4.txt
./1471-2148-1-8.txt
./ar297.txt
./bcr631.txt
./1471-2148-2-17.txt
./gb-2002-3-9-research0044.txt
./1475-925X-2-10.txt
./1471-2105-4-26.txt
./cc105.txt
./1471-2350-3-7.txt
./bcr285.txt
./gb-2002-3-6-software0001.txt
./gb-2002-3-12-research0078.txt
./gb-2003-4-2-r14.txt
./1471-213X-1-6.txt
./1472-6920-2-3.txt
./gb-2002-3-11-research0060.txt
./1471-213X-3-7.txt
./1471-2164-4-19.txt
./1471-2199-3-12.txt
./1471-2210-2-6.txt
./1472-6874-2-13.txt
./1471-2202-2-19.txt
./1471-2121-2-11.txt
./1471-2091-3-14.txt
./1471-2105-3-34.txt
./gb-2002-3-12-research0088.txt
./1471-2180-1-34.txt
./1471-2164-3-7.txt
./cvm-2-6-278.txt
./1471-2091-3-4.txt
./1471-2105-3-6.txt
./1472-6947-1-6.txt
./1468-6708-3-3.txt
./1471-2202-2-5.txt
./1471-2210-1-2.txt
./1471-2105-3-4.txt
./1471-213X-1-11.txt
```
## Option -v: Prints lines not matching criteria (inverse search)
- Source: https://docs.rackspace.com/docs/use-the-linux-grep-command  

__Current working directory = ~/techincal__  
example 1: Searches for lines that don't have a ',' in the file 1471-213X-1-11.txt  
COMMAND
```
cd biomed
grep -v , 1471-213X-1-11.txt
```
OUTPUT:
```
 Background
        understanding of the role of mesenchymal cells and their
        products in regulation of proliferation and differentiation
        fibroblasts 
        leukocytes can bring growth- activating substances to
        lymphocytes were shown to promote tissue growth and
        regeneration (reviewed in Ref. [ 12]). In spite of these
        mesenchymal and tissue-specific cells is still in its
        beginning. While a lot of work has been done on the role of
        various growth factors and cytokines produced by
        mesenchymal cells on the cell cycle and death 
        little is known about interactions between mesenchymal and
        tissue-specific cells 
        in vivo. 
...
```
example 2: Searches for lines in chapter-10.txt that don't contain the word 'the'  
COMMAND
```
cd 911report
grep -v the chapter-10.txt
```
OUTPUT:
```
      
            WARTIME
                of unnerving false alarms, Air Force One flew to Barksdale Air Force Base in
                White House Situation Room that morning.
            
                advisers, and Vice President Cheney were strongly advising against it. President
                Bush reluctantly acceded to this advice and, at about 10:10, Air Force One changed
                course and began heading due west. The immediate objective was to find a safe
                Barksdale Air Force Base as an appropriate interim destination.
            
...
```
## Option -c: Count that how many lines matches the given pattern/string
- Source: thegeekstuff.com/2009/03/15-practical-unix-grep-command-examples/  

__Current working directory = ~/techincal__  
example 1: Recursively counts the number of lines with the word 'death' in all the files inside the current working directory.  
COMMAND
```
cd 911report
grep -rc death 
```
OUTPUT:
```
./chapter-13.4.txt:2
./chapter-13.5.txt:6
./chapter-13.1.txt:0
./chapter-13.2.txt:0
./chapter-13.3.txt:0
./chapter-3.txt:4
./chapter-2.txt:3
./chapter-1.txt:0
./chapter-5.txt:0
./chapter-6.txt:1
./chapter-7.txt:1
./chapter-9.txt:2
./chapter-8.txt:0
./preface.txt:0
./chapter-12.txt:3
./chapter-10.txt:1
./chapter-11.txt:0
```
example 2: Recursively counts the number of lines that doesn't contain a full stop '.' in all the files inside 911report.  
COMMAND:
```
cd 911report
grep -vcr .
```
OUTPUT:
```
./chapter-13.4.txt:1
./chapter-13.5.txt:1
./chapter-13.1.txt:1
./chapter-13.2.txt:1
./chapter-13.3.txt:1
./chapter-3.txt:1
./chapter-2.txt:1
./chapter-1.txt:362
./chapter-5.txt:1
./chapter-6.txt:1
./chapter-7.txt:1
./chapter-9.txt:1
./chapter-8.txt:1
./preface.txt:1
./chapter-12.txt:1
./chapter-10.txt:1
./chapter-11.txt:1
```




