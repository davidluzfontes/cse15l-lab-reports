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


## Part 2 - Researching Commands


`grep -n` - found using `man grep`

This option shows you the line number for every match that you find. This is useful if you need to find the expression in a file, 
such as to make and need to find where that mistake was made, or just want to go to 
that place and read more about the context in which the word was used.
```bash
$ grep -n that technical/biomed/cc2172.txt
29:        particularly when 'injurious' ventilatory strategies that
31:        ] . Experimental studies suggested that mechanical
38:        to humans based on the assumption that the effects of
107:          opt ) was defined as the PEEP that
248:        max , to a degree similar to that in
254:        The results of the present study indicate that
285:        understanding that PEEP at 10 cmH
308:        oxygen extraction ratio that was sufficient to compensate
310:        2 that occurred during PEEP titration [
312:        It is also noteworthy that there may be individual
349:        our discussion because we believe that pH
353:        that evaluated the impact of PEEP on splanchnic perfusion
368:        in that conducted by Kiefer and coworkers).
374:        above). We acknowledge that in day-to-day clinical
384:        because some methodological problems, we believe that we
404:        i , it is conceivable that longer
408:        Collectively, the present findings indicate that
416:        vasculature. Nonetheless, the possibility that PEEP can`
```

```bash
$ grep -n oxygen technical/biomed/cc3.txt
6:        Aggressive methods of decreasing oxygen consumption,
8:        patients with marginal oxygen delivery associated with
11:        to increase efficiency of oxygen utilization and decrease
16:        work and oxygen consumption in the face of compromised
201:          Decreased brain oxygenation initially causes increased
277:        arrhythmias by increasing myocardial work and oxygen
281:        arrhythmias and compromise oxygen delivery. Hyperactivity
```


**Bracket Expressions** found using `man grep`


```bash
$ grep [wxz] technical/biomed/1471-2334-3-13.txt
          Have any transfers been described between archaea
          bifunctional catalase-peroxidase is likely a transfer
          factor, this enzyme has been implicated as a virulence
          E. coli O157:H7 catalase-peroxidase
          has been associated with enterohaemorrhagic hemolysin in
          a variety of shiga-like toxin-producing
          (verotoxin-producing)
          correlation of the presence of the catalase-peroxidase in
          How can we identify other genes likely to have been
          virulence-associated. This subset will be the focus of
          O157-specific plasmids that were previously sequenced [
          32 ] from which some of the preliminary work [ 9 ]
          described below was derived.
          following criteria:
          score > 95) to ORFs found in at least two archaeal
          3) having few or no highly similar proteins (BLASTP
          This search was facilitated by the Clusters of
          worth considering as LGTs from archaea to pathogenic
          bacteria. Table 1shows these ORFs with their location
          and, if any information was available, a possible
          generally associated with virulence, many genes, under
          contribute to pathogenicity. There are examples in the
          literature where both ABC transporters (in
          Further testing of this hypothesis will require
          although commonly employed [ 6 7 37 ] it is fraught with
          wrote:
            tree-based approach will become both more challenging
            and more rewarding.
          transfer as a major contributor of "new" virulence genes
          many ways, the most unlikely source for virulence genes.
          virulence genes will be expanded to include virtually all
          At the same time, however, it would allow us to move from
          a descriptive, reactionary view of infectious disease
          towards a predictive science of infectious disease. It
          would be dramatic evidence of what some microbiologists
          the emergence of new bacterial pathogens.
```


