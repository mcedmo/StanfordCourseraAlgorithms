# Asymptotic Analysis

## The Gist
The language by which all computer scientists evaluate algorithms.

* sweet spot for high level reasoning about algorithms
    * coarse enough to ignore architechure/language/compiler
    * sharp enough to make useful comparisons

* High level idea: supress constant factors and lower order terms.
    * lower order terms become increasingly irrelevant with large inputs
    * constants include system dependents

* Example: equate 6nlog2n + 6n with just nlogn (6n is lower order on both sides so they are dropped)
    * terminology: running time is O(nlogn)
    * once you have selected an algorithm it may be good to include the lower order terms

* Example: 1 loop: does array A contain the integer?
    * simplest solution: go through each index and check. If you get to the end it is not there
        * Running time: O(n) (aka linear)
        * constant number of computes per loop
* Example 2: two loops: given A, B arrays and t does a or b contain t?
    * there are twice as many operations but there is still only one loop
    * remains O(n)
* Example 3: Do arrays A, B have a number in common?
    * coded with a for loop inside of a loop
    * O(n^2) (quadratic time algorithm).
    * Doubling the input length the running time goes up 4x
* example 4: two nested loops (ii): does array have duplicate entries?
    * two nested for loops but j = i + 1
    * O(n^2)
    * number of iterations is still a factor of n

## Big-Oh Notation

Q: What does it mean for a function to be O(f(n))
A: for all sufficiently large n it is bounded above by a constant multiple of f(n)

Formal definition: 

## Big Omega and Theta

Definition: T(n) = omega(f(n)) if and oly if there exists constants c,n0 such that T(n) >= c * f(n) for all sufficiently large n. upsidedown A >= n0.
* N0 is the crossing point at wich it becomes true or where the two functions cross

* upper bound is usually used since the upper bound is more important

Theta Notation:
* T(n) = theta(fn) if and only if T(n) = O(f(n)) and T(n) = omega(f(n))