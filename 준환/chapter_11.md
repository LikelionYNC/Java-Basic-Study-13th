
# 11 기본클래스
## 🌅 공부기록
1. Object 클래스
2. String 클래스
3. Wrapper 클래스
4. Class 클래스
### 🧠 배운 점
object 클래스
- 모든 자바 클래스의 최상위 클래스
- 컴파일 과정에서 extends object가 자동으로 쓰여진다.
- Object 메서드
  | 메서드 | 설명 |
  | --- | --- |
  | String toString( ) | 객체를 문자열로 표현하여 반환, 재정의하여 객체에 대한 설명이나 특정 멤버 변수 값을 반환 |
  | boolean equals(Object obj) | 두 인스턴스가 동일한지 여부를 반환합니다. 재정의하여 논리적으로 동일한 인스턴스임을 정의할 수 있다. |
  | int hashCode( ) | 객체의 해시 코드 값을 반환 |
  | Object clone( ) | 객체를 복제하여 동일한 멤버 변수 값을 가진 새로운 인스턴스 생성 |
  | Class getClass( ) | 객체의 Class 클래스를 반환 |
  | void finalize( ) | 인스턴스가 힙 메모리에서 제거될 때 가비지 컬렉터에 의해 호출되는 메서드, 네트워크 해제, 열려 있는 파일 스트림 해체 등 구현 |
  | void wait( ) | 멀티스레드 프로그램에서 사용하는 메서드, 스레드를 기다리는 상태로 만듬 |
  | void notify( ) | wai( ) 메서드에 의해 기다리고 있는 스레드를 실행 가능한 상태로 가지고 온다 |

- Object 클래스의 toString( ) 메서드
  -  생성된 인스턴스의 클래스 이름과 주소값을 보여준다
