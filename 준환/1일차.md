<!--
제목 : [이름] 2025-04-07
-->

## 🌅 공부기록

### 🧠 배운 점
- 변수의 선언과 값을 대입, 변수 초기화
```java
int level; //정수형 변수 level을 선언
level = 10; // 값을 10을 level 변수에 대입
int level = 10; //level 변수 선언과 동시에 값을 대입(초기화)
``` 
- 논리 자료형
```java
public class BooleanEx {
    public static void main(String[] args) {
        boolean isMarried = true; //boolean 변수를 선언하고 초기화화
        System.out.println(isMarried);
    }
}
// boolean형 변수는 true 나 false만 대입할 수 있고 그 결과 값도 true,false로 출력이 된다
``` 
- 상수와 리터널
```java
public class Constant {
    public static void main(String[] args) {
        final int MAX_NUM = 100; // 선언과 동시에 초기화
        final int MIN_NUM;

        MIN_NUM = 0; // 사용하기 전에 초기화 초기화 하지 않으면 오류 발생

        System.out.println(MAX_NUM);
        System.out.println(MIN_NUM);

        //MAX_NUM = 1000; 오류 발생. 상수는 값을 변경할 수 없음
    }
}
// 상수를 사용하면 편리한 이유 내부에서 반복적으로 사용하고 변하지 않아야 하는 값을 상수로 선언하여 사용하면 좋다
``` 
```java
public class liternal {
    public static void main(String[] args) {
        long population = 8000000000L;
        final float PI = 3.14f; // float이라서 F,f

        System.out.println("Population: " + population); //int보다 더 큰 범위의 정수를 표현할 수 있고, 리터널 값 뒤에 L 또는 l을 붙여서 long형임을 명시시
        System.out.println("PI: " + PI); //
    }
    
}

``` 
- 형 변환
하나의 자료형으로 통일한 후 연산을 해야 한다
기본 원칙
1. 바이트 크기가 작은 자료형에서 큰 자료형으로 형 변환은 자동으로 이루어진다.
2. 덜 정밀한 자료형에서 더 정밀한 자료형으로 형 변환은 자동으로 이루어진다.
- 묵시적 형 변환, 명시적 형 변환
```java
public class ImplicitConversion {
    public static void main(String[] args) {
        byte bnum = 10;
        int inum = bnum; //byte형 값이 int형 변수로 대입됨

        System.out.println(bnum);
        System.out.println(inum);

        int inum2 = 20;
        float fnum = inum2; // int형 값이 float형 변수로 대입됨

        System.out.println(inum);
        System.out.println(fnum);

        double dnum;
        dnum = fnum + inum;
        System.out.println(dnum);
    }    
}

``` 
```java
public class ExplicitConversion {
    public static void main(String[] args) {
        double dnum1 = 1.2;
        float fnum2 = 0.9F;

        int inum3 = (int)dnum1 + (int)fnum2; //두 실수가 각각 형 변환되어 더해짐
        int inum4 = (int)(dnum1 + fnum2); // 두 실수의 합이 먼저 계산되고 형 변환됨됨

        System.out.println(inum3);
        System.out.println(inum4);
    }
}

``` 
