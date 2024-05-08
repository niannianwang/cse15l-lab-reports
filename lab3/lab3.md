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

## Part 2 - `grep` Command Research

1. `-i`
**Source:**
https://docs.rackspace.com/docs/use-the-linux-grep-command

**Command:**
```
grep -i research technical/biomed/*.txt
```

**Output:**
```
technical/biomed/1472-6874-2-13.txt:        the primary products of research [ 8 9 ] . Figure 1, though
technical/biomed/1472-6874-2-13.txt:          Endocrine Research Laboratory. The analyses for E 
technical/biomed/1472-6874-2-13.txt:        typical purposes of epidemiological research because the
technical/biomed/1472-6874-2-13.txt:        results of typical epidemiological research center on
technical/biomed/1472-6874-2-13.txt:        researchers' capacity to control. For example, the validity
technical/biomed/1472-6874-2-13.txt:        useful for designing future research projects exploring the
technical/biomed/1472-6874-2-13.txt:        from the Cancer Center Support grant to the Cancer Research
technical/biomed/1472-6882-1-10.txt:        hunting success. During the research some hunters claimed
technical/biomed/1472-6882-1-10.txt:          The research area is located in Guayaguayare on
technical/biomed/1472-6882-1-10.txt:          conducted research with one group of seven hunters based
technical/biomed/1472-6882-1-10.txt:          mixed race. This research included participant
technical/biomed/1472-6882-1-10.txt:          to hunters (and researchers) which may explain some of
technical/biomed/1472-6882-1-10.txt:          their bush medicine remedies. One research hazard was the
...
```

**Function:**
In this example, using `-i` ignores the text files and texts in `biomed` that does not contain the word `research` and displays all the files and lines where `research` appears. This is really useful for what we normally do command+f when looking through web pages and files, but case case insensitive.

**Command:**
```
grep -i police technical/911report/*.txt
```

**Output:**
```
technical/911report/chapter-1.txt:    At 8:52, in Easton, Connecticut, a man named Lee Hanson received a phone call from his son Peter, a passenger on United 175. His son told him: "I think they've taken over the cockpit-An attendant has been stabbed- and someone else up front may have been killed. The plane is making strange moves. Call United Airlines-Tell them it's Flight 175, Boston to LA." Lee Hanson then called the Easton Police Department and relayed what he had heard.
technical/911report/chapter-1.txt:    Shortly after 9:00, Indianapolis Center started notifying other agencies that American 77 was missing and had possibly crashed. At 9:08, Indianapolis Center asked Air Force Search and Rescue at Langley Air Force Base to look for a downed aircraft. The center also contacted the West Virginia State Police and asked whether any reports of a downed aircraft had been received. At 9:09, it reported the loss of contact to the FAA regional center, which passed this information to FAA headquarters at 9:24.
technical/911report/chapter-10.txt:                of a military police lead vehicle and a van; the proposed briefing theater had no
technical/911report/chapter-11.txt:                officials-local airport managers and local police departments- who had not seen such
technical/911report/chapter-11.txt:                concerned citizens. Representatives of the Justice Department, the FAA, local police
technical/911report/chapter-12.txt:                violent extremism. According to Karachi's police commander, there are 859 madrassahs
technical/911report/chapter-12.txt:            The country's vast unpoliced regions make Pakistan attractive to extremists seeking
technical/911report/chapter-12.txt:                with al Qaeda. Saudi police are regularly being killed in shootouts with terrorists.
...
```

2. `-E`

**Function:**
This will be useful for people who would like to research particularly on police involvement in 911 as the command searches for where police appears in the text files about 911report. They don't have to scroll through all files but can quickly query the areas where the information they want may be.

**Input:**
```
grep -E "[0-9]" technical/biomed/*.txt
```

**Output:**
```
technical/biomed/rr172.txt:        4 hours in minimal Eagle's medium with Earle's salts to
technical/biomed/rr172.txt:        consisted of untreated controls, treatment with 50 ng/ml
technical/biomed/rr172.txt:        TNF-α and treatment with 0.4 μg/ml CSC. After treatments,
technical/biomed/rr172.txt:        from the wells and centrifuged 1 min at 12,000 × 
technical/biomed/rr172.txt:        g. Aliquots of 20 μl of each lysate
technical/biomed/rr172.txt:        to moderate doses of CSC by activating both the ERK1/2 and
technical/biomed/rr172.txt:        kinase; MEK-1 = MAPK kinase; NFκB = nuclear factor-kappa B;
technical/biomed/rr191.txt:        hyperinsulinemic [ 1 ] . An increased incidence of neonatal
technical/biomed/rr191.txt:        infants of diabetic mothers [ 1 ] . RDS is caused by
technical/biomed/rr191.txt:        lung development [ 2 ] . It has been proposed that high
technical/biomed/rr191.txt:        the diabetic mother [ 3 ] .
technical/biomed/rr191.txt:        (~80%), cholesterol (~10%), and proteins (~10%), functions
technical/biomed/rr191.txt:        end expiration [ 4 ] . The surfactant-associated proteins
technical/biomed/rr191.txt:        regulated [ 4 ] . We, and others, have shown that the SP-A
technical/biomed/rr191.txt:        significantly decreased [ 1 ] . Low SP-A levels in amniotic
technical/biomed/rr191.txt:        neonatal RDS [ 5 ] . Our previous studies have shown that
technical/biomed/rr191.txt:        transcription [ 6 7 ] .
...
```
