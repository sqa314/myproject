포커 시뮬레이터
=
## 1. 배경지식
### 1.1 포커

포커는 여러명의 플레이어가 플레잉 카드를 나누어 가지고 카드의 숫자와 무늬의 조합을 겨루는 게임이다.
이때 조합[1]을 족보라고 하고 우리나라에서 통용되는 족보는 다음과 같다.

|족보|조건|
|-|-|
|**로얄 스트레이트 플러쉬**|무늬가 같은 A,K,Q,J,10|
|<mid>**스트레이트 플러쉬**</mid>|무늬가 같고 연속되는 숫자 5장|
|**포카드**|숫자가 같은 카드 4장|
|**풀하우스**|숫자가 같은 카드가 따로 3장, 2장 총 5장|
|**플러쉬**|무늬가 같은 카드 5장|
|**스트레이트**|연속되는 숫자 5장|
|**트리플**|숫자가 같은 카드 3장|
|**투 페어**|숫자가 같은 카드가 따로 2장, 2장 총 4장|
|**원 페어**|숫자가 같은 카드가 2장|
|**노 페어**|위의 조합 어느것도 해당되지 않는 조합|
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

이제 배열된 카드들을 족보에 만족하는지를 판단하기 쉽도록 배열해야 한다.

|입력|출력|
|-|-|
|int[][] card|int[][] arr|
<pre><code>int[][] arr = new int[card.length][3];
for(i = 0; i < card.length; i++) {
	arr[i][0] = card[i][1];
	arr[i][1] = card[i][2];
	arr[i][2] = card[i][2];
}</code></pre>
포커조합은 숫자, 무늬, 숫자+무늬의 조합으로 이루어지기 때문에 각각에 필요한 다양한 배열방식을 준비한다.
<br>
위 코드에서 arr[i][0]는 숫자 정렬
<br>
arr[i][1]은 숫자+무늬 정렬
<br>
arr[i][2]는 무늬 정렬에 사용된다
<pre><code>for(j=0 ; j < card.length-1; j++)
{
	for(k=j+1 ; k < card.length; k++)
	{
		if(arr[j][0] <= arr[k][0])
		{
			temp1 = arr[j][0];
			temp2 = arr[j][1];
			arr[j][0] = arr[k][0];
			arr[j][1] = arr[k][1];
			arr[k][0] = temp1;
			arr[k][1] = temp2;
		}
		if(arr[j][2] <= arr[k][2]) {
			temp3 = arr[j][2];
			arr[j][2] = arr[k][2];
			arr[k][2] = temp3;
		}
	}
}
return arr;</code></pre>
C언어에서도 흔히 볼 수 있는 배열 방식이다. 자세히 보면 숫자와 숫자+무늬는 큰 수부터,
<br>
무늬는 무늬별로 정렬하고 있다.
#### 2.2.3 rank
|입력|출력|
|-|-|
|int[][] arr|int result|
<pre><code>Rank a = new Rank();
if (a.RSP(arr) == true) 
	return 10;
else if (a.StF(arr) == true)
	return 9;
else if (a.Fcd(arr) == true)
	return 8;
else if (a.FuH(arr) == true)
	return 7;
else if (a.Fsh(arr) == true)
	return 6;
else if (a.Str(arr) == true)
	return 5;
else if (a.Trp(arr) == true)
	return 4;
else if (a.TwP(arr) == true)
	return 3;
else if (a.OnP(arr) == true)
	return 2;
else
	return 1;</code></pre>
이제 판단하기 쉽도록 잘 정렬된 배열을 Rank class에 보내주고
<br>
Rank class에서 처리가 끝난 결과를 받을 준비가 되었다.
### 2.3 Rank

Rank class는 우리가 보는 숫자의 조합, 무늬의 조합을
<br>
수학적으로, 프로그래밍 적으로 어떻게 처리하는가를 다룬다.
<pre><code>int i,j,k,l = 0;
int count = 0;
int count1 = 0;
int count2 = 0;
public void cls() {
	count = 0;
}</code></pre>
아래 나오는 모든 판단은 위 코드를 기본가정하고,
<br>
오름차순 정렬된 n장의 패가 각 조건을 만족하는가 여부를 판단한다.
<br>
실제 코드에서도 후술 순서대로 진행하며, 위쪽에서 판별된 조합은 아래쪽에서는 자동으로 제외된다.
* **로얄 스트레이트 플러쉬**