![image](https://github.com/user-attachments/assets/040dc097-4bc1-4f8a-acff-e2181b0ced24)
![image](https://github.com/user-attachments/assets/0773d725-e313-458d-b249-6ad6d1d8e51d)
  - toString( ) 메서드 정의하기
![image](https://github.com/user-attachments/assets/87f9d888-0cb1-4e2b-a082-8066cda57aaf)
![image](https://github.com/user-attachments/assets/cf685a83-7d19-40ea-8c25-d293823afe94)

- equals( ) 메서드
  - 두 인스턴스가 있을 때 `==` 는 단순히 물리적으로 같은 메모리 주소인지 여부를 확인 할 수있고, 논리적으로 같은 인스턴스인지 확인하도록 구현할 수 있습니다.
```
package chapter11.object;

class Student {
    int studentId;
    String studentName;

    public Student(int studentid, String studentName) {
        this.studentId = studentid;
        this.studentName = studentName;
    }

    public String toString() {
        return studentId + "," + studentName;
    }
}

public class EqualsTest {
    public static void main(String[] args) {
        Student studentLee = new Student(100, "이상원");
        Student studentLee2 = studentLee; //주소 복사
        Student studentSang = new Student(100,  "이상원");

        if(studentLee == studentLee2) // == 기호로 비교
            System.out.println("studentLee와 studentLee2의 주소는 같습니다.");
        else
            System.out.println("studentLee와 studentLee2의 주소는 다릅니다.");
        
        if(studentLee.equals(studentLee2)) // equals() 메서드로 비교
            System.out.println("studentLee와 studentLee2의 주소는 동일합니다.");
        else
            System.out.println("studentLee와 studentLee2의 주소는 동일하지 않습니다.");

        if(studentLee == studentSang)// == 기호로 비교
            System.out.println("studentLee와 studentSang의 주소는 같습니다.");
        else
            System.out.println("studentLee와 studentSang의 주소는 다릅니다.");

        if(studentLee.equals(studentSang))// equals() 메소드로 비교교
            System.out.println("studentLee와 studentSang은 동일합니다.");
        else
            System.out.println("studentLee와 studentSang은 동일하지 않습니다.");
    }
}

```
![image](https://github.com/user-attachments/assets/66cb370b-edcd-4e86-8687-ea82a20357d6)

  - String과 Integer 클래스의 equals()메서드
![image](https://github.com/user-attachments/assets/2cb5603f-72e2-4c61-9ef0-0e0788ea1839)
![image](https://github.com/user-attachments/assets/dccf3834-1685-4e8d-bb07-65f0505db69f)

  - equals() 메서드 재정의하기
![image](https://github.com/user-attachments/assets/83eebda9-11dc-4592-a4d9-91a47788bc04)

- hashCode()메서드
  - 객체의 특정 정보를 매개변수 값으로 넣으면 그 객체가 저장되어야 할 위치나 저장된 해시 테이블 주소를 반환 합니다
  - 객체 정보를 알면 해당 객체의 위치를 빠르게 검색할 수 있다.
 
  - String과 Integer 클래스의 hashCode() 메서드
![image](https://github.com/user-attachments/assets/a459b6bc-edbe-4402-8fb5-e07aef889eec)
![image](https://github.com/user-attachments/assets/73df6209-d274-4ab2-a579-c915f2a93691)

  - hashCode() 메서드 재정의하기
![image](https://github.com/user-attachments/assets/a76d85bd-e692-4487-8831-4c66148b3f6b)
![image](https://github.com/user-attachments/assets/0d81cd9b-7d81-45ec-a73f-823a011ff786)


- clone() 메서드
  - 가본 틀의 복사본을 사용해 동일한 인스턴스를 만들어 복잡한 생성 과정을 간단히 하려는 경우에 사용
 
  - clone 메서드로 인스턴스 복제하기
```
package chapter11.object;
//원점을 의미하는 Point 클래스
class Point {
    int x;
    int y;

    Point(int x, int y) {
        this.x = x;
        this.y = y;
    }

    public String toString() {
        return "x = " + x + ", " + "y = " + y;
    }
}
// 객체를 복제해도 된다는 의미로 Cloneable 인터페이스를 함께 선언
class Circle implements Cloneable {
    Point point;
    int radius;

    Circle(int x, int y, int radius) {
        this.radius = radius;
        point = new Point(x, y);
    }

    public String toString() {
        return "원점 = " + point + ", " + "반지름은 " + radius + "입니다.";
    }
//clone() 메서드를 사용할 때 발생할 수 있는 오류를 예외 처리함함
    @Override
    public Object clone() throws CloneNotSupportedException {
        return super.clone();
    }
}

public class ObjectCloneTest {
    public static void main(String[] args) throws CloneNotSupportedException {
        Circle circle = new Circle(10, 20, 30);
        Circle copyCircle = (Circle)circle.clone(); // clone() 메서드를 사용해 circle 인스턴스를 copyCircle에 복제함함

        System.out.println(circle);
        System.out.println(copyCircle);
        System.out.println(System.identityHashCode(circle));
        System.out.println(System.identityHashCode(copyCircle));
    }
}

```
![image](https://github.com/user-attachments/assets/664f0bdb-3e77-40ca-b2b3-d0b9a31836cf)

- String 클래스
  - 생성자의 매개변수로 하여 생성하는 방식
  - 생성된 문자열 상수를 가리키는 방식

- 주소 값 비교하기

![image](https://github.com/user-attachments/assets/16cda20a-35b3-4ebf-8f49-27f2582ccdca)
![image](https://github.com/user-attachments/assets/0890f9bb-a6e0-4614-9ace-1250abe46910)

- 두 문자열 연결하기
- 두 문자열이 연결될때 변경이 되는게 아니라 두 문자열이 연결된 새로운 문자열이 생성

![image](https://github.com/user-attachments/assets/940922e7-5b37-4492-a87f-1a73016997f9)
![image](https://github.com/user-attachments/assets/e583a462-62e1-4941-a7b5-1ace0bdbd0e1)

- StringBuilder 클래스
- 내부 변경 가능한 Char[]를 변수로 가지고 있다.
- 기존 사용하던 char[] 배열이 확장되므로 추가 메모리를 사용하지 않는다.

![image](https://github.com/user-attachments/assets/505b5214-307e-4094-8446-787588deefe2)
![image](https://github.com/user-attachments/assets/96d849e5-f642-4bed-8795-6974a087d695)

- Class 클래스란?
- 클래스의 정보를 사용할 경우에 클래스 정보를 찾을때 사용
  1. Object 클래스의 getClass() 메서드 사용하기
  2. 클래스 파일 이름을 Class 변수에 직접 대입하기
  3. Class.forName("클래스 이름") 메서드 사용하기

- 클래스 생성
```
package chapter11.classex;
public class Person {
    private String name;
    private int age;

    public Person() {}

    public Person(String name) {
        this.name = name;
    }

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}

```
- Person의 Class 클래스 가져오기

![image](https://github.com/user-attachments/assets/3e187a41-a6b6-46e8-be56-72278c19d504)
![image](https://github.com/user-attachments/assets/50c2ae1a-a0d6-49f3-8b07-15ec16a6ae5e)

- String 클래스 정보 가져오기

![image](https://github.com/user-attachments/assets/4c5d9d9e-94f6-4034-a78f-2220d81c88e9)

- Person 클래스의 인스턴스 생성하기

![image](https://github.com/user-attachments/assets/a3d33ec1-d116-46e3-8962-474f9dd446c5)
![image](https://github.com/user-attachments/assets/f5cd9294-c6e7-4d77-b1d5-320321190ca3)


