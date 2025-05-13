++num
num1 + num2;
(5 > 3) ? 1: 0;

package chapter;

public class Hellojava {
  public static void main(String[] args) {
	int mathScore = 90;
	int engScore = 70;
	 
	int totalScore = mathScore + engScore;
	System.out.println(totalScore);
			
	double avgScore = totalScore / 2.0;
	System.out.println(avgScore);
    }
}
   
 
!= -> 두 개의 항이 다르면 참, 아니면 거짓을 반환환
... 조건식, 반복문 제어할 때 사용


&& -> 논리 곱
|| -> 논리 합
!  -> 부정(참인 경우 거짓으로, 거짓인 경우 참으로 변경)


<복합 대입 연산자>
ex.
num1 += 2; -> num1 = num1 + 2;


<연산자> *암호화에 활용 됨
|(OR) -> 비트 값이 하나라도 1이면 연산 결과 값이 1이 돤다.
^(XOR) -> 같은 값이면 0, 다른 값이면 1의 결과 값을 갖는다.
~(반전) -> 0은 1로, 1은 0으로 바꾼다.
<<, >>, >>>(차이가 있다면 무조건 0)
*비트를 이동했다고 해서 num 값이 바로 변하진 않는다.
-> num에 '대입'을 해주어야 바뀐다.



if(조건식) {
    수행문1
}

else if(else){
    수행문2
}

<조건 연산자>
조건식 ? 결과1 : 결과2;
-> 조건식이 참이면 결과1, 조건식이 거짓이면 결과2 선택 됨

switch() {
    case 1 : ;
            break;
    .
    .
    .
    default : ;
}


Q. for과 while문의 차이?
A. for은 반복 횟수를 정확히 아는 경우, while은 조건만 중요할 때
ex.
for (int i = 0; i < 5; i++) {
    System.out.println("i는 " + i);
}

int i = 0;
while (i < 5) {
    System.out.println("i는 " + i);
    i++;
}


<do-while문>
✅ 언제 do-while을 쓰냐면?
-사용자에게 최소 한 번은 입력을 받아야 할 때
-메뉴 보여주고 나서 계속 반복할지 물어볼 때
ex.
Scanner sc = new Scanner(System.in);
String input;

do {
    System.out.print("계속하려면 y를 입력: ");
    input = sc.nextLine();
} while (input.equals("y"));


<continue문>
특정 조건에서는 수행하지 않고 건너뛰어야 할 때 사용

 
<break문>
조건을 만족하면 다른 조건을 더 이상 비교하지 않고 반복문을 빠져나온다.