# Lab Report 5 - Putting it All Together

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


**TA**
Instead of running it with the java command, try it with the java debugger so you can see exactly what went wrong
```
jdb -classpath .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples
```






## Part 2 – Reflection
Something cool I learned was using Vim to edit files directly from the command line. 
I had heard about it before, and tried to use it on ieng6 and on my own laptop, but it 
felt very clunky and slow. Learning the shortcuts, and specifically the thought behind 
their naming, has helped me edit text more efficiently. 
I think the compound commands can help me write faster, especially since 
I don't use a mouse, so I want to get better at it.
