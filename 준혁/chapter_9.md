## 11. 기본 클래스
### 11-1 Object 클래스
> 모든 클래스의 최상위 클래스

컴파일 과정에서 모든 클래스는 Object 클래스를 상속한다.

Object 클래스는 자바에서 사용되는 클래스의 여러 기본적인 메서드를 제공. 그러나 모든 메서드를 재정의 할 수 있지는 않다.

#### Object 클래스의 기본 메서드
- toString() : 인스턴스의 정보를 문자열로 반환, 재정의가 가능하다.
- equals() : 인스턴스의 물리적인 주소가 `boolean`으로 반환하는 메서드, 재정의가 가능하다.
  재정의시 매개변수로 받은 obj 클래스를 같은 클래스로 형변환해서 사용한다.
- hashCode() : 인스턴스의 주소값을 반환하는 메서드, 재정의가 가능하다.
- clone() : 인스턴스를 복제하는 메서드.

## 11-2 String 클래스

선언방법

```java
String str = new String("문자열");
```

String 클래스의 value 는 불변하다. final을 사용하여 선언되었다.

변경이 가능한 String 클래스를 선언하기 위해선 `StringBuffer` 클래스나 `StringBuilder` 클래스를 이용하자.

`StringBuilder` 클래스는 문자열이 안전하게 변경되는 것을 보장하지 않지만 실행 속도가 빠르기 때문에 싱글 스레드 프로그램에서 유용하다.

## 11-3 Wrapper 클래스

기본 자료형을 위한 클래스

int, boolean 같은 기본 자료형이 아닌 `Integer`, `Boolean` 같은 클래스형으로 선언한다.

```java
Integer i = new Integer(100);
```

- 언박싱 : Wrapper 클래스를 기본 자료형으로 형변환
- 오토박싱 : 기본 자료형을 Wrapper 클래스로 형변환

## 11-4 Class 클래스

클래스나 인터페이스에 대한 변수, 메서드, 생성자 등의 정보를 가짐

```java
String str = new String();
Class cls = s.getClass();
Class c = String.Class;
```