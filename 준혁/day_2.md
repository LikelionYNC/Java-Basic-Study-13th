
## 3. 자바의 여러가지 연산자
### 03-1 기본 연산자
- 산술 연산자
```java
public class day2 {
    public static void main(String[] args) {
        System.out.println(10+3);
        System.out.println(10-3);
        System.out.println(10*3);
        System.out.println(10/3);
        System.out.println(10%3);
    }
}
```

```sh
>> java -cp src.day2
13
7
30
3
1
```
- 비교 연산자
```java
public class day2 {
    public static void main(String[] args) {
        System.out.println(1>3);
        System.out.println(1<3);
        System.out.println(1>=3);
        System.out.println(1>=3);
        System.out.println(1==3);
        System.out.println(1!=3);
    }
}
```

```bash
>> java -cp src.day2
false
true
false
false
false
true
```

- 논리 연산자
```java
public class day2 {
    public static void main(String[] args) {
        System.out.println(true&&false);
        System.out.println(true||false);
        System.out.println(!false);
    }
}
```

```sh
>> java -cp src.day2
false
true
true
```

### 03-2 비트 연산자
- AND
```java
public class day2 {
    public static void main(String[] args) {
        int a = 0b0010100;
        int b = 0b0101101;
        int c = a & b; // 0b100 = 4
        
        System.out.println(c);
    }
}
```

```sh
>> java -cp src.day2
4
```

- OR
```java
public class day2 {
    public static void main(String[] args) {
        int a = 0b0010100;
        int b = 0b0101101;
        int c = a | b; // 0b111101 = 61
        
        System.out.println(c);
    }
}
```

```sh
>> java -cp src.day2
61
```

- XOR
```java
public class day2 {
    public static void main(String[] args) {
        int a = 0b0010100;
        int b = 0b0101101;
        int c = a ^ b; // 0b111001 = 57
        
        System.out.println(c);
    }
}
```

```sh
>> java -cp src.day2
57
```

- NOT
```java
public class day2 {
    public static void main(String[] args) {
        short a = 0b0010100;
  
        System.out.println(Integer.toBinaryString(~a));
    }
}```

```sh
>> java -cp src.day2
11111111111111111111111111101011
```

## 4. 제어 흐름 이해하기
### 04-1 조건문
- if, else if
```java
public class day2 {
    public static void main(String[] args) {
	    if (true) {
            System.out.println("실행됨");
        }
  
        if (false) {
            System.out.println("실행 안됨");
        } else {
            System.out.println("실행되나 else는 필수적으로 사용되는 조건은 아님님");
        }
  
        if (false) {
            System.out.println("실행 안됨");
        } else if (true) {
            System.out.println("실행됨 else 보다 우선적으로 실행됨됨");
        }
    }
}
```

```sh
>> java -cp src.day2
실행됨
실행되나 else는 필수적으로 사용되는 조건은 아님
실행됨 else 보다 우선적으로 실행됨
```

- Switch
```java
public class day2 {
    public static void main(String[] args) {
        switch(1) {
            case 1:
                System.out.println("실행됨");
                break;
            default :
                System.out.println("위 case에서 정의되지 않는 케이스는 default로 실행");
        }
    }
}
```

```sh
>> java -cp src.day2
실행됨
```

### 04-2 반복문
- for
```java
public class day2 {
    public static void main(String[] args) {
	    for (int i = 0; i < 10; i++) {
            System.out.println(i+1);
        }
    }
}
```

```sh
>> java -cp src.day2
1
2
3
4
5
6
7
8
9
10
```

- while
```java
public class day2 {
    public static void main(String[] args) {
		int cnt = 0;
        while(++cnt < 10);
        System.out.println(cnt);
	}
}
```

```sh
>> java -cp src.day2
10
```

- Do - while
```java
public class day2 {
    public static void main(String[] args) {
	    int cnt = 0;
        do {
            cnt++;
        } while(false);
        System.out.println(cnt);
    }
}
```

```sh
>> java -cp src.day2
1
```