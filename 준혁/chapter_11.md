## 13. 내부 클래스, 람다식, 스트림
### 13-1 내부 클래스

> 클래스 내부에 선언된 클래스

```java
class outer {
	class inner {}
}
```

- 익명 내부 클래스
```java
class outer {
	type getType() {
		return new type() {
			@override
			public void run() {
				// todo
			}
		};
	}
}
```

### 13-2 람다식

> 익명 함수

```java
(int x, int y) -> {return x + y};
```

- 괄호 생략 문법 (매개변수가 2개 이상인 경우 불가)
```java
str -> {System.out.println(str);}
```

- 중괄호 생략 문법 (구현이 한 줄일 경우만 가능)
```java
str -> System.out.println(str);
```

- return 예약어 생략 문법
```java
(x, y) -> x + y;
str -> str.length();
```

- 함수형 인터페이스 생성 시 내부 메서드는 하나만 존재해야한다.
```java
@FuntionalInterface // 함수형 인터페이스에 2개 이상의 메서드 선언을 막기위한 어노테이션
interface Inter {
	int add (int a, int b);
}

public class a {
	public static void main(string[] args) {
		int a = 1;
		int b = 2;
		// 람다식 사용 시 인터페이스를 정의하는 클래스없이 바로 인스턴스를 만들어 사용한다.
		Inter inter = (x, y) -> {return x + y};
		System.out.println(inter.add(a, b));
	}
}
```

### 13-3 스트림

> 여러 자료 처리에 대한 기능을 구현해 놓은 클래스

```java
int[] arr = {1,2,3,4,5};
// stream을 이용해 배열의 요소를 하나씩 출력하는 foreach문
Arrays.stream(arr).foreach(n -> System.out.println(n));
```

- 스트림 연산
	- 중간 연산
		```java
// filter 연산
sList.stream().filter(s -> s.length() >= 5).foreach(s -> System.out.println(s));
// map 연산
customerList.stream().map(c -> c.getName()).foreach(s -> System.out.println(s));
		```

	- 최종 연산
```java
Arrays.stream(arr).sum(); // 요소의 총합
Arrays.stream(arr).count(); // 요소의 개수(long 타입)
Arrays.stream(arr).foreach(n -> System.out.println(n)); 
// 등등...
```

#### 스트림 특징
- 대상과 관련없이 동일한 연산 수행
- 재사용 불가
- 기존 자료 변경 X
- 중간 연산과 최종 연산이 존재함