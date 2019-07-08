Problem
=
En garde! Charles and Delila are about to face off against each other in the final fight of the Swordmaster fencing tournament. <br>
Along one wall of the fencing arena, there is a rack with N different types of swords; the swords are numbered by type, from 1 to N. As the head judge, you will pick a pair of integers (L, R) (with 1 ¡Â L ¡Â R ¡Â N), and only the L-th through R-th types of swords (inclusive) will be available for the fight. <br>
Different types of sword are used in different ways, and being good with one type of sword does not necessarily mean you are good with another! Charles and Delila have skill levels of Ci and Di, respectively, with the i-th type of sword. Each of them will look at the types of sword you have made available for this fight, and then each will choose a type with which they are most skilled. If there are multiple available types with which a fighter is equally skilled, and that skill level exceeds the fighter's skill level in all other available types, then the fighter will make one of those equally good choices at random. Notice that it is possible for Charles and Delila to choose the same type of sword, which is fine ? there are multiple copies of each type of sword available. <br>
The fight is fair if the absolute difference between Charles's skill level with his chosen sword type and Delila's skill level with her chosen sword type is at most K. To keep the fight exciting, you'd like to know how many different pairs (L, R) you can choose that will result in a fair fight. <br>
Input
The first line of the input gives the number of test cases, T. T test cases follow. Each case begins with a line containing the two integers N and K, as described above. Then, two more lines follow. The first of these lines contains N integers Ci, giving Charles' skill levels for each type of sword, as described above. Similarly, the second line contains N integers Di, giving Delila's skill levels. 
Output
For each test case, output one line containing Case #x: y, where x is the test case number (starting from 1) and y is the number of choices you can make that result in a fair fight, as described above. 
Limits
1 ¡Â T ¡Â 100.<br>
0 ¡Â K ¡Â 105.<br>
0 ¡Â Ci ¡Â 105, for all i.<br>
0 ¡Â Di ¡Â 105, for all i.<br>
Time limit: 30 seconds per test set.<br>
Memory limit: 1GB.<br>
Test set 1 (Visible)<br>
1 ¡Â N ¡Â 100.<br>
Test set 2 (Hidden)<br>
N = 105, for exactly 8 test cases.<br>
1 ¡Â N ¡Â 1000, for all but 8 test cases.
Sample

Input <br><br>  
6<br>
4 0<br>
1 1 1 8<br>
8 8 8 8<br>
3 0<br>
0 1 1<br>
1 1 0<br>
1 0<br>
3<br>
3<br>
5 0<br>
0 8 0 8 0<br>
4 0 4 0 4<br>
3 0<br>
1 0 0<br>
0 1 2<br>
5 2<br>
1 2 3 4 5<br>
5 5 5 5 10<br><br>
Output <br><br> 
Case #1: 4<br>
Case #2: 4<br>
Case #3: 1<br>
Case #4: 0<br>
Case #5: 1<br>
Case #6: 7<br><br>  
In Sample Case #1, the fight is fair if and only if Charles can use the last type of sword, so the answer is 4. <br>
In Sample Case #2, there are 4 fair fights: (1, 2), (1, 3), (2, 2), and (2, 3). Notice that for pairs like (1, 3), Charles and Delila both have multiple swords they could choose that they are most skilled with; however, each pair only counts as one fair fight. <br>
In Sample Case #3, there is 1 fair fight: (1, 1). <br>
In Sample Case #4, there are no fair fights, so the answer is 0. <br>
In Sample Case #5, remember that the duelists are not trying to make the fights fair; they choose the type of sword that they are most skilled with. For example, (1, 3) is not a fair fight, because Charles will choose the first type of sword, and Delila will choose the third type of sword. Delila will not go easy on Charles by choosing a weaker sword! <br>
In Sample Case #6, there are 7 fair fights: (1, 3), (1, 4), (2, 3), (2, 4), (3, 3), (3, 4), and (4, 4). 