![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/58637195-4e0b-4aab-a52e-e95adbf530ed)# Lab Report 5 - Putting it All Together

## Part 1 - Debugging Scenario

**Student**
 Hi, my test case for finding all of the "a"s in a list isn't working.There is only one "a", but it says there are 2

```java
@Test
public void testFilter2() {
  List<String> s1 = Arrays.asList("a", "b", "c");
  List<String> s2 = Arrays.asList("d", "a", "a");

  List<String> expect1 = Arrays.asList("a");
  List<String> expect2 = Arrays.asList("a", "a");

  List<String> result1 = ListEx.filter(s1, new IsA());
  List<String> result2 = ListEx.filter(s2, new IsA());

   assertEquals(expect1, result1);
   assertEquals(expect2, result2);
}
```
I ran my `test.sh` file
```bash
javac -g -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples
```
This is the result
```
JUnit version 4.13.2
.E.
Time: 0.067
There was 1 failure:
1) testFilter2(TestListExamples)
java.lang.AssertionError: expected:<[a]> but was:<[a, a]>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at TestListExamples.testFilter2(TestListExamples.java:39)

FAILURES!!!
Tests run: 2,  Failures: 1
```


<br>

**TA**
Instead of running it with the java command, try it with the java debugger so you can see exactly what went wrong
```
jdb -classpath .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples
```
After that, type `> stop at TestListExamples:<LINE NUMBER>` (substitute <LINE NUMBER> for the number of the line with the failing assert),
then, use `> run` to run the program until that line.

From there, you can use `print <VARIABLE>` to see the value of the variables at that point. You can also use the stop command to stop at different lines and compare the results. 


**Student**
I see! `result1` is being updated when `result2` is created, it must be an issue with the creation of new objects in my method
![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/125cfbaf-3993-4bac-bb2e-f1fd7db23c59)
![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/c94c2106-460e-43e7-b746-935e2103596e)
Thank you so much :)

I changed this:
![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/f553904d-fd40-4e49-94a6-829b862c5bcf)


To this:
![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/fa2978d2-a541-4423-b7a9-f43207982ae9)


And it worked!
![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/6bbc4f89-fca1-4c3f-a95e-df238752f494)


<br>

---
### File structure
![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/3af779a5-70fc-4a73-bb4b-86ebe2b5caf2)
![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/949a5935-ba45-4426-9411-1767fd20d9e6)


### Files

**ListExamples.java**
Before
![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/f553904d-fd40-4e49-94a6-829b862c5bcf)
After
![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/fa2978d2-a541-4423-b7a9-f43207982ae9)

**TestListExamples.java**
![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/e02a056a-6cf3-4ae3-8229-fd78989c917f)

**test.sh**
![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/4156f9bc-e4f9-4eb4-8268-f29b608cd662)

Files in `lib` are the default `.jar` files for JUnit. `.class` files are resultant from running `test.sh`


### Bug

This induced the bug when the program was run using `java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples`: 
![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/33a4f4c4-7877-4525-bb57-5396f474fb93)
The ArrayList `result` was part of the class, and not being created during the method. Therefore, the method didn't return a reference
to a new ArrayList, but to `result`. When the line for `result2` was run, it updated `result`, subsequently updating `result1`. I fixed it by creating and returning a new object when the method is called


## Part 2 – Reflection
Something cool I learned was using Vim to edit files directly from the command line. 
I had heard about it before, and tried to use it on ieng6 and on my own laptop, but it 
felt very clunky and slow. Learning the shortcuts, and specifically the thought behind 
their naming, has helped me edit text more efficiently. 
I think the compound commands can help me write faster, especially since 
I don't use a mouse, so I want to get better at it.
