﻿Problem
=
You have been hired recently as the Chief Decision Maker (CDM) at a famous parcel delivery company, congratulations! Customers love speedy deliveries of their parcels and you have decided to decrease the time it takes to deliver parcels around the world to win customers. You have introduced this idea to the authorities and they have allocated you enough budget to build at most one new delivery office. 
The world can be divided into an R × C grid of squares. Each square either contains a delivery office or it does not. You may pick a grid square that does not already contain a delivery office and build a new delivery office there. <br>
The delivery time of a parcel to a square is 0 if that square contains a delivery office. Otherwise, it is defined as the minimum Manhattan distance between that square and any other square containing a delivery office. The overall delivery time is the maximum of delivery times of all the squares. What is the minimum overall delivery time you can obtain by building at most one new delivery office? 
Note: The Manhattan distance between two squares (r1,c1) and (r2,c2) is defined as |r1 - r2| + |c1 - c2|, where |*| operator denotes the absolute value. <br>
## Input
The first line of the input gives the number of test cases, T. T test cases follow. The first line of each test case contains the number of rows R and number of columns C of the grid. Each of the next R lines contains a string of C characters chosen from the set {0, 1}, where 0 denotes the absence of a delivery office and 1 denotes the presence of a delivery office in the square. 
## Output
For each test case, output one line containing Case #x: y, where x is the test case number (starting from 1) and y is the minimum overall delivery time you can obtain after adding at most one additional delivery office. 
### Limits
Time limit: 15 seconds per test set.<br>
Memory limit: 1GB.<br>
1 ≤ T ≤ 100.<br>
There is at least one delivery office in the initial grid.<br>
Test set 1 (Visible)<br>
1 ≤ R ≤ 10.<br>
1 ≤ C ≤ 10.<br>
Test set 2 (Hidden)<br>
1 ≤ R ≤ 250.<br>
1 ≤ C ≤ 250.<br>
### Sample

Input   <br><br>

3<br>
3 3<br>
101<br>
000<br>
101<br>
1 2<br>
11<br>
5 5<br>
10001<br>
00000<br>
00000<br>
00000<br>
10001<br><br>
Output <br><br>
  

  
Case #1: 1<br>
Case #2: 0<br>
Case #3: 2<br><br>

  
In Sample Case #1, you get a minimum overall delivery time of 1 by building a new delivery office in any one of the five squares without a delivery office. <br>
In Sample Case #2, all the squares already have a delivery office and so the minimum overall delivery time is 0. Note you have to add at most one delivery office. <br>
In Sample Case #3, to get a minimum overall delivery time of 2, you can build a new delivery office in any of these squares: (2, 3), (3, 2), (3, 3), (3, 4), or (4, 3). Any other possibility results in a higher overall delivery time than 2. 