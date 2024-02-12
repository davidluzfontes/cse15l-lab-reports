# Lab Report 3 - Bugs and Commands

## Part 1 - Bugs

**Failiure-inducing input**

```java
//Code that fails test
public class ArrayExamples {
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
}

//Failed test
public class ArrayTests {
	@Test 
	public void testReverseInPlace() {
		int[] willFail = { 1, 2, 3 }; //Failiure inducing output
		ArrayExamples.reverseInPlace(willFail);
		assertArrayEquals(new int[]{ 3, 2, 1 }, willFail); 
	}
}
```
