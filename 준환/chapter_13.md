
# 12 컬렉션 프레임워크
## 🌅 공부기록
1. 내부 클래스
2. 람다식
3. 스트림
## 🧠 배운 점
### 내부 클래스
- 선언하는 위치나 예약어에 따라 네가지 유형
  1. 인스턴스 내부 클래스
  2. 정적 내부 클래스
  3. 지역 내부 클래스
  4. 익명 내부 클래스

- 인스턴스 내부 클래스
  - 인스턴스 변수를 선언할 때와 같은 위치에 선언하며, 외부 클래스 내부에서만 생성하여 사용하는 객체를 선언할 때 사용
  - 외부 클래스를 먼저 생성하지 않고 인스턴스 내부 클래스를 사용할 수 없습니다.

- 인스턴스 내부 클래스
```
package chapter13.innerclass;

class OutClass {
    private int num = 10;
    private static int sNum = 20;

    private InClass inClass;// 내부 클래스 자료형 변수를 먼저 선언

    // 외부 클래스 디폴트 생성자. 외부 클래스가 생성된 후에 내부 클래스 생성가능능
    public OutClass() {
        inClass = new InClass();
    }

    class InClass {
        int inNum = 100;

        void inTest() {
            System.out.println("OutClass num = " + num + " (외부 클래스의 인스턴스 변수)");
            System.out.println("OutClass sNum = " + sNum + " (외부 클래스의 정적 변수)");
        }
    }

    public void usingClass() {
        inClass.inTest();
    }
}

public class InnerTest {
    public static void main(String[] args) {
        OutClass outClass = new OutClass();
        System.out.println("외부 클래스 이용하여 내부 클래스 기능 호출");
        outClass.usingClass();// 내부 클래스 기능 호출출
    }
}

```
![image](https://github.com/user-attachments/assets/72c020cc-51ad-40b9-9db5-d77c1b1c224b)

- 정적 내부 클래스
  - 내부 클래스가 외부 클래스 생성과 무관하게 사용할 수 있어야 하고 정적 변수도 사용 할 수 있어야 한다면 사용
  - 내부 클래스처럼 외부 클래스의 멤버 변수와 같은 위치에 정의하며 static 예약어를 함께 사용합니다.

```
package chapter13.innerclass;

class OutClass {
    private int num = 10;
    private static int sNum = 20;

    static class InStaticClass {
        int inNum = 100;
        static int sInNum = 200;
        //정적 내부 클래스의 일반 메서드드
        void inTest() {
            System.out.println("InStaticClass inNum" +inNum+ "(내부 클래스의 인스턴스 변수 사용)");
            System.out.println("InStaticClass sInNum=" + sInNum + "(내부 클래스의 정적 변수 사용)");
            System.out.println("OutClass sNum=" +sNum + "(외부 클래스의 정적 변수 사용)");
        }
        // 정적 내부 클래스의 정적 메서드드
        static void sTest() {
            System.out.println("OutClass sNum="+sNum+"(외부 클래스의 정적 변수 사용)");
            System.out.println("InStaticClass sInNum="+sInNum+"외부 클래스의 정적 변수 사용");
        }
    }
}

public class InnerTest2 {
    public static void main(String[] args) {
        OutClass.InStaticClass sInClass = new OutClass.InStaticClass(); // 외부 클래스를 생성하지 않고 바로 정적 내부 클래스 생성 가능능
        System.out.println("정적 내부 클래스 일반 메서드 호출");
        sInClass.inTest();

        System.out.println();
        System.out.println("정적 내부 클래스의 정적 메서드 호출");
        OutClass.InStaticClass.sTest();
    }
}

```
![image](https://github.com/user-attachments/assets/2ae1a9d3-e23d-4d7e-8945-ad73389a661e)

| 정적 내부 클래스 메서드 | 변수 유형 | 사용 가능 여부 |
| --- | --- | --- |
| **일반 메서드** void inTest() | 외부 클래스의 인스턴스 변수(num) | ✕ |
|  | 외부 클래스의 정적 변수(sNum) | ○ |
|  | 정적 내부 클래스의 인스턴스 변수(inNum) | ○ |
|  | 정적 내부 클래스의 정적 변수(sInNum) | ○ |
| **정적 메서드** static void sTest() | 외부 클래스의 인스턴스 변수(num) | ✕ |
|  | 외부 클래스의 정적 변수(sNum) | ○ |
|  | 정적 내부 클래스의 인스턴스 변수(inNum) | ✕ |
|  | 정적 내부 클래스의 정적 변수(sInNum) | ○ |

- 정적 내부 클래스에서 사용하는 메서드가 정적 메서드인 경우에는 외부 클래스와 정적 내부 클래스에 선언된 변수 중 정적 변수만 사용 가능


- 지역 내부 클래스
  - 지역 변수처럼 메서드 내부에 클래스를 정의하여 사용하는 것 처럼 말한다.

```
package chapter13.innerclass;

class Outer {
    int outNum = 100;
    static int sNum = 200;

    Runnable getRunnable(int i) {
        int num = 100;

        class MyRunnable implements Runnable {
            int localNum = 10;

            @Override
            public void run() {
                System.out.println("i=" + i);
                System.out.println("num=" +num);
                System.out.println("localNum=" +localNum);
                System.out.println("outNum=" +outNum + "(외부 클래스 인스턴스 변수)");
                System.out.println("Outer.sNUm=" + Outer.sNum + "(외부 클래스 정적 변수)");
            }
        }
        return new MyRunnable();
    }
}
public class LocallnnerTest {
    public static void main(String[] args) {
        Outer out = new Outer();
        Runnable runner = out.getRunnable(10);
        runner.run();
    }
}

```
![image](https://github.com/user-attachments/assets/bed7475c-413d-4e0f-be49-d04687a33b38)


- 익명 내부 클래스
  - 클래스 이름을 사용하지 않는 클래스

![image](https://github.com/user-attachments/assets/1d8fd07f-9aa7-4f07-986c-57f4e871ed17)
![image](https://github.com/user-attachments/assets/208b97d3-eb51-41fa-9cef-15bf6fd42fea)

내부 클래스 표 정리
| 종류 | 구현 위치 | 사용할 수 있는 외부 클래스 변수 | 생성 방법 |
| --- | --- | --- | --- |
| 인스턴스 내부 클래스 | 외부 클래스 멤버 변수와 동일 | 외부 인스턴스 변수, 외부 정적 변수 | 외부 클래스를 먼저 만든 후 내부 클래스 생성 |
| 정적 내부 클래스 | 외부 클래스 멤버 변수와 동일 | 외부 정적 변수 | 외부 클래스와 무관하게 생성 |
| 지역 내부 클래스 | 메서드 내부에 구현 | 외부 인스턴스 변수, 외부 정적 변수 | 메서드를 호출할 때 생성 |
| 익명 내부 클래스 | 메서드 내부에 구현, 변수에 대입하여 직접 구현 | 외부 인스턴스 변수, 외부 정적 변수 | 메서드를 호출할 때 생성. 되거나, 인터페이스 타입 변수에 대입할 때 new 예약어를 사용하여 생성 |

### 람다식
- 함수형 프로그래밍 방식
- 람다식 문법 (매개변수) -> {실행문;}

- 함수형 인터페이스 선언하기
![image](https://github.com/user-attachments/assets/2405be59-ac45-4997-9ce7-795ab76592b8)

- 람다식 구현과 호출
![image](https://github.com/user-attachments/assets/0662dd5d-6c0c-45fc-82ab-4676a9fbbbbf)
![image](https://github.com/user-attachments/assets/62535ec0-56a4-4b39-b58e-2c171608fa1d)

- 함수형 인터페이스
  - 자바에서 참조 변수 없이 메서드를 호출할 수는 없다
  - 람다식을 구현하기 위해 함수형 인터페이스 제작 -> 인터페이스에 람다식으로 구현할 메서드 선언
  - 람다식은 하나의 메서드를 구현하여 인터페이스형 변수에 대립하므로 두 개 이상의 메서드를 가져서는 안된다.
 
- 객체 지향 프로그래밍과 람다식 비교

- 인터페이스 구현
![image](https://github.com/user-attachments/assets/b6126e35-ac65-42b6-b502-7db88b21d195)

- 추상 메서드 구현
![image](https://github.com/user-attachments/assets/73f288ae-9336-4e57-9c9b-1451b9f8fcad)

- 메서드 테스트
![image](https://github.com/user-attachments/assets/ab8d62c5-fee6-4a42-81a2-69454acc4e97)
![image](https://github.com/user-attachments/assets/a15fb6fc-4b92-4052-a363-e401955eb732)

- 람다식으로 인터페이스 구현하기
![image](https://github.com/user-attachments/assets/cba81268-7ec0-4807-8786-338248ae1ca7)
![image](https://github.com/user-attachments/assets/216c4b3d-ed05-454f-9e58-fb0644bc6c8b)

###스트림이란?
- 여러 자료의 처리에 대한 기능을 구현해 놓은 클래스

- 정수 배열에서 스트림 활용
![image](https://github.com/user-attachments/assets/b9cc9363-6aac-4443-a5c7-f1b5326d5e7d)

- ArrayList에서 스트림 활용하기
![image](https://github.com/user-attachments/assets/0806432c-29b1-4efd-a0dd-827f67d64bfb)
![image](https://github.com/user-attachments/assets/45681a86-0a21-4584-b460-b5e6051b88d7)

- 스트림의 특징
  1. 자료의 대상과 관계없이 동일한 연산을 수행한다.
  2. 한 번 생성하고 사용한 스트림은 재사용할 수 없다.
  3. 스트림의 연산은 기존 자료를 변경하지 않는다.
  4. 스트림의 연산은 중간 연산과 최종 연산이 있다.
 
- reduce() 연산
  - 내부적으로 스트림의 요소를 하나씩 소모하면서 프로그래머가 직접 지정한 기능을 수행
![image](https://github.com/user-attachments/assets/51ecfb0c-d276-4f32-a58b-f424c29a0c68)
![image](https://github.com/user-attachments/assets/dfa8ebee-df73-4bce-94e0-f9750b62ff75)




