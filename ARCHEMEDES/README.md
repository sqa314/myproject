아르키메데스의 원주율
=

## 1. 배경지식
### 1.1 아르키메데스
![example](./example.png)
<br>
아르키메데스는
<br>
임의의 원의 둘레는 정 다각형이 그 원에 내접할 때의 길이보다 길고, 외접할 때의 길이보다 작음을 이용하여
<br>
무리수 π 의 값을 알 수 있다고 생각했다.
<br>
아르키메데스는 실로 정 구십육각형을 이용하여 원주율을 3.1408 < π < 3.1429까지 계산하였다.
### 1.2 코드
본 코드는 작성자가 처음으로 개발한 소프트웨어로 C언어에 입문할 당시의 본인을 기준으로
<br>
초심자가 보고 따라 만들 수 있을 수준의 기초적인 내용을 상세히 설명한다.

## 2 코드 기초
### 2.1 #include
* #include<stdio.h>

정 n각형의 n값을 입력받기 위한 scanf_s
계산값을 출력하기 위한 printf를 포함한 여러 입출력 함수들이 포함되어 있다.
* **#include<math.h>**

정 n각형의 둘레를 계산하기 위해서는 cos sin tan와 지수의 계산이 필요하다.
* **#include<Windows.h>**

원주율 코드 자체에는 필요 없으나 gotoxy[1](39,3); system(cls); Sleep(3000);등의 시각적 직관성을 위해 사용되었다.
### 2.2 gotoxy _ 커서이동
<pre><code>void gotoxy(int x, int y)
{
	COORD Pos = { x - 1, y - 1 };	
	SetConsoleCursorPosition(GetStdHandle(STD_OUTPUT_HANDLE), Pos);
}
</code></pre>
* **COORD** 

pos배열을 포함하는 구조체 함수이다.
* **Pos**

2개의 정수로 이루어진 배열로 gotoxy의 정수 입력 x(가로)와 y(세로)[2]가 저장된다.
* **SetConsoleCursorPosition**

GetStdHandle(STD_OUTPUT_HANDLE)이라는 함수와 Pos배열을 입력으로 가지는 함수로<br>
커서의 위치를 조절하는 HANDLE을 불러내어 Pos의 위치에 가져다 놓는(반환하는) 방식으로 화면에서의 커서 좌표를 설정한다.
### 2.3 함수
* **int, double, char**

각각 정수, 고정소수점, 문자를 담을 수 있는 변수를 선언한다.
<code><pre>int i;
	double PI = 3.1415926535897932384;
	char yn;
</code></pre>위와 같이 사용된다.
* **printf**
>     printf(" %9d# %.4f < π < %.4f\n", 6 * cun, znuq * sum / 2, skrri);

정수, 고정소수점, 문자열 등을 출력할 수 있는, 가장 기본적인 출력함수로 위의 경우
> 96# 3.1408 < π < 3.1429

가 출력된다.[3]
* **scanf**
>     scanf("%d", &num);

정수, 고정소수점, 문자열 등을 입력할 수 있는, 가장 기본적인 입력함수로 위의 경우
<br>
이후 입력된 값이 num의 주소값으로 보내져 변수 num의 값으로 적용된다.
* **cos, sin, tan**
>     cos(a);

입력값에 코사인, 사인, 탄젠트 값을 구한다. 위의 경우 cos(a)의 값을 반환한다.
<br>
주의해야할 점은 60분법이 아닌 **호도법을 사용**하므로 각도를 라디안(rad) 단위로 입력해야한다.
* **hypot**
>     hypot(a);

입력값의 제곱근을 구한다. 위의 경우 √a의 값을 반환한다.
* **pow**
>     pow(b, a);

입력값의 지수 함수값을 구한다 위의 경우 a^b의 값을 반환한다.
* **Sleep**
>     sleep(3000);

코드 진행을 일정 시간 지연하는 기능으로 입력값의 1/1000초를 정지한다. 위의 경우 3초간 지연된다.
* **system**

system함수는 입력값에 따라 다양한 기능을 수행하지만 본 코드에서는
>     system("cls");

만을 사용하며 이 경우 콘솔의 모든 내용을 지운다.
* **if**
<pre><code>if (yn == 'N' || yn == 'n')
	goto end;
else
	goto here;
</code></pre>if는 경우에 따라 코드의 진행이 달라지는 분기점에 사용하는 함수로 따라오는 괄호 안의 내용이<br>참일 경우 코드의 진행을 이어가고, 거짓일 경우 바로 뒤의 코드를 생략하고 넘어간다.<br>괄호 안의 내용은 &&를 통해 and 연결, ||를 통해 or 연결 가능하며<br>함수가 끝날 때 else를 사용하면 내용이 거짓일때만 실행되는 코드를 작성할 수 있다.

* **for**
<pre><code>for(i = 0; i < 10; i ++)
{
	printf("%d",i);
	Sleep(1000);
}
</code></pre>
for는 반복문으로 따라오는 괄호안의 내용은
> for(초기 조건; 반복 조건; 1회 반복당 실행)
	
