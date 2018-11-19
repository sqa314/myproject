

아르키메데스의 원주율
=

1.배경지식
-

아르키메데스는
<br>
임의의 원의 둘레는 정 다각형이 그 원에 내접할 때의 길이보다 길고, 외접할 때의 길이보다 작음을 이용하여
<br>
무리수 π 의 값을 알 수 있다고 생각했다.
<br>
아르키메데스는 실재로 정 구십육각형을 이용하여 원주율을 3.1408 < π < 3.1429까지 계산하였다.

2.C언어를 이용한 원주율
-
### 2.1 #include
* #include<stdio.h>

정 n각형의 n값을 입력받기 위한 scanf_s
계산값을 출력하기 위한 printf를 포함한 여러 입출력 함수들이 포함되었다.
* #include<math.h>

정 n각형의 둘레를 계산하기 위해서는 cos sin tan와 제곱의 계산이 필요하다.
* #include<Windows.h>

원주율 코드 자체에는 필요 없으나 gotoxy[1](39,3); System(cls); sleep(3000);등의 시각적 직관성을 위해 사용되었다.
### 2.2 gotoxy _ 커서이동
<pre><code>void gotoxy(int x, int y)
{
	COORD Pos = { x - 1, y - 1 };
	SetConsoleCursorPosition(GetStdHandle(STD_OUTPUT_HANDLE), Pos);
}
</code></pre>
* COORD 

pos배열을 포함하는 구조체 함수이다.
* Pos

2개의 정수로 이루어진 배열로 gotoxy의 정수 입력 x(가로)와 y(세로)[2]가 저장된다.
* SetConsoleCursorPosition

GetStdHandle(STD_OUTPUT_HANDLE)이라는 함수와 Pos배열을 입력으로 가지는 함수로<br>
커서의 위치를 조절하는 HANDLE을 불러내어 Pos의 위치에 가져다 놓는(반환하는) 방식으로 화면에서의 커서 좌표를 설정한다.
### 2.3 main
* printf
정수, 고정소수점, 문자열 등을 출력할 수 있는, 가장 기본적인 출력함수로
> printf(" %9d# %.4f < π < %.4f\n", 6 * cun, znuq * sum / 2, skrri);

위와 같이 쓸 수 있으며
>        96# 3.1408 < π < 3.1429

가 출력된다.[3]
* scanf
정수, 고정소수점, 문자열 등을 입력할 수 있는, 가장 기본적인 입력함수로
<br>
> scanf("%d", &num);
<br>
와 같이 사용할 수 있으며 이후 입력된 값이 num의 주소값으로 보내져 변수 num의 값으로 적용된다.
<br>
[^1] :gotoxy함수 내에있는 SetConsoleCursorPosition 함수는 헤더파일 WinCon.h의 함수지만 Windows.h가 WinCon.h를 포함하므로 설명은 생략한다.
<br>
[2] :임의의 문자도 상관 없다.
<br>
[3]: 설명을 위해 변수에 들어갈 값은 임의로 조정하였다.
