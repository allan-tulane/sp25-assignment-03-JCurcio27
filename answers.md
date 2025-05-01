# CMPS 2200 Assignment 3
## Answers

**Name:** Jaedan Curcio


Place all written answers from `assignment-03.md` here for easier grading.

1a.) Starting with N dollars, always take the largest possible coin with value < N. 
Then subtract that coin's value from N, and pick the next highest possible coin with value < N. 
Keep repeating. until the exchange is complete 

1b.) In this case, the greedy choice is picking the largest coin. If the largest coin is not picked,
its value must be made up using two or more smaller coins, which is suboptimal,meaning that the greedy 
choice is part of an optimal solution. The optimal substructure property also applies because when the 
largest coin is picked, the problem resets with value N - 2^k instead of N, meaning there is no overlap
between subproblems and can be solved recursively.

1c.) W(n) = W(n - 2^k) + O(1). Since the problem size decreased by
n/2 or more for each step, the total work is O(log n). The span is also O(log n), as no work can be done
in parallel since the optimal substructure property applies.


2a.) One counterexample to prove that the greedy algorithm above does not work would be if you were trying
to split 8 coins (N = 8) into the set of denominations {6, 4, 1}. The greedy algorithm above would tell you
that picking 6 first would be optimal, but that forces you to pick 3 total coins (6, 1, 1). However, you 
could just pick 4 and 4, and reach N in 2 coins, meaning that the greedy algorithm doesn't work in this case.

2b.) It does have the optimal substructure property, as when starting with N total coins, each time you
subtract a coin regardless of denomination, the problem resets with problem size N - K (where K is a coin
of any number), and this pattern repeats until 0 is reached. This means that the optimal substructure
property applies, as there cannot be any overlap between subproblems in this case.

2c.) Initialize an array dp size n + 1 where dp[k] is the minimum coins needed for amount i. 
Start with dp[0] = 0. For each amount from 1 to N, check each coin: if the coin's value ≤ current amount,
set dp[i] to min(its current value, 1 + dp[i - coin's value]). This guarantees finding the optimal 
solution in O(N*k) time where k is the number of coin types. The span is O(n), as the algorithm is 
sequential and checks each value in the array