으로 이루어 지며 위의 함수를 예시로 들면
1. i = 0을 설정하며 반복을 시작
2. i < 10 인지 확인
3. i < 10이 참이라면 printf, Sleep을 차례로 실행한 후 i++(i값을 1 올림), 과정 2로 되돌아감
4. i < 10이 거짓이라면 뒤의 코드 생략
5. for함수 끝

위의 과정을 5번이 나올 때까지 반복한다. 
* **goto**

goto 함수는 코드 위 줄에서부터 아래 줄로 차례대로 실행되는 프로그램의 실행 순서를 강제로 변경하는 함수로
<br>
**코드의 직관성을 해치고, 프로그램의 오류를 유발하므로 사용하지 않는 것을 권장한다.**
<br>
사용 방법은
>     goto a;

와 같이 임의의 변수를 goto로 선언하고 프로그램의 임의의 위치에
>     a:

를 놓으면 실행순서가 즉시 a:의 위치로 이동한다.
* **return**

return은 함수의 결과값을 반환하는 함수로 본 코드에서는 main함수의 코드를 끝내는
>     return 0;

로만 사용되었다.
## 3 구조
### 3.1 선언부
<pre><code>char c;
char yn;
double PI = 3.1415926535897932384;
int i;
int sum = 6;
int num;
</code></pre>
C언어 특성상 변수의 선언이 코드에서 가장 우선되어야 한다.
<br>
다른 함수 아래에 변수의 선언이 이루어질 경우 오류가 난다.
<br>
이때 코드는 일반적으로 { }로 묶인 단위 내부을 이야기한다. 
### 3.2 입력부
<pre><code>printf("\n\n몇각형으로 실험하시겠습니까?    [3*(2^  )]각형\n최대 201326592각형 = 오차 ≤ 0.00000000000001");
	gotoxy(39, 3);
	scanf("%d", &num);</code></pre>
입력부는 사용자에게 무엇을 요구하는지 설명하기위한 printf,
<br>
사용자의 입력 커서가 위치할 곳을 지정하는 gotoxy,
<br>
사용자가 입력한 값을 받아들일 scanf_s함수로 이루어져 있다.
<br>
각각 함수에 대한 설명은 2에서 나온 내용과 같다.
### 3.2 연산부
<pre><code>if (num <= 26 && num >= 1) {
	for (i = 0; i < num;) {
		int cun = pow((double)2, i);
		double cune = 1 / (double)cun;
		double zhei = cune * (PI / 3);
		double scr = sin(zhei);
		double csr = 1 - cos(zhei);
		double znuq = hypot(scr, csr);
		double skr = tan(zhei);
		double skrri = skr * 3 * cun;
		printf(" %9d#  %.16f < π < %.16f\n", 6 * cun, znuq*sum / 2, skrri);
		i = i + 1;
		sum = sum * 2;
		Sleep(1);
	}
}
else
{
	printf("입력한 수가 잘 못 되었거나 너무 큽니다.\n오차가 커져 값을 정밀하게 표현할 수 없습니다.\n다시 입력해 주세요");
	Sleep(3000);
	goto here;
}</code></pre>

연산부는 if문을 통해 계산가능한 수인지 확인한 후
<br>
지수 함수와 삼각 함수의 계산을 for문을 통해 반복적하는 과정이다.
<br>
각 함수의 쓰임은 2에서 나온 내용과 같다.
<br>
### 3.4 재시작
<pre><code>printf("\n다시하시겠습니까 ( Y/N ) ?     [");
scanf("%c", &yn);
if (yn == 'N' || yn == 'n')
	goto end;
else if (yn == 'Y' || yn == 'y')
	goto here;
end:
return 0;</code></pre>
모든 계산이 끝난 이후에는 재시작이 가능하다.
<br>
사용자에게 재시작 여부를 묻는 질문이 나타나고
<br>
사용자의 입력을 scanf_s로 받아 if로 의사를 판단한다.
<br>
이후 goto문을 통해 원하는 방향으로 프로그램 진행을 결정한다.
## 결과
### 주의점
* 고정소수점을 double로 설정하였기 때문에 **8Byte 이진법으로 계산 가능한 소숫값까지 신뢰**할 수 있다.
* 모든 각도 계산은 **호도법**으로 이루어져 있다.
### 결과
C언어의 단순 연산으로 계산 가능한 범위는 정 201326592각형을 아르키메데스의 방식으로 적용할 수 있으며
<br>
이로 얻은 원주율 π는 3.141592653589792까지 신뢰할 수 있다.
![start](./start.png)
![result](./result.png)
<br>
[1] :gotoxy함수 내에있는 SetConsoleCursorPosition 함수는 헤더파일 WinCon.h의 함수지만 Windows.h가 WinCon.h를 포함하므로 설명은 생략한다.
<br>
[2] :임의의 문자도 상관 없다.
<br>
[3]: 설명을 위해 변수에 들어갈 값은 임의로 조정하였다.
[4]: \n은 줄바꿈을 의미한다.
