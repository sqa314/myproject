

아르키메데스의 원주율
=

1.배경지식
-

아르키메데스는<br>임의의 원의 둘레는 정 다각형이 그 원에 내접할 때의 길이보다 길고, 외접할 때의 길이보다 작음을 이용하여<br>무리수 π 의 값을 알 수 있다고 생각했다.<br>아르키메데스는 실재로 정 구십육각형을 이용하여 원주율을 3.1408 < π < 3.1429까지 계산하였다.

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
### 2.2 gotoxy
함수 원형 void gotoxy(int a, int b)
### 2.3 main
사실 이 코드는 main 한 블럭으로 별도의 함수정의나 객체화 없이 구성되어 있으므로<br>위 줄에서부터 아래 줄로 내려오는 C언어의 특성을 그대로 따라오면 쉽게 이해할 수 있다.
* printf();
<br>
[1]:gotoxy함수 내에있는 SetConsolCursorPosition 함수는 헤더파일 WinCon.h에 포함되어 있으나 Windows.h가 WinCon.h를 포함하므로 생략한다.
This is a text with a footnote1.

This is a text with a
footnote[^2].

[^2]: And here is the definition.
