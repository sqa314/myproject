Problem
=
You have just entered the world's easiest maze. You start in the northwest cell of an N by N grid of unit cells, and you must reach the southeast cell. You have only two types of moves available: a unit move to the east, and a unit move to the south. You can move into any cell, but you may not make a move that would cause you to leave the grid. <br>
You are excited to be the first in the world to solve the maze, but then you see footprints. Your rival, Labyrinth Lydia, has already solved the maze before you, using the same rules described above! <br>
As an original thinker, you do not want to reuse any of Lydia's moves. Specifically, if her path includes a unit move from some cell A to some adjacent cell B, your path cannot also include a move from A to B. (However, in that case, it is OK for your path to visit A or visit B, as long as you do not go from A to B.) Please find such a path. <br>
        
               
## Input
The first line of the input gives the number of test cases, T. T test cases follow; each case consists of two lines. The first line contains one integer N, giving the dimensions of the maze, as described above. The second line contains a string P of 2N - 2 characters, each of which is either uppercase E (for east) or uppercase S (for south), representing Lydia's valid path through the maze. 
## Output
For each test case, output one line containing Case #x: y, where x is the test case number (starting from 1) and y is a string of 2N - 2 characters each of which is either uppercase E (for east) or uppercase S (for south), representing your valid path through the maze that does not conflict with Lydia's path, as described above. It is guaranteed that at least one answer exists. 
### Limits
1 ¡Â T ¡Â 100.<br>
Time limit: 15 seconds per test set.<br>
Memory limit: 1GB.<br>
P contains exactly N - 1 E characters and exactly N - 1 S characters.<br>
Test set 1 (Visible)<br>
2 ¡Â N ¡Â 10.<br>
Test set 2 (Visible)<br>
2 ¡Â N ¡Â 1000.<br>
Test set 3 (Hidden)<br>
For at most 10 cases, 2 ¡Â N ¡Â 50000.<br>
For all other cases, 2 ¡Â N ¡Â 10000.<br>
### Sample

Input <br><br>
  
2<br>
2<br>
SE<br>
5<br>
EESSSESE<br><br>

Output <br><br>
  

  
Case #1: ES<br>
Case #2: SEEESSES<br><br>

  
In Sample Case #1, the maze is so small that there is only one valid solution left for us. <br>
Sample Case #2 corresponds to the picture above. Notice that it is acceptable for the paths to cross. 