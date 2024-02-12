# Lab Report 3 - Bugs and Commands

## Part 1 - Bugs



**Code being tested**
```java
public class ArrayExamples {
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
}
```



**Failure-inducing input: { 1, 2, 3 }**
```java
public class ArrayTests {
  @Test 
  public void testReverseInPlace() {
    int[] willFail = { 1, 2, 3 }; 
    ArrayExamples.reverseInPlace(willFail);
    //Expects { 3, 2, 1 }, actual { 3, 2, 3 }
    assertArrayEquals(new int[]{ 3, 2, 1 }, willFail); 
  }
}
```



**Input that doesn't induce a failure: { 1, 2, 1 }**
```java
public class ArrayTests {
  @Test 
  public void testReverseInPlace() {
    int[] willPass = { 1, 2, 1 }; 
    ArrayExamples.reverseInPlace(willPass);
    //Expects { 1, 2, 1 }, actual { 1, 2, 1 }
    assertArrayEquals(new int[]{ 1, 2, 1 }, willPass); 
  }
}
```