<pre><code>public boolean RSF(int[][] a) {
	int s[] = new int[5];
	int p[] = {2,3,5,7};
	j = 0;
	for(i = 0;i < a.length-1; i++) {
		if (s[0] == 0)
			s[0] = a[i][1];
		if (a[i][0] == a[i+1][0] + 1) {
			s[j+1]=a[i+1][1];
			j++;
			count++;
		}
		else if (a[i][0] == a[i+1][0])
			s[j] = s[j] * a[i+1][1];
		else {
			cls();
			s[0] = 0;
			j = 0;
		}
		if(count == 4){
			for(k = 0;k < p.length; k++){
				for(l = 0; l < s.length; l++){
					if (s[l] % p[k] == 0 ){
						count1++;
					}
				}
				if(count1 == 5 && a[i][0] == 9){	
					count1 = 0;
					cls();
					return true;
				}
				count1 = 0;
			}
			for(l = 0; l < s.length-1; l++){
				s[l] = s[l+1];
			}
			s[4] = 0;
			j--;
			count--;
		}
	}	
	cls();
	count1 = 0;
	return false;
}</code></pre>
1. 숫자가 연속되는 5개의 패가 있는지 확인
2. 5개의 숫자가 무늬별로 있을 수 있기 때문에 별도의 배열에 무늬에 해당하는 소수를 곱함
3. 숫자별 무늬 배열이 하나의 소수로 모두 나누어 떨어진다면 하나의 무늬로된 5개의 연속된 수 존재
4. 5개의 연속된 수가 A K Q J 10이어야 하기 때문에 마지막 순서가 10임을 확인 (코드에서는 9)
* **스트레이트 플러쉬**
<pre><code>public boolean StF(int[][] a) {
	int s[] = new int[5];
	int p[] = {2,3,5,7};
	j = 0;
	for(i = 0;i < a.length-1; i++) {
		if (s[0] == 0)
			s[0] = a[i][1];
		if (a[i][0] == a[i+1][0] + 1) {
			s[j+1]=a[i+1][1];
			j++;
			count++;
		}
		else if (a[i][0] == a[i+1][0])
			s[j] = s[j] * a[i+1][1];
		else {
			cls();
			s[0] = 0;
			j = 0;
		}
		if(count == 4){
			for(k = 0;k < p.length; k++){
				for(l = 0; l < s.length; l++){
					if (s[l] % p[k] == 0 ){
						count1++;
					}
				}
				if(count1 == 5){
					count1 = 0;
					cls();
					return true;
				}
				count1 = 0;
			}
			for(l = 0; l < s.length-1; l++){
				s[l] = s[l+1];
			}
			s[4] = 0;
			j--;
			count--;
		}
	}	
	cls();
	count1 = 0;
	return false;
}</code></pre>
1. 로얄 스트레이트 플러쉬의 1~4까지의 조건과 같다.
* **포카드**
<pre><code>public boolean Fcd(int[][] a) {
	for(i = 0; i < a.length-1; i++) {
		if (a[i][0] == a[i+1][0])
			count++;
		else
			cls();
		if (count == 3) {
			cls();
			return true;
		}
	}
	cls();
	return false;
}</code></pre>
1. 배열의 다음수가 같은 수인지 확인
2. 있다면 count++ 없다면 count = 0
3. count가 3이면, 즉 같은수가 4번 연속 나온다면 포카드
* **풀 하우스**
<pre><code>public boolean FuH(int[][] a) {
	int count1 = 0;
	int count2 = 0;
	for(i = 0;i < a.length-1; i++) {
		if (a[i][0] == a[i+1][0]) {
			count++;
			count2++;
		}
		else
			cls();
		if (count == 2)
			count1 = 1;
		if (count2 == 3 && count1 == 1) {
			count2 = 0;
			count1 = 0;
			cls();
			return true;
		}
	}
	cls();
	count2 = 0;
	count1 = 0;
	return false;
}</code></pre>
1. 배열의 다음 수가 같은 수인지 확인
2. 있다면 count++, count2++ 없다면 count = 0
3. count2가 2 이상이면, 즉 같은 수가 3번 연속 나온다면 count1 = 1;
4. count1가 1이고 count2가 3이면 풀 하우스
* **플러쉬**
<pre><code>public boolean Fsh(int[][] a) {
	for(i = 0;i < a.length-1; i++) {
		if (a[i][2] == a[i+1][2])
			count++;
		else
			cls();
		if (count == 4) {
			cls();
			return true;
		}
	}
	cls();
	return false;
}</code></pre>
1. 무늬에 따라 순서대로 정렬된 배열에 포카드와 같은 방법으로 5개의 같은 수가 있는지 확인
* **스트레이트**
<pre><code>public boolean Str(int[][] a) {
	for(i = 0;i < a.length-1; i++) {
		if (a[i][0] == a[i+1][0] + 1)
			count++;
		else if (a[i][0] == a[i+1][0])
			;
		else
			cls();
		if (count == 4) {
			cls();
			return true;
		}
	}
	cls();
	return false;
}</code></pre>
1. 배열의 다음수가 연속된 수인지 혹은 같은 수인지 확인
2. 연속된 수라면 count++, 같은 수라면 유지, 둘 다 아니라면 count = 0;
3. count가 4라면, 즉 연속된 수가 5개 있다면 스트레이트
* **트리플**
<pre><code>public boolean Trp(int[][] a) {
	for(i = 0;i < a.length-1; i++) {
		if (a[i][0] == a[i+1][0])
			count++;
		else
			cls();
		if (count == 2) {
			cls();
			return true;
		}
	}
	cls();
	return false;
}</code></pre>
1. 포카드의 절차와 동일하며 다만 4개의 같은 수가 아닌 3개의 같은 수를 찾는다.
* ** 투 페어**
<pre><code>public boolean TwP(int[][] a) {
	for(i = 0;i < a.length-1; i++) {
		if (a[i][0] == a[i+1][0])
			count++;
		if (count == 2) {
			cls();
			return true;
		}
	}
	cls();
	return false;
}</code></pre>
1. 배열의 다음수가 같은 수인지 확인
2. 있다면 count++
3. count가 2 이상이면 투 페어
* **원 페어**
<pre><code>public boolean OnP(int[][] a) {
	for(i = 0;i < a.length-1; i++) {
		if (a[i][0] == a[i+1][0])
			return true;				
	}
	return false;
}</code></pre>
1. 포카드의 절차와 동일하며 다만 4개의 같은 수가 아닌 2개의 같은 수를 찾는다.
<br>
### 3. 결과

위 코드를 실행해 7장의 카드로 1,000,000번의 플레이를 한 결과 실제 포커 확률과 0.01%이내의 오차를 가지는 결과를 얻을 수 있었고, 실행시간은 약 1 백만 번 당 30초가량 소요되었다.
<br>
[1] : 국가, 지역마다 규칙이 다르다.
