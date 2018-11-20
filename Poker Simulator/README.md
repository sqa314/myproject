포커 시뮬레이터
=
## 1. 배경지식
### 1.1 포커

포커는 여러명의 플레이어가 플레잉 카드를 나누어 가지고 카드의 숫자와 무늬의 조합을 겨루는 게임이다.
이때 조합[1]을 족보라고 하고 우리나라에서 통용되는 족보는 다음과 같다.
* **로얄 스트레이트 플러쉬**

무늬가 같은 A,K,Q,J,10
* **스트레이트 플러쉬**

무늬가 같고 연속되는 숫자 5장
* **포카드**

숫자가 같은 카드 4장
* **풀하우스**

숫자가 같은 카드가 따로 3장, 2장 총 5장
* **플러쉬**

무늬가 같은 카드 5장
* **스트레이트**

연속되는 숫자 5장
* **트리플**

숫자가 같은 카드 3장
* **투 페어**

숫자가 같은 카드가 따로 2장, 2장 총 4장
* **원 페어**

숫자가 같은 카드가 2장
* **노 페어**

위의 조합 어느것도 해당되지 않는 조합 
### 1.2 자바

자바 프로그래밍의 가장 큰 특징은 객체화로 모든 코딩이 블럭처럼 나뉘어진다고 생각하면 편하다.
<br>
기존의 위에서 아래로 읽어내려가며 실행하는 C언어처럼 코딩할 수도 있으나,
<br>
객체화를 통해 훨씬 유연하고 다양한 방식의 코딩이 가능하다.
### 1.3 기초함수

이번 설명에서는 출력, 입력, 선언과 같은 기본적인 함수를 포함한 자바 전반에 대한 설명은 생략하고,
<br>
프로그램이 어떻게 구성 되었는지 설명한다.
## 2. 클래스
### 2.1 main(poker)
<pre><code>public class poker {
	public static void main(String[] args) {
		int n;
		int i;
		int num;
		int result;
		int[][] card;
		Scanner scan = new Scanner(System.in);
		Play game = new Play();
		System.out.println("카드 장 수를 설정해주십시오 [5,6,7]");
		n = scan.nextInt();
		System.out.println("몇 번 실험하시겠습니까");
    num = scan.nextInt();
    for(i = 0; i < num; i++) {
			card = game.shuffle(n);
      result = game.rank(game.array(card));
			System.out.println(result);
		}
	}
}</code></pre>
C언어에서의 main함수와 다르게 자바에서의 main은 다른 객체를 호출하거나 활용하는 용도로 쓰인다.
### 2.2 Play
#### 2.2.1 shuffle
|입력|출력|
|-|-|
|int n|int[][] card|
<pre><code>int[][] card = new int[n][3];
for(i = 0; i < n; i++) {
  newCard = rand.nextInt(52);
  card[i][0]= newCard;
 }</code></pre>
우선 카드의 장 수를 입력받아 2차원 배열을 생성한 후 랜덤한 숫자를 넣는다.
<pre><code>for(check = false;check == false;) {
	if(i==0)
		check = true;
	for(j = 0;j < i && card[i][0]!= card[j][0];j++) {
		if (j == i-1) 
			check = true;
	}
}</code></pre>
플레잉 카드에는 중복되는 카드가 없으므로 랜덤 할당 한번 할 때마다 중복을 확인해야 한다.
<pre><code>card[i][1] = newCard % 13;
switch(newCard / 13) {
  case 0:
    card[i][2] = 1;
    break;
  case 1:
    card[i][2] = 2;
    break;
   case 2:
    card[i][2] = 3;
    break;
  case 3:
    card[i][2] = 4;
    break;
}</code></pre>
랜덤을 통해서 얻은 서로 다른 카드들을 우리가 아는 A ~ K, ◇♣♡♠에 해당하는 숫자로 배열에 할당한다. 
#### 2.2.2 array
<br>
[1] : 국가, 지역마다 규칙이 다르다.
