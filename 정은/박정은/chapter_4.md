Object = 최상위 클래스

class Student extends Object {
    int studentID;
    String studentName;
}

*편집창에 Object라고 쓰고 F1 키를 누르면 JavaDos 내용 -> Object 클래스에 정의된 메서드 확인 가능
*final 예약어로 선언한 메서드는 재정의 불가능

Object 클래서의 기본 제공 
-> toString() 메서드
✅ 언제 사용하나요?
-디버깅: 객체 상태를 확인할 때
-로깅: 로그로 객체 정보 출력
-UI 출력: 사용자에게 정보를 보여줄 때 
ex. System.out.println(car.toString());

(재정의)
@Override
public String toString() {
    return bookTitle + "," + bookNumber;
}

✅equals() 메서드 -> 재정의 하여 논리적으로 같은 인스턴스인지 확인할 수 있음
hash -> 정보를 저장하거나 검색할 때 사용하는 자료 구조
ex. index = hash(key)
+객체의 논리적 동등성(equals())이 같다면, 동일한 hashCode를 반환해야 함
-> hashCode()가 같다고 해서 equals()가 반드시 true는 아님

clone() 메서드 = 객체 원본을 유지하며 복사본 사용


final -> 문자 변경 X
concat() -> 두 문자열을 연결하는 메서드

StringBuffer & StringBuilder 클래스
= char[] 배열이 확장되어 추가 메모리 사용 X


Wrapper 클래스
-> parseInt() 메서드 = 문자열에서 int 값을 바로 가져와서 변환O

(기본형과 객체형의 차이)
-기본형 = 변수에 직접 값 저장, 메모리 공간 적고 빠름, 메서드X, null X
-객체형 = 주소를 저장장, 더 많은 메모리와 시간 소요, 메서드O, null O

*"메서드(method)"는 객체나 클래스가 가지고 있는 기능(동작)을 정의한 함수
*null은 변수에 어떤 객체나 값도 연결되어 있지 않음을 나타낼 때 사용


자바의 모든 클래스와 인터페이스는 컴파일 되고 나면 class 파일로 생성된다.
*Class 클래스는 컴파일 된 class 파일에 저장된 클래스나 인터페이스 정보를 가져오는데 사용

(어떤 클래스인지 아는 방법)
1. Object 클래스의 getClass() 메서드 사용하기
2. 클래스 파일 이름을 Class 변수에 직접 대입하기
3. Class.forName("클래스 이름") 메서드 사용하기

인스터스 = 객체는 개념, 인스턴스는 실체화된 객체를 지칭
*하나의 클래스에서 여러 인스턴스를 만들 수 있음
Car car1 = new Car();
Car car2 = new Car();

✅ 리플렉션 프로그래밍이란?
실행 중(Run-time)에 클래스의 정보(이름, 메서드, 필드 등)를 동적으로 읽고, 수정하거나 호출하는 기술

✅ 왜 필요한가?
보통은 프로그램이 컴파일될 때 모든 정보가 고정되지만, 리플렉션을 사용하면 실행 중에 동적으로 객체를 다룰 수 있어서 아래와 같은 일을 할 수 있어요.

📌 예시 상황:
-클래스 이름이 문자열로만 주어졌을 때 해당 클래스의 객체 만들기
-어떤 객체가 어떤 메서드를 가지고 있는지 조사
-private 필드/메서드에 접근해서 값 읽기/수정
-프레임워크에서 DI(의존성 주입), 애노테이션 처리 등
ex.
import java.lang.reflect.Method;

public class Example {
    public void hello() {
        System.out.println("Hello!");
    }
}

public class Main {
    public static void main(String[] args) throws Exception {
        // 클래스 이름으로 클래스 정보 얻기
        Class<?> clazz = Class.forName("Example");

        // 인스턴스 생성
        Object obj = clazz.getDeclaredConstructor().newInstance();

        // "hello" 메서드 정보 가져오기
        Method method = clazz.getMethod("hello");

        // 메서드 실행
        method.invoke(obj);  // → "Hello!" 출력
    }
}

forName() 메서드는 컴파일할 때 오류를 알 수 없을 때가 있다.
-> 시스템 연동 중 매개변수로 넘어온 값, 동적 로딩을 통해 Class 가져오면 됨!


제네릭 프로그래밍 = 여러 참조 자료형을 사용 가능하도록 프로그래밍한다 

✅ 1. list란?
여러 개의 값을 순서대로 저장하는 자료구조예요.
값들을 묶어서 한 번에 다루고 싶을 때 사용해요.

✅ 2. 지역 변수 (Local Variable)
특정 블록({}) 안에서 선언되고, 그 블록을 벗어나면 사라지는 변수

