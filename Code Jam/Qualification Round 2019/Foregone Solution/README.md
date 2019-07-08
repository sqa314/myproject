Problem
=
Someone just won the Code Jam lottery, and we owe them N jamcoins! However, when we tried to print out an oversized check, we encountered a problem. The value of N, which is an integer, includes at least one digit that is a 4... and the 4 key on the keyboard of our oversized check printer is broken. <br>
Fortunately, we have a workaround: we will send our winner two checks for positive integer amounts A and B, such that neither A nor B contains any digit that is a 4, and A + B = N. Please help us find any pair of values A and B that satisfy these conditions. <br>
## Input
The first line of the input gives the number of test cases, T. T test cases follow; each consists of one line with an integer N. 
## Output
For each test case, output one line containing Case #x: A B, where x is the test case number (starting from 1), and A and B are positive integers as described above. <br>
It is guaranteed that at least one solution exists. If there are multiple solutions, you may output any one of them. (See "What if a test case has multiple correct solutions?" in the Competing section of the FAQ. This information about multiple solutions will not be explicitly stated in the remainder of the 2019 contest.) 
### Limits
1 ¡Â T ¡Â 100.<br>
Time limit: 10 seconds per test set.<br>
Memory limit: 1GB.<br>
At least one of the digits of N is a 4.<br>
Test set 1 (Visible)<br>
1 < N < 105.<br>
Test set 2 (Visible)<br>
1 < N < 109.<br>
Solving the first two test sets for this problem should get you a long way toward advancing. The third test set is worth only 1 extra point, for extra fun and bragging rights! <br>
Test set 3 (Hidden)<br>
1 < N < 10100.
### Sample

Input   <br><br>

3<br>
4<br>
940<br>
4444<br><br>

Output <br><br>
  
Case #1: 2 2<br>
Case #2: 852 88<br>
Case #3: 667 3777<br><br>

  
In Sample Case #1, notice that A and B can be the same. The only other possible answers are 1 3 and 3 1. 