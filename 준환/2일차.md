<!--
제목 : [김준환] 2025-04-08
-->

## 🌅 공부기록

### 🧠 배운 점
기본연산자
-
횡과 연산자

+ 단항 연산자 : 항이 한 개인 연산자 ex) ++num;

+ 이항 연산자 : 항이 두 개인 연산자 ex) num1 + num2;

+ 삼항 연산자 : 항이 세 개인 연산자 ex) (5>3)? 1 : 0;

연산자 우선순위 단항 -> 이항 -> 삼항

대입 연산자
-
말 그대로 변수에 값을 대입하는 연산자
```java
int age = 24 //나이를 의미하는 age 변수에 값 24를 대입
```
+ 왼쪽 변수 와 오른쪽 변수 값을 대입을 하면 항상 오른쪽 값을 가져와서 왼쪽 변수에 대입하기 때문에
오른쪽 변수에는 항상 변수 나 상수가 와야 한다.

부호 연산자
-
+ '+' 변수나 상수 값을 양수로 만든다.
+ '-' 변수나 상수 값을 음수로 만든다. 


산술 연산자
-
+ '+' 두 항을 더합니다
+ '-' 앞에 있는 항에서 뒤에 있는 항을 뺍니다
+ '*' 두 항을 곱합니다.
+ '/' 앞에 있는 항에서 뒤에 있는 항을 나누어 몫을 구합니다.
+ '%' 앞에 있는 항에서 뒤에 있는 항을 나누어 나머지를 구합니다.

```java
public class OperationEX1 {
    public static void main(String[] args) {
        int mathScore = 90;
        int engScore = 70;

        int totalScore = mathScore + engScore; // 총점 구하기
        System.로
        System.out.println(value);
        System.out.println(num1);
        System.out.println(i);

        value = ((num1 = num1 + 10) > 10) || ((i = i + 2)< 10);
        System.out.println(value);
        System.out.println(num1);
        System.out.println(i);

        value = ((num1=num1 + 10) > 10) || ((i = i + 2) < 10); // 논리 합에서 앞 항의 결과 값이 참이므로 이 문장은 실행되지 않음 i 값은 그대로
        System.out.println(value);
        System.out.println(num1);
        System.out.println(i);
    }
}

```
![image](https://github.com/user-attachments/assets/73556ea8-5b6c-4b8e-8a2e-aa491be3cfc6)

복합 대입 연산자
-
: 대입 연산자와 다른 연산자를 조합해 하나의 연산자처럼 사용하는 연산자 이다.
+ '+=' 두 항의 값을 더해서 왼쪽 항에 대입
+ '-=' 왼쪽 항에서 오른쪽 항을 빼서 그 값을 왼쪽 항에 대입
+ '*=' 두 항의 값을 곱해서 왼쪽 항에 대입
+ '/=' 왼쪽 항을 오른쪽 항으로 나누어 그 몫을 왼쪽 항에 대입
+ '%=' 왼쪽 항을 오른쪽 항으로 나누어 그 나머지를 왼쪽 항에 대입
+ '<<=' 비트를 왼쪽으로 이동하고 그 값을 왼쪽 항에 대입
+ '>>=' 비트를 오른쪽으로 이동하고 그 값을 왼쪽 항에 대입
+ '>>>=' 비트를 오른쪽으로 이동하고 그 값을 왼쪽 항에 대입
+ '&=' 두항의 & 비트 연산 후 그 값을 왼쪽 항에 대입
+ '|=' 두 항의 | 비트 연산 후 그 값을 왼쪽 항에 대입
+ '^=' 두 항의 ^ 비트 연산 후 그 값을 왼쪽 항에 대입
  
조건 연산자
-
+ 조건식 ? 결과1 : 결과2; 조건식이 참이면 결과 1 거짓이면 결과 2를 선택
```java
// 조건 연산자를 사용하여 부모님의 나이 비교하기기
public class OperationEx4 {
    public static void main(String[] args) {
        int fatherAge = 45;
        int motherAge = 47;

        char ch;
        ch = (fatherAge > motherAge)? 'T' : 'F';

        System.out.println(ch);
    }
}
```
![image](https://github.com/user-attachments/assets/12a7d731-94a6-47aa-9e22-0e81904bc2e4)

비트 연산자
-
+ '|' 비트 값이 하나라도 1이면 연산 결과 값이 1이 됩니다.
+ '^' 같은 값이면 0, 다른 값이면 1의 결과 값을 갖습니다.
+ '~' 비트값을 0 => 1로 1 => 0 으로 바꾸는 연산자
+ 비트 이동 연산자
```java
public class OperationEx5 {
    public static void main(String[] args) {
        int num = 0B00000101;

        System.out.println(num << 2); //왼쪽으로 2비트 이동 00010100 (20)
        System.out.println(num >> 2); //오른쪽으로 2비트 이동 00000001 (1)
        System.out.println(num >>> 2); //오른쪽으로 2비트 이동 00000001 (1)

        System.out.println(num); // num에 값을 대입하지 않았기 때문에 기존 값 그대로 출력

        num = num << 2; // 원쪽으로 2비트 이동한 값을 다시 num에 대입
        System.out.println(num);
    }
}

// 연산자 우선순위
// 단항 연산자가 가장 높고 이항, 삼항 연산자 순서입니다.
// 대입 연산자의 우선순위가 가장 낮습니다.
// 산술 관계 논리 대입 연산자 순서로 우선순위를 가지며 ()의 우선순위가 가장 높습니다.

```
![image](https://github.com/user-attachments/assets/00c5ada5-6080-4b15-91c0-3551b26038af)
-
조건문
-
+ 조건에 따라 다른 문장을 선택 할 수 있도록 프로그래밍 하는 것

if문과 if~else문
-
+ if 조건 마다 각각 비교
```code
if(조건식){
  수행문; //조건식이 참일 경우에 이 문장을 수행
}
```
+if~else 하나의 조건을 만족하면 나머지 조건을 비교하지 않고 다음 수행문으로 이동
```code
if(조건식){
  수행문1; //조건식이 참일 경우에 이 문장을 수행
}
else{
  수행문2; //조건식이 거짓일 경우에 이 문장을 수행
}
```
```java
public class ifExample1 {
    public static void main(String[] args) {
        int age = 7;
        if(age >= 8)
        {
            System.out.println("학교에 다닙니다.");
        }
        else
        {
            System.out.println("학교에 다니지 않습니다.");
        }
    }
}
```
![image](https://github.com/user-attachments/assets/fdcb33a0-2f0e-4f80-a89a-7ec0ab79c22e)

여러개의 조건이 필요한 경우
```java
public class ifExample2 {
    public static void main(String[] args) {
        int age = 9;
        int charge;

        if(age < 8){
            charge = 1000;
            System.out.println("취학 전 아동입니다.");
        }
        else if(age < 14){
            charge = 2000;
            System.out.println("초등학생입니다.");
        }
        else if(age < 20){
            charge = 2500;
            System.out.println("중,고등학생입니다.");
        }
        else{
            charge = 3000;
            System.out.println("일반인입니다.");
        }
        System.out.println("입장료는"+charge+"원입니다.");
    }
}
```
![image](https://github.com/user-attachments/assets/451829ed-7155-4593-a97b-4f67ebcdcc8f)

swich-case문
-
주로 조건이 하나의 변수 값이나 상수 값으로 구분되는 경우 사용
```java
public class SwitchCase {
    public static void main(String[] args) {
        int ranking = 1;
        char medalColor;

        switch (ranking) {
            case 1: medalColor = 'G';
                break;
            case 2: medalColor = 'S';
                break;
            case 3: medalColor = 'B';
                break;
            default:
                medalColor = 'A';
        }
        System.out.println(ranking + "등 메달의 색깔은" + medalColor + "입니다.");
    }
}
```
![image](https://github.com/user-attachments/assets/c4d5e127-018d-4029-8932-adb68f1d16e7)

+ break switch-case문의 수행을 멈추고 빠져나가도록 만듬
case문에 문자열 사용하기
```java
public class SwitchCase2 {
    public static void main(String[] args) {
        String medal = "Gold";

        switch (medal) {
            case "Gold":
                System.out.println("금메달입니다."); 
                break;
            case "Silver":
                System.out.println("은메달입니다."); 
                break;
            case "Bronze":
                System.out.println("동메달입니다.");
                break;
            default:
                System.out.println("메달이 없습니다");
                break;
        }
    }
}
```
![image](https://github.com/user-attachments/assets/310da6a8-cca0-4dfa-884a-134501acc570)

반복문
-
반복적인 일을 처리하기 위해 사용

while문
-
```code
while(조건식){
수행문1;
...
} //조건식이 참인 동안 반복 수행
  수행문2;
  ...
```
```java
public class WhileExmaple1 {
    public static void main(String[] args) {
        int num = 1;
        int sum = 0;

        while (num <= 10) { // num값이 10보다 작거나 같을 동안
            sum += num; // 합계를 뜻하는 sum에 num을 더하고
            num++; // num에 1씩 더해 나감감

        }
        System.out.println("1부터 10까지의 합은"+sum+"입니다");
    }
}
```
![image](https://github.com/user-attachments/assets/9ee2d99d-23b7-43ea-92ad-6eccc6cba1da)

do-while문
-
do-while 문은 무조건 한번 수행한 후 조건식을 검사 즉 조건이 부합 하는지는 마지막에 검사
```code
do{
수행문1;
...
}while(조건식);
  수행문2;
  ...
```
```java
public class DoWhileExaple {
    public static void main(String[] args) {
        int num = 1;
        int sum = 0;

        do{
            sum += num;
            num++; // 조건식이 참이 아니더라도 무조건 한 번 수행함
        }while(num <= 10);

        System.out.println("1부터 10까지의 합은" +sum+"입니다.");
    }
}
```
![image](https://github.com/user-attachments/assets/dd227e0b-d398-40ba-a3ce-8e5cba730ca1)

for문
- 
반복문을 구현하는데 필요한 요소는(변수의 초기화식, 조건식, 증감식) 어떤 조건부터 어떤 조전까지 반복 수행을 했는지 한눈에 알아 볼 수 있어서 반복문중 가장 많이 사용
```code
for(초기화식; 조건식; 증감식){
  수행문
}
```
for문의 수행 순서
![image](https://github.com/user-attachments/assets/495be40f-9abc-4f05-bc28-3d22598b0342)
1부터 10까지 더하는 과정을 for문으로 구현
```java
public class ForExample1 {
    public static void main(String[] args) {
        int i;
        int sum;
        for(i = 1, sum = 0; i <= 10; i++){
            sum += i;
        }

        System.out.println("1부터 10까지의 합은"+sum+"입니다");
    }
}
```
![image](https://github.com/user-attachments/assets/1687226a-c2e7-4abc-b068-ae36598fd616)

+ 중첩된 반복문 ex)구구단
```java
public class NestedLoop {
    public static void main(String[] args) {
        int dan;
        int times;
        for(dan=2; dan<=9; dan++){
            for(times = 1; times <= 9; times++){
                System.out.println(dan + "X" + times + "=" + dan * times);
            }
            System.out.println( );   
        }
    }
}
```
![image](https://github.com/user-attachments/assets/cd053f2d-c088-4160-9aab-699dcda50b9a)
-
중첩 반복문의 수행 순서
![image](https://github.com/user-attachments/assets/5f173a0d-004a-49f0-a190-e6a73a27e85d)
-
continue문
-
continue문을 만나면 이후의 문장은 수행하지 않고 for문의 처음으로 돌아가 증감식을 수행
```java
public class ContunueExample {
    public static void main(String[] args) {
        int total = 0;
        int num;

        for(num=1; num<=100; num++){
            if(num%2 == 0)
                continue; // for(num=1; num<=100; num++) <- 여기로 다시 이동
            total += num;
        }
        System.out.println("1부터 100까지의 홀수의 합은:"+total+"입니다");
    }
}
```
![image](https://github.com/user-attachments/assets/3e8ffb0d-9dbb-4566-87e4-2169a912cb88)

