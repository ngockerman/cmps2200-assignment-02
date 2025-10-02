# CMPS 2200 Assignment 2

**Name:** Natalie Gockerman

In this assignment we'll work on applying the methods we've learned to analyze recurrences, and also see their behavior
in practice. As with previous
assignments, some of of your answers will go in `main.py` and `test_main.py`. You
should feel free to edit this file with your answers; for handwritten
work please scan your work and submit a PDF titled `assignment-02.pdf`
and push to your github repository.


## Part 1. Asymptotic Analysis

Derive asymptotic upper bounds of work for each recurrence below.

* $W(n)=2W(n/3)+1$
.  a = 2, b = 3, f(n) = 1
.  Given that n^(log3 2) dominates the constant:
. W(n) = Θ(n^(log 3 2)
.  
. 
.  
. 
 
* $W(n)=5W(n/4)+n$
.  a = 5, b = 4, f(n) = n 
.  n^(log4 5) which is approximately equal to n^(1.161)
. Since f(n) = n = o(n^(log4 5)), case 1 applies. 
.  Therefore W(n) = Θ(nlog4 5)
. 
.  
.  
. 

* $W(n)=7W(n/7)+n$
.  a = 7, b =7, f(n) = n
.  Since f(n) = Θ(n), case 2 applies:
.  W(n) = Θ(nlogn)
.  
. 
.  
.

* $W(n)=9W(n/3)+n^2$
.  a = 9, b = 3, f(n) = n^2
.  n^(logb a) = n^(log3 9) = n^2, case 2 applies
.  W(n) = Θ(n^2 logn)
.  
. 
.  
.  
.  
.

* $W(n)=8W(n/2)+n^3$
.  a = 8, b =2, f(n) = n^3
.  n^(logb a) = n^(log2 8) = n^3, case 2 applies
.  W(n) = Θ(n^3 log n)
.  
.  
.  
. 
.  
. 


* $W(n)=49W(n/25)+n^{3/2}\log n$
.  a = 49, b = 25, f(n) = n^(3/2) logn
.  n^(logb a) = n^(log25 49) = 1.209, case 3 applies
.  W(n) = Θ(n^(3/2) log n)
.  
. 
.  
.  
.  

* $W(n)=W(n-1)+2$
.  For this I will use telescoping:
.  W(n) = W(n-1) + 2 = W(n-2) + 4 = ... = W(1) + 2(n-1) = Θ(n)
. 
.  
. 
.  
.  
.  

* $W(n)= W(n-1)+n^c$, with $c\geq 1$
.  For this I will use summation:
.  W(n) = W(1) + sum (n, k=2) k^c = Θ(n^(c+1))
.  
.  
.  
. 
.  
. 

* $W(n)=W(\sqrt{n})+1$
.  For this I will use change of variables:
.  n = 2^k, sqrt(n) = 2^(k/2)
.  T(k) = W(2^k)
.  T(k) = T(k/2) + 1 = Θ(logk)
.  W(n) = Θ(log logn)
. 
. 


## Part 2. Algorithm Comparison

Suppose that for a given task you are choosing between the following three algorithms:

  * Algorithm $\mathcal{A}$ solves problems by dividing them into
      five subproblems of half the size, recursively solving each
      subproblem, and then combining the solutions in linear time.
    
  * Algorithm $\mathcal{B}$ solves problems of size $n$ by
      recursively solving two subproblems of size $n-1$ and then
      combining the solutions in constant time.
    
  * Algorithm $\mathcal{C}$ solves problems of size $n$ by dividing
      them into nine subproblems of size $n/3$, recursively solving
      each subproblem, and then combining the solutions in $O(n^2)$
      time.

    What are the asymptotic running times of each of these algorithms?
    Which algorithm would you choose?


.  Algorithm A: Ta(n) = Θ(n^log2 5) = Θ(n^2.322)
.  Algorithm B: Tb(n) = Θ(2^n)
.  Algorithm C: Tc(n) = Θ(n^2 logn)
.  I would pick algorithm C because it has the smallest growth.
. 
. 



## Part 3: Parenthesis Matching

A common task of compilers is to ensure that parentheses are matched. That is, each open parenthesis is followed at some point by a closed parenthesis. Furthermore, a closed parenthesis can only appear if there is a corresponding open parenthesis before it. So, the following are valid:

- `( ( a ) b )`
- `a () b ( c ( d ) )`

but these are invalid:

- `( ( a )`
- `(a ) ) b (`

Below, we'll solve this problem three different ways, using iterate, scan, and divide and conquer.

**3a. iterative solution** Implement `parens_match_iterative`, a solution to this problem using the `iterate` function. **Hint**: consider using a single counter variable to keep track of whether there are more open or closed parentheses. How can you update this value while iterating from left to right through the input? What must be true of this value at each step for the parentheses to be matched? To complete this, complete the `parens_update` function and the `parens_match_iterative` function. The `parens_update` function will be called in combination with `iterate` inside `parens_match_iterative`. Test your implementation with `test_parens_match_iterative`.


.  
. 



**3b.** What are the recurrences for the Work and Span of this solution? What are their Big Oh solutions?

**enter answer here**

.  Work recurrence: W(n) = W(n-1) + O(1), when W(0) = O(1) --> W(n) = O(n)
.  Span recurrence: S(n) = S(n-1) + O(1), when S(0) = O(1) --> S(n) = O(n)



**3c. scan solution** Implement `parens_match_scan` a solution to this problem using `scan`. **Hint**: We have given you the function `paren_map` which maps `(` to `1`, `)` to `-1` and everything else to `0`. How can you pass this function to `scan` to solve the problem? You may also find the `min_f` function useful here. Implement `parens_match_scan` and test with `test_parens_match_scan`

.  
. 



**3d.** Assume that any `map`s are done in parallel, and that we use the efficient implementation of `scan` from class. What are the recurrences for the Work and Span of this solution? 

**enter answer here**

.  Work: 
     map = O(n)
     scan = O(n)
     reduce(min) = O(n)
     Total work = O(n)
.  Span:
     map = O(1)
     scan = O(log n)
     reduce(min) = O(log n)
     Total span = O(log n)




**3e. divide and conquer solution** Implement `parens_match_dc_helper`, a divide and conquer solution to the problem. A key observation is that we *cannot* simply solve each subproblem using the above solutions and combine the results. E.g., consider '((()))', which would be split into '(((' and ')))', neither of which is matched. Yet, the whole input is matched. Instead, we'll have to keep track of two numbers: the number of unmatched right parentheses (R), and the number of unmatched left parentheses (L). `parens_match_dc_helper` returns a tuple (R,L). So, if the input is just '(', then `parens_match_dc_helper` returns (0,1), indicating that there is 1 unmatched left parens and 0 unmatched right parens. Analogously, if the input is just ')', then the result should be (1,0). The main difficulty is deciding how to merge the returned values for the two recursive calls. E.g., if (i,j) is the result for the left half of the list, and (k,l) is the output of the right half of the list, how can we compute the proper return value (R,L) using only i,j,k,l? Try a few example inputs to guide your solution, then test with `test_parens_match_dc_helper`.



.  
. 





**3f.** Assuming any recursive calls are done in parallel, what are the recurrences for the Work and Span of this solution? What are their Big Oh solutions?

**enter answer here**

.  Work recurrence: W(n) = 2W(n/2) + O(1), W(1) = O(1) --> W(n) = O(n)
.  Span recurrence: S(n) = S(n/2) + O(1), S(1) = O(1) --> S(n) = O(log n)


 
 


