# O(n log n) Algorithm for counting inversions

Option one: brute force.
* double for loop to go through i, j. Checks if it is inverted. n(n-1)/2 compares. O(n^2) time.

Option two: divide and conquer
* inspired by mergesort
* types of inversions
    * left inversion: i, j <= n/2
    * right inversion: i, j > n/2
    * split: i < n/2 < j

* goal implement countsplit in lenar time 
* there are quadriatic split inversion but we want to count them in linear time

 # Inversion Algorithm video II

 Key idea: have recursive calls both count and sort inversions
 * mergesort naturally finds inversions

 Outline:
 Sort_and_count(array A, length n)
    if n = 1
        return 0
    else
        b,x = sort and count(1st half of A)
        c,y = sort and count(2nd half of A)
        d,z = merge and count split inv(b, c)
    return x + y + z

# Strassen's Subcubic Matrix Multiplication Algorithm

* non trivial and useful. No idea how he came up with the algorithm

Problem: multiply 2 nxn matricies to produce
* best we could do it O(n^2) theoretically

|a b| x |e f| = |ae+bg  af+bh|
|c d|   |g h|   |ce+dg  cf+dh|
* by definition of matrix multiplication O(n^3)

Strassen's Algorithm(1969): better than cubic time!. At the time that it was published it blew people's minds
* Step 1: recursively compute only 7 (cleverly chosen) products. Saving 1 recursive call makes a huge difference since that will be called many many times
* Step 2: do th neccessary (clever) additiona and subtractions (still O(n^2) time)

The seven products:
* P1 = A(F-H)
* P2 = (A+b)H
* P3 = (C + D)E
* P4 = D(G-E)
* P5 = (A+D)(E+H)
* P6 = (B - D)(G + H)
* P7 = (A - C)(E + F)

|a b| x |e f| = |ae+bg  af+bh|
|c d|   |g h|   |ce+dg  cf+dh|

* ae+bg = P5+P4-P2+P6
* af+bh = P1+P2
* ce+dg = P3+P4
* cf+dh = P1+P5-P3-P7