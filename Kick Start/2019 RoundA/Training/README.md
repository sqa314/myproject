Problem
-
As the football coach at your local school, you have been tasked with picking a team of exactly P students to represent your school. There are N students for you to pick from. The i-th student has a skill rating Si, which is a positive integer indicating how skilled they are. 
<br>
You have decided that a team is fair if it has exactly P students on it and they all have the same skill rating. That way, everyone plays as a team. Initially, it might not be possible to pick a fair team, so you will give some of the students one-on-one coaching. It takes one hour of coaching to increase the skill rating of any student by 1. 
<br>
The competition season is starting very soon (in fact, the first match has already started!), so you'd like to find the minimum number of hours of coaching you need to give before you are able to pick a fair team. 
<br>
## Input
The first line of the input gives the number of test cases, T. T test cases follow. Each test case starts with a line containing the two integers N and P, the number of students and the number of students you need to pick, respectively. Then, another line follows containing N integers Si; the i-th of these is the skill of the i-th student. 
<br>
## Output
For each test case, output one line containing Case #x: y, where x is the test case number (starting from 1) and y is the minimum number of hours of coaching needed, before you can pick a fair team of P students. 
<br>
### Limits
<br>
Time limit: 15 seconds per test set.
Memory limit: 1 GB.
<br>
1 ≤ T ≤ 100.<br>
1 ≤ Si ≤ 10000, for all i.<br>
2 ≤ P ≤ N.<br>
Test set 1 (Visible)<br>
2 ≤ N ≤ 1000. <br>
Test set 2 (Hidden)<br>
2 ≤ N ≤ 105. <br><br>
### Sample
<br><br>
Input        <br> 
3<br>
4 3<br>
3 1 9 100        Case #1: 14<br>
6 2               Case #2: 0<br>
5 5 1 2 3 4   Case #3: 6<br>
5 5<br>
7 7 1 7 7<br> <br>
Output<br>
Case #1: 14<br>
Case #2: 0<br>
Case #3: 6<br><br>
In Sample Case #1, you can spend a total of 6 hours training the first student and 8 hours training the second one. This gives the first, second and third students a skill level of 9. This is the minimum time you can spend, so the answer is 14. <br>
In Sample Case #2, you can already pick a fair team (the first and second student) without having to do any coaching, so the answer is 0. <br>
In Sample Case #3, P = N, so every student will be on your team. You have to spend 6 hours training the third student, so that they have a skill of 7, like everyone else. This is the minimum time you can spend, so the answer is 6. 