✅ 다이아몬드 연산자란?
List<String> list = new ArrayList<>();
여기서 <> 이 부분이 다이아몬드 연산자예요.
Java 컴파일러가 ArrayList의 타입을 앞에 있는 List<String>을 보고 자동으로 추론해줘요.

✅ 왜 필요할까?
🔴 예전 방식
List<String> list = new ArrayList<String>();
매번 타입을 반복해서 써야 했어요. (길고 불편)

**제너릭(Generic)**은 Java에서 타입을 일반화해서 코드의 재사용성과 안정성을 높여주는 기능이에요.
✅ 제너릭 클래스 (Generic Class)
클래스 전체에 타입 파라미터를 적용해서 다양한 타입에 대응할 수 있게 만든 클래스
✅ 제너릭 메서드 (Generic Method)
메서드 자체에 타입 파라미터를 붙여서 다양한 타입의 인자를 처리할 수 있는 메서드


컬렉션 프레임워크 = 데이터(객체들)를 효율적으로 저장, 검색, 수정, 삭제하기 위한 자료구조 모음
-Collection 인터페이스
.List 인터페이스 = 순차적
.Set(=집합) 인터페이스 = 순서와 상관없이 중복 허용X
-Map 인터페이스 = 하나가 아닌 쌍(하나이상)으로 되어있는 key-value 쌍(중복X) 

✅ 자바 클래스 전체 구조
public class Person extends Human implements Runnable {

    // 🔹 필드 (속성)
    String name;
    int age;

    // 🔹 생성자
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    // 🔹 메서드 (동작)
    public void introduce() {
        System.out.println("안녕하세요, " + name + "입니다. 나이: " + age);
    }

    // 🔹 인터페이스 구현 메서드
    public void run() {
        System.out.println(name + "이(가) 달립니다!");
    }

    // 🔹 내부 클래스
    class Heart {
        void beat() {
            System.out.println("두근두근");
        }
    }
}

✅ 정리: 언제 어떤 내부 클래스를 쓸까?
-외부 클래스 인스턴스와 강하게 연결	= 인스턴스 내부 클래스
-외부 클래스 없이 독립적으로 사용 = 정적(static) 내부 클래스
-메서드 내에서만 잠깐 사용 = 지역 내부 클래스
-딱 한 번 쓸 객체가 필요할 때 = 익명 내부 클래스

ArrayList & Vector 클래스
-동기화 지원 여부 차이
-배열을 구현한 클래스

*스레드 =  프로세스(process) 안에서 실제로 작업을 수행하는 단위
-단일 스레드
-멀티스레드

링크드 리스트는 자료를 중간에 추가하거나 삭제할 때 자료의 이동이 배열보다 적다

Cpllection 요소를 순회(=하나씩 꺼내기)하는 Iterator
✅ 언제 Iterator를 직접 써야 할까?
-컬렉션을 순회하면서 요소를 제거해야 할 때 (→ remove() 메서드)
-다양한 컬렉션(List, Set 등)을 동일한 방식으로 순회할 때
-for-each로 처리하기 어려운 복잡한 조건이 있을 때

자바의 Collection 인터페이스나 MAp 인터페이스를 구현한 클래스 중
Tree로 시작하는 클래스는 데이터를 추가한 후 결과를 출력하면 결과 값이 정렬된다.

(TreeSet)
-Set 인터페이스의 구현체
-중복 ❌, 자동 정렬 ⭕️ (기본: 오름차순)
-내부적으로 TreeMap을 사용함
= 정렬된 구조로 데이터를 저장하고 관리하는 자료구조들
+ 자바 컬렉션 프레임워크에서는 특히 이진 탐색 트리 기반으로 정렬과 검색에 최적화된 기능을 제공

(Comparable 인터페이스와 Comparator 인터페이스)
| 항목      | Comparable               | Comparator                              |
| -----     | ------------------------ | ------------------------------------    |
| 위치      | 클래스 내부               | 클래스 외부                             |
| 메서드    | `compareTo()`             | `compare()`                            |
| 정렬 기준 | 하나만 가능                | 여러 개 가능                           |
| 사용법    | `Collections.sort(list)`  | `Collections.sort(list, comparator)`   |
| 유연성    | 낮음                      | 높음                                   |

✅ 언제 써야 할까?
-Comparable: 기본 정렬 기준이 명확하고 고정적일 때
→ 예: 학생을 항상 나이순으로 정렬하고 싶다면 Student implements Comparable<Student>
-Comparator: 동적으로 기준을 바꿔야 할 때
→ 예: 이름순, 나이순, 점수순 등 상황에 따라 바꾸고 싶을 때


내부 클래스란 = 클래스 안에 정의된 또 다른 클래스
*외부 클래스와 긴밀한 관계가 있는 클래스의 논리적 묶음

