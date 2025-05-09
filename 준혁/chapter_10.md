## 12. 컬렉션 프레임워크
### 12-1 제네릭
여러 참조 자료형을 사용할 수 있도록 프로그래밍 하는 것

제네릭

```java
// 제너릭 클래스의 선언
public class Generic<T> {
	// 제너릭 타입의 멤버변수
	private T i;

	// 제너릭 타입의 매개변수
	public void setI(T i) {
		this.i = i;
	}

	// 제너릭 타입을 반환하는 함수
	public T getI() {
		return i;
	}
}
```

제네릭 클래스의 사용

```java
Generic<Integer> i = new Generic<Integer>();
i.setI(new Integer(100));
Integer j = i.getI();
```

제너릭 타입을 특정 자료형으로 제한할 수 있다
```java
public class Generic<T extends Integer>
```

### 12-2 컬렉션 프레임워크

자바에서 제공하는 자료구조 라이브러리

`Collection` 인터페이스와 `Map` 인터페이스을 기반으로 구성되어 있음

- `Collection` 인터페이스
	- `List` 인터페이스
	- `Set` 인터페이스
- `Map` 인터페이스
	- `key`와 `value`를 가짐

### 12-3 List 인터페이스
- ArrayList 클래스 : 객체 배열을 구현한 클래스, 컬렉션 인터페이스와 List 인터페이스를 구현
- LinkedList 클래스 : 링크드 리스트를 클래스를 구현한 클래스

### 12-4 Set 인터페이스
- HashSet 클래스 : 집합 자료 구조를 구현하고 중복을 허용하지 않음
- TreeSet 클래스 : 자료의 중복을 허용하지 않으면서 출력 결과 값을 정렬하는 클래스

### 12-5 Map 인터페이스
- HashMap 클래스 : Hash 형태로 자료를 관리하는 Map 인터페이스를 구현한 클래스
- TreeMap 클래스 : 이진 검색 트리로 구성된 key 값으로 자료를 정렬한 클래스