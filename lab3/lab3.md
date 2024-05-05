# Lab Report 3
## Part 1 - Bugs
### 1.1 & 1.2
Failure-inducing Test:
```
public class ArrayTests {
        @Test 
	public void testReverseInPlace() {
            int[] input2 = {1, 2, 3};
            ArrayExamples.reverseInPlace(input2);
            assertArrayEquals(new int[]{3, 2, 1}, input2);
	}
 }
```
Passed Test:
```
public class ArrayTests {
	@Test 
	public void testReverseInPlace() {
            int[] input1 = { 3 };
            ArrayExamples.reverseInPlace(input1);
            assertArrayEquals(new int[]{ 3 }, input1);
        }
 }
```

### 1.3 Output
Error Message:
``` (base) nian-nianwang@Nian-NiandeMBP lab3 % javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
(base) nian-nianwang@Nian-NiandeMBP lab3 % java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ArrayTests
JUnit version 4.13.2
.E.
Time: 0.005
There was 1 failure:
1) testReverseInPlace(ArrayTests)
arrays first differed at element [2]; expected:<1> but was:<3>
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:78)
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:28)
        at org.junit.Assert.internalArrayEquals(Assert.java:534)
        at org.junit.Assert.assertArrayEquals(Assert.java:418)
        at org.junit.Assert.assertArrayEquals(Assert.java:429)
        at ArrayTests.testReverseInPlace(ArrayTests.java:16)
        ... 30 trimmed
Caused by: java.lang.AssertionError: expected:<1> but was:<3>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at org.junit.internal.ExactComparisonCriteria.assertElementsEqual(ExactComparisonCriteria.java:8)
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:76)
        ... 36 more

FAILURES!!!
Tests run: 2,  Failures: 1 ```
```

### 1.4 Code
Buggy Code:
```
public class ArrayExamples { 

  // Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
}
```

Fixed Code:
```
public class ArrayExamples { 

  // Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length / 2; i += 1) {
      int toSwap = arr[i];
      arr[i] = arr[arr.length - i - 1];
      arr[arr.length - i - 1] = toSwap;
    }
  }
}
```

### 1.5
The fixed code loops through half of the Array. This loop is designed to only iterate through half of the array because when swapping elements to reverse the array, we only need to go halfway to avoid re-reversing elements. 

Within the loop, it stores the value of the element at index `i` in a variable named `toSwap`. It assigns the value of the element at index `arr.length - i - 1`, which corresponds to the position of the element in the array that is symmetrically opposite to the element at index `i`, to the element at index i. The element at index `arr.length - i - 1` is then assigned to the value `toSwap`, which was the original value of the element at index `i`.

This fixed code effectively swaps the first half of the array with the second half.
