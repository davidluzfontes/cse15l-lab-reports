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
```
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

```
$ grep -n oxygen technical/biomed/cc3.txt
6:        Aggressive methods of decreasing oxygen consumption,
8:        patients with marginal oxygen delivery associated with
11:        to increase efficiency of oxygen utilization and decrease
16:        work and oxygen consumption in the face of compromised
201:          Decreased brain oxygenation initially causes increased
277:        arrhythmias by increasing myocardial work and oxygen
281:        arrhythmias and compromise oxygen delivery. Hyperactivity
```


**Bracket Expressions** - found using `man grep`

A bracket expression is a list of characters enclosed by [   and   ]. By using that that
grep will look for any character in that expression. You can use a hyphen to search for a range of
characters, such as [a-e] for [abcdefg] or [0-5] to [012345]. Its useful if you want to find all of the
numbers in a file, or if you're looking for words with multiple spellings.

```
$ grep wom[ea]n technical/biomed/1471-2407-1-13.txt
        of developing corpus uterine cancer. In addition, a woman
        these women should be removed from the at-risk population
          women's health issues, such as pregnancy and
          hysterectomy. A question that asks whether a woman has
          woman's current age, indicates the prevalent proportion
          of women who have had a hysterectomy by a certain
          the population so that it reflects women at risk of
          developing the disease. We assume that a woman is at risk
          women who are diagnosed with corpus uterine cancer are
          age-specific number of hysterectomies plus women
          the age-specific rate of women not at risk of corpus
          uterine cancer divided by the age-specific rate of women
          prevalent proportion of women not at risk of corpus
        1995-97 are highest, particularly for women aged 45 through
        the denominator of the rate calculation including women who
        women ages 75-79. In this age group, the uncorrected rate
        Corresponding percentages women free of the disease at age
        Utah over the next 10 years among women aged
        with cancer of the corpus uterine is greatest for women
        of women alive that have undergone a hysterectomy increases
        procedure, over 35% of women in the United States received
        relevant to a woman already aged to mid-life. However,
        reflect those women at risk. The two methods developed in
```

```
$ grep " [a-z]en"  technical/biomed/1471-2288-2-4.txt
        genetic changes have been proposed for cancer early
        The true positive rate (TPR), or the test sensitivity, is
        mortality endpoint, mammography is generally considered an
        TPR (Table 2) and generate a receiver-operating
        better the test performance. As mentioned previously,
        To more generally compare performance of a combination
        farthest to the left, which is generally all that would
        model that is overly sensitive to chance fluctuations in
        into ten samples each with 10% of the data, (ii) one of the
        (iv) an average is taken of the statistic over all ten 10%
        split-sample approach tended to underestimate performance,
```

**Anchoring** found using `man grep` 
The caret ^ and the dollar sign $ respectively match the empty string at the beginning and end of a line. This is useful if you want to line for expressions at the start or at the end of a line.


```
$ grep ^this technical/government/Env_Prot_Agen/tech_adden.txt
this time. The unquantified benefits for ozone and PM fall into two
this analysis because of modeling and resource limitations. The
this case, we have a 70 year old individual dying from pneumonia
this section.
this analysis.
```

```
$ grep -n ^that technical/government/Env_Prot_Agen/bill.txt
112:that is subject to emissionreduction requirements or limitations
177:that section;
364:that is reported as a generating unit pursuant to Department of
2082:that emissions limitation is not expressed on an annual basis, the
2360:that producedelectricity for sale.
2648:that the reassigned tonnage limitswill, in total, achieve the same
2884:that for the purposes of applying this subsection to any such unit,
4128:that the auctioned allowances shall be allocated and sold on the
4277:that produced or produces electricity for sale during 2001 or any
4696:that does not exceed 250,000 allowances; and
4822:that section;
5163:that permits the unit during the demonstration period
5239:that produced or produces electricity for sale during 2001 or any
5582:that the Administrator administers in a State's applicable
5775:that an owner or operator has either undertaken a continuous
5799:that is not a new affected unit.
5979:that the technology is equivalent in terms of mercury capture to
6583:that the following requirements are met prior to the commencement
6854:that a transitional area has not attained the standard, the area
6973:that: 
```

**Alternation** - found using `man grep`

Two regular expressions may be joined by the operator |.
The resulting regular expression matches any stringmatching either alternate expression.
 *If using basic regular expressions the | operator needs to be prefixed by \.


```
$ grep 'agent\|platypus' technical/biomed/1472-6947-3-8.txt
          biomolecular features. If an agent were discovered that
          to the same agent.
          biological property allows us to infer that agents that
          agents (chemical or biological) that induce precancers to
            that heighten sensitivity to a causal agent, such as
            regress when the causative agent is withdrawn (e.g.
            example, the platypus has challenged animal
```

```
$ grep -E 'oxygen|nitrogen|hydrogen' technical/biomed/1471-2091-2-9.txt
        double-bounded oxygen, an arrangement that is similar to
          equatorial nitrogen from an amino group and three
          equatorial oxygen ligands from carboxyl or phosphate
          set includes two equatorial oxygen from two water
          molecules, one equatorial oxygen from a carboxyl group or
          phosphate, and one equatorial nitrogen from an amino
          group. The other set contains one equatorial oxygen from
          water and three equatorial oxygens from carboxyl groups
          is one equatorial oxygen from a hydroxyl group and three
          equatorial oxygens from carboxyl groups or phosphate.
          according to eq 1 is two equatorial oxygen from hydroxyl
          groups and another two equatorial oxygen from two water
        from aspartate or glutamate, and two oxygens from the
        hydroxyl group and three oxygens derived from carboxyl
        water molecule through hydrogen bond in the conformation
        two water molecules that are hydrogen bonded to other
          oxygen was removed from solutions by purging with dry
          nitrogen gas. Stock vanadyl and nucleotide solution were
          immediately frozen in liquid nitrogen, and stored in
          liquid nitrogen before using.
          standard cavity and a liquid nitrogen flow cryostat
```
