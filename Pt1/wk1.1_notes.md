# Week 1: Introduction

## Integer Multiplication

* Usually define problem with specified input and output

Input: two n-digit number x and y
Output: product x * y

Assess the algorithm through the number of basic opperations performed:
For now these opperations inlclude
* adding 2 single digit numbers
* adding 2 single digit numbers

5678 * 1234

Use long multiplication to break this down to single digit multiplication.

Upshot: number of operations grows at a constant * n^2

"Perhaps the most important principle of all for the good algorithm designer is to refuse to be content"

Is this really the best algorithm for multiplication?

## Karatsuba Multiplication

x = 1234
y = 5678

Dont need to understnad the demo. Just know that there is a lot of room for improvement in the algorithm space.

Step 1: a * c = 672
Step 2: b * d = 2652
Step 3: (a+b)(c + d) = 6164
Step 4: 3 - 2 - 1 = 2840
Step 5: 6720000 + 2652 + 284000 = 7006652

#### A recursive algorithm
To create this we need to break the inputs up into smaller numbers.

Write x = 10^(n/2) a + b and y = 10^(n/2) c + d where a, b,c,d are n/2-digit numbers.

Then: x * y = (10^(n/2)a + b) * (10^(n/2) c + d) <-- call this *
            = (10^n)ac + (10^(n/2))(ad+bc) + bd
Idea: recursively compute ac, ad, bc, bd then compute (*) in teh gradeschool algorithm.
* base case: when there is one digit in each of the inputs has one digit multiply them

#### Refine the algorithm
There are only 3 quantities we care about (ad+bc) can be treated as one

1. Recursively compute ac
2. Recursively compute bd
3. Recursively compute (a+b) * (c+d)  = ac + ad + bc + bd
4. Gauss's trick: step 3 - step 1 - step 2 = ad + bc

Upshot: only need 3 recursive multiplications

## Mergesort: Motivation and Example
Why study mergesort?
* known in 1945
* still used all the time and is the standard in a number of programming libraries
* good introduction to divide and conquer. Still may be the most clear example
* improves over selection, insertion, bubble sorts. Still can have places where they are useful but mergesort is better
* analysis generalized to "master method"

**The sorting problem:**
Input: arrof of n numbers, unsorted.
Output: same numbers increasing in order

## Mergesort: Pseudocode
* recursively sort 1st half of input array
* recursively sort 2nd half
* merge 2 sorted sublists
* [ignores basecases]

c = output array (length n)
a = 1st sorted array (n/2)
b = 2nd sorted array (n/2)
i = 1
j = 1

for k = 1 to n: <-- increment K
    if a(i) < b(j): <-- 1 comparison
        c(k) = a(i) <-- 1 operation assignment
        i++ <-- 1 increment operation
    else:
        c(k) = b(j)
        j++

Running time:
Key Q: imagine running the program in the debugger one line at a time. How many lines of code get executed?

**Start small: how many operations in the merge?**
* i and j assignments = 2 operations
* for loop executes n times
    * in each loop: 4 operations
    * 4 operati
* Upshot: given an array of m numbers running time is <= 4m+2 (call this 6m -- we know its sloppy)

Evaluating a recursive problem seems hard since there will be exponential number number of calls of the same cod. However each successive call is smaller than the one before.

**claim: mergesort requires <=6nlog^2*n+2n**

* log is good because it grows very slowly compared to the identity algorithm f(n) = n.

## Merge Sort: Analysis

* Recursion tree method - write all calls in tree form

* Level 0: entire input
* level 1: half of input
* level 2: half of level one
* level log2n: half of log2n-1

* number of levels of recursion is log2n+1 since that is the number of times you can divide by 2 befire getting to 1 or 0. The +1 is from the first level
* at each level j there are 2^j subprobelms
* at each level j the size of the subproblem is n/2^j
* Therefore, at each level: <= 2^j + 6(n/2^j) = 6n (independent of the level)
    * number of subproblems * the amount of work at the level
* Now multiply by the max number of levels: 6nlog2n + 6n
