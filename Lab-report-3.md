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



