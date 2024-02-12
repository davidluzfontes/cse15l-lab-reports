# Lab Report 3 - Bugs and Commands

## Part 1 - Bugs

<br>  

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

<br>

**Failure-inducing input: { 1, 2, 3 }**
```java
public class ArrayTests {
  @Test 
  public void testReverseInPlace() {
    int[] willFail = { 1, 2, 3 }; 
    ArrayExamples.reverseInPlace(willFail);
    //Expected { 3, 2, 1 }, Actual { 3, 2, 3 }
    assertArrayEquals(new int[]{ 3, 2, 1 }, willFail); 
  }
}
```

 <br>

**Input that doesn't induce a failure: { 1, 2, 1 }**
```java
public class ArrayTests {
  @Test 
  public void testReverseInPlace() {
    int[] willPass = { 1, 2, 1 }; 
    ArrayExamples.reverseInPlace(willPass);
    //Expected { 1, 2, 1 }, Actual { 1, 2, 1 }
    assertArrayEquals(new int[]{ 1, 2, 1 }, willPass); 
  }
}
```

 <br>

**Symptom**
![Symptom](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/3792d2c5-15f0-4321-8168-a70c3f1515a4)

 <br>

**Fix**

Before
```java
public class ArrayExamples {

  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
}
```

After
```java
public class ArrayExamples {

  static void reverseInPlace(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[i];
    }
  }
}
```

The issue was that the elements at the start of the array were being overwritten,
so when the loop tried to access them to replace the values at the end, they were no
longer their original values.

The fix adresses the issue by creating a temporary array `newArr`, which is identical to the original
array `arr`. Then the loop can replace the elements in `arr` using the values from `newArr`, which don't change.