(4가지 종류)
-인스턴스 내부 클래스
-정적(static) 내부 클래스
-지역 클래스 (메서드 내부에 정의)
-익명 클래스 (이름 없는 일회용 클래스)

인스턴스 내부 클래스 = 외부 클래스의 인스턴스가 있어야 생성 가능한 클래스
*외부 클래스의 필드와 메서드에 자유롭게 접근 가능

static 키워드를 가질 수 없음 (정적 멤버 선언 불가)

public class Outer {
    private String outerField = "외부 클래스 필드";

    // 인스턴스 내부 클래스
    public class Inner {
        public void show() {
            System.out.println("내부 클래스 메서드");
            System.out.println("외부 필드 접근: " + outerField);
        }
    }
}


인스턴스 내부 클래스에서 사용 가능한 것들
-private 포함 모든 멤버에 접근 가능
-외부 클래스의 this 참조는 Outer.this

public class Outer {
    private int number = 10;

    public class Inner {
        public void print() {
            System.out.println("외부 클래스 변수: " + number);     // 가능
            System.out.println("외부 클래스 참조: " + Outer.this); // 가능
        }
    }
}

(다른 클래스에서 인스턴스 내부 클래스 생성)
Outer outer = new Outer(); // 외부 클래스 인스턴스 생성
Outer.Inner inner = outer.new Inner(); // 내부 클래스 인스턴스 생성
inner.show(); // 내부 클래스 메서드 호출

정적 내부 클래스 (static class)
정적(static) 내부 클래스는 외부 클래스의 인스턴스를 만들지 않고 사용할 수 있다
외부 클래스의 정적(static) 멤버만 접근할 수 있고, 보통 외부 클래스의 보조 기능을 담당할 때 사용

public class Outer {
    static int staticVal = 100;

    static class StaticInner {
        void display() {
            System.out.println("정적 내부 클래스: " + staticVal);
        }
    }
}

// 다른 클래스에서 사용
Outer.StaticInner inner = new Outer.StaticInner();
inner.display();


지역 내부 클래스 = 메서드 안에서 정의되는 클래스
-그 메서드 안에서만 사용 가능
-메서드의 지역 변수는 final 또는 effectively final(값을 바꾸지 않음)이어야 접근 가능능

public class Outer {
    void myMethod() {
        int localVar = 10;  // 값이 바뀌지 않아서 effectively final

        class LocalInner {
            void print() {
                System.out.println("지역 내부 클래스: " + localVar);
            }
        }

        LocalInner inner = new LocalInner();
        inner.print();
    }
}

+익명 내부 클래스
이름이 없는 일회성 클래스
인터페이스나 추상 클래스를 구현할 때 많이 사용
객체 생성과 동시에 오버라이딩 가능, 주로 콜백, 이벤트 처리 등에 사용된다

public class Example {
    public static void main(String[] args) {
        Runnable task = new Runnable() {
            @Override
            public void run() {
                System.out.println("익명 내부 클래스 실행");
            }
        };

        task.run();
    }
}

익명 내부 클래스는 어디에 사용하는가?
익명 내부 클래스는 일회성으로 인터페이스나 추상 클래스를 구현하거나 상속할 때 사용
*주로 콜백 함수, 이벤트 리스너, 스레드 처리 등 간단한 동작을 바로 정의해서 실행하고 싶을 때

Thread t = new Thread(new Runnable() {
    @Override
    public void run() {
        System.out.println("익명 내부 클래스에서 실행");
    }
});
t.start();


람다식 = "함수 자체를 값처럼" 표현하는 방법
-익명 내부 클래스보다 더 간결하고 읽기 쉬운 표현 방식
-특히 함수형 인터페이스와 함께 사용하면 매우 직관적

Runnable r = () -> System.out.println("람다식 실행");
r.run();

(매개변수) -> { 실행문 }
매개변수가 하나이면 괄호 생략 가능, 실행문이 하나이면 중괄호도 생략 가능

함수형 인터페이스 (Functional Interface) = 추상 메서드가 딱 하나만 정의된 인터페이스


(람다식으로 이 인터페이스를 구현하면....!!)

MyFunction func = () -> System.out.println("함수형 인터페이스 람다식");
func.doSomething();

✅객체지향 프로그래밍 방식과 람다식 비교
항목	객체지향 방식	람다식 (함수형)
형태	클래스 생성 → 인터페이스 구현	함수 자체를 값처럼 전달
구조	코드가 길어짐	간결하고 읽기 쉬움
목적	객체 중심의 설계	동작(함수) 중심 설계
사용 사례	복잡한 로직, 다형성 활용	콜백, 일회성 동작, 스트림 처리


람다식= **익명 함수(이름 없는 함수)**를 간결하고 간단하게 표현현
함수형 인터페이스에 사용되며, 간단한 방식으로 메서드를 구현

