Skip to content


  
Pull requests 
Issues 
Marketplace 
Explore 
 


Sign out 


 Watch 
0 
 Star 
0 
 Fork 
0 

sqa314/myproject 
 Code 
 Issues 0 
 Pull requests 0 
 Projects 0 
 Wiki 
 Insights 
 Settings 
Branch: master 
Find file 
Copy path 
myproject/Archimedes 
8e52725 7 days ago 
 sqa314 Create Archimedes 
1 contributor 
 
Raw
Blame
History
   
62 lines (59 sloc) 1.73 KB 

include<stdio.h>

#include<math.h>

#include<Windows.h>

void gotoxy(int x, int y)

{

	COORD Pos = { x - 1, y - 1 };

	SetConsoleCursorPosition(GetStdHandle(STD_OUTPUT_HANDLE), Pos);

}

int main()

{

	printf("\n\n           아르키메데스의 원주율");

	printf("\n\n      -아르키메데스는 기원전 2세기경 한 원의 둘레는 원 안에 내접하는\n      정 n각형의 둘레와 외접하는 정 n각형의 둘레사이에 있을 것이라 생각했고\n      원안에 96각형을 작도함으로써 원주율을 3.14까지 계산 해냈다.");

	printf("\n\n\n\n      제작자 : 사각사과");

	Sleep(3000);

here:

	char c;

	char yn;

	double PI = 3.1415926535897932384;

	int i;

	int sum = 6;

	int num;

	system("cls");

	printf("\n\n몇각형으로 실험하시겠습니까?    [3*(2^  )]각형\n최대 201326592각형 = 오차 < 0.00000000000001");

	gotoxy(39, 3);

	scanf("%d", &num);

	if (num <= 26 && num >= 1) {

		for (i = 0; i<num;)

		{

			int cun = pow((double)2, i);

			double cune = 1 / (double)cun;

			double zhei = cune * (PI / 3);

			double scr = sin(zhei);

			double csr = 1 - cos(zhei);

			double znuq = hypot(scr, csr);

			double skr = tan(zhei);

			double skrri = skr * 3 * cun;

			printf(" %9d#  %.16f <π< %.16f\n", 6 * cun, znuq*sum / 2, skrri);

			i = i + 1;

			sum = sum * 2;

			Sleep(1);

		}

	}

	else

	{

		printf("입력한 수가 잘 못 되었거나 너무 큽니다.                                   \n오차가 커져 값을 정밀하게 표현할 수 없습니다.\n다시 입력해 주세요");

		Sleep(3000);

		goto here;

	}



dace:



	printf("\n다시하시겠습니까 ( Y/N ) ?     [");

	getchar();

	scanf("%c", &yn);

	if (yn == 'N' || yn == 'n')

		goto end;

	else if (yn == 'Y' || yn == 'y')

		goto here;

end:

	return 0;

}

© 2018 GitHub, Inc.
Terms
Privacy
Security
Status
Help
 
Contact GitHub
Pricing
API
Training
Blog
About

Press h to open a hovercard with more details. 