(람다식 문법)
(매개변수) -> { 실행할 코드 }
람다식의 장점
-코드 간결화: 코드가 간결하고 명확해져 가독성이 증가
-콜백 처리 및 이벤트 처리: 자주 사용되는 콜백 함수나 이벤트 처리에서 유용하다
-고차 함수: 함수(메서드)를 값으로 전달할 수 있기 때문에 함수형 프로그래밍을 가능

함수형 인터페이스 (Functional Interface)
람다식은 반드시 함수형 인터페이스에서만 사용된다
함수형 인터페이스는 하나의 추상 메서드만 가지고 있는 인터페이스를 의미한다

@FunctionalInterface
interface MyInterface {
    void action(); // 추상 메서드
}

예제 - 람다식 구현
MyInterface myFunc = () -> System.out.println("람다식으로 함수 실행!");
myFunc.action();


⚠️예외 처리 (Exception Handling)
-try-catch 문
try-catch는 예외가 발생할 가능성이 있는 코드 영역을 try 블록 안에 두고, 
예외가 발생하면 catch 블록에서 처리한다

try {
    int result = 10 / 0; // 예외 발생
} catch (ArithmeticException e) {
    System.out.println("0으로 나눌 수 없습니다.");
}

-try-catch-finally 문
finally 블록은 예외가 발생하든 안 하든 무조건 실행한다
주로 자원 해제 코드나 마무리 작업을 수행

try {
    int result = 10 / 0;
} catch (ArithmeticException e) {
    System.out.println("예외 처리");
} finally {
    System.out.println("무조건 실행");
}

-try-with-resources 문
try-with-resources는 자동으로 자원을 해제해주는 구문
AutoCloseable을 구현한 객체에서만 사용할 수 있다
자원(파일, 소켓 등)을 열고 사용 후 자동으로 닫을 수 있다

try (BufferedReader br = new BufferedReader(new FileReader("file.txt"))) {
    String line = br.readLine();
} catch (IOException e) {
    e.printStackTrace();
}

-AutoCloseable 인터페이스
자원 자동 해제를 위한 인터페이스
ex. 객체가 close() 메서드를 자동으로 호출해 자원을 해제할 수 있다

class MyResource implements AutoCloseable {
    @Override
    public void close() throws Exception {
        System.out.println("자원 해제 완료");
    }
}

throws로 예외 처리 미루기
메서드에서 발생할 수 있는 예외를 호출하는 곳으로 전달(미룰) 수 있다 

public void readFile() throws IOException {
    FileReader fr = new FileReader("file.txt");
}


(다중 예외 처리)
하나의 catch 블록에서 여러 개의 예외를 처리할 수 있다 
파이프(|)로 구분하여 여러 예외를 처리

try {
    String s = null;
    System.out.println(s.length());
} catch (NullPointerException | ArithmeticException e) {
    e.printStackTrace();
}


(사용자 정의 예외 클래스)
사용자 정의 예외 클래스를 만들어 특정한 예외를 처리할 수 있다
Exception을 상속하여 필요한 예외를 정의한한다

class MyCustomException extends Exception {
    public MyCustomException(String msg) {
        super(msg);
    }
}

*자바 입출력 (I/O)
-바이트 스트림: 1 byte씩 읽고 씁니다.
-문자 스트림: 2 byte씩 읽고 씁니다.

(바이트 단위 스트림)
바이트 단위 스트림은 파일, 이미지, 비디오 등 이진 데이터를 처리할 때 사용된다
InputStream, OutputStream을 상속받은 클래스를 사용

FileInputStream fis = new FileInputStream("file.bin");
int data = fis.read();
fis.close();

(문자 단위 스트림)
문자 단위 스트림은 텍스트 파일 처리에 사용되며, Reader, Writer를 상속받은 클래스가 사용된다

FileReader fr = new FileReader("text.txt");
int data = fr.read();
fr.close();

보조 스트림 = 기능을 확장하는 스트림
ex. 버퍼링을 사용하여 성능을 향상, 데이터를 변환

BufferedReader br = new BufferedReader(new FileReader("text.txt"));
String line = br.readLine();

직렬화 = 객체를 바이트 스트림으로 변환하여 파일에 저장하거나 네트워크를 통해 전송 
+객체를 바이트 형태로 저장하고, 나중에 복원(역직렬화)할 수 있다

ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream("object.ser"));
oos.writeObject(new MyObject());
oos.close();

*그 외 입출력 클래스
-PrintWriter: 형식화된 출력에 사용됩니다.
-Scanner: 입력을 읽는 클래스
-RandomAccessFile: 파일을 랜덤 액세스할 수 있는 클래스

Scanner scanner = new Scanner(System.in);
String input = scanner.nextLine();
