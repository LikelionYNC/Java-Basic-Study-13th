

## 🌅 공부기록
1. 상속이란
2. 상속에서 클래스 생성과 형 변환
3. 메서드 오버라이딩
4. 다형성
5. 다형성 활용
6. 다운 캐스팅과 instanceof
### 🧠 배운 점
- 상속이란
- B클래스가 A클래스를 상속 받았을때 B클래스는 A클래스의 변수나 메서드를 사용이 가능하다.
- Customer 클래스 구현하기
- ![image](https://github.com/user-attachments/assets/7c266bc1-c9d9-42dd-9be4-d3f43d4b90c2)
- vip 클래스 구현하기
- ![image](https://github.com/user-attachments/assets/b54b24a0-e7c6-4d6a-8f39-15d0b3099968)
customer 코드에서 뭔가 잘못해서 그 부분만 나중에 다시 추가하겠습니다.
- 다형성이란
- 하나의 코드가 여러 자료형으로 구분되어 실행되는 것을 말한다.
- 다향성 테스트 하기
```
package chapter08.polymorphism;

class Animal {
    public void move() {
        System.out.println("동물이 움직입니다");
    }
}

class Human extends Animal {
    public void move() {
        System.out.println("사람이 두 발로 걷습니다");
    }
}

class Tiger extends Animal {
    public void move() {
        System.out.println("호랑이가 네 발로 뜁니다.");
    }
}

class Eagle extends Animal {
    public void move() {
        System.out.println("독수리가 하늘을 납니다");
    }
}

public class AnimalTest1 {
    public static void main(String[] args) {
        AnimalTest1 aTest = new AnimalTest1(); // 자기 자신 객체 생성
        aTest.moveAnimal(new Human());
        aTest.moveAnimal(new Tiger());
        aTest.moveAnimal(new Eagle());
    }    

    public void moveAnimal(Animal animal) {
        animal.move();
    }
}

```
![image](https://github.com/user-attachments/assets/809f2846-37de-44ce-9898-dce2da34f779)
- instanceof로 원래 인스턴스형 확인 후 다운 캐스팅 하기
'''
package chapter08.polymorphism;
import java.util.ArrayList;

class Animal {
    public void move() {
        System.out.println("동물이 움직입니다.");
    }
}

class Human extends Animal {
    public void move() {
        System.out.println("사람이 두 발로 걷습니다.");
    }

    public void readBook() {
        System.out.println("사람이 책을 읽습니다.");
    }
}

class Tiger extends Animal {
    public void move() {
        System.out.println("호랑이가 네 발로 뜁니다.");
    }

    public void hunting() {
        System.out.println("호랑이가 사냥을 합니다.");
    }
}

class Eagle extends Animal {
    public void move() {
        System.out.println("독수리가 하늘을 납니다.");
    }

    public void flying() {
        System.out.println("독수리가 날개를 쭉 펴고 멀리 날아갑니다.");
    }
}
public class AnimalTest {
    ArrayList<Animal> aniList = new ArrayList<Animal>(); // Animal 타입의 ArrayList 선언

    public static void main(String[] args) {
        AnimalTest aTest = new AnimalTest();
        System.out.println("원래 융으로 다룰 캐스팅");
        aTest.addAnimal();
        aTest.testCasting();
    }

    public void addAnimal() {
        aniList.add(new Human()); // Human 객체 추가
        aniList.add(new Tiger()); // Tiger 객체 추가
        aniList.add(new Eagle()); // Eagle 객체 추가

        for (Animal ani : aniList) {
            ani.move(); // 각 동물의 move 메서드 호출
        }
    }

    public void testCasting() {
        for (int i = 0; i < aniList.size(); i++) { // 모든 요소를 하나씩 돌면서
            Animal ani = aniList.get(i); // Animal 타입으로 가져옴
            if (ani instanceof Human) {
                Human h = (Human) ani; // Human이면 캐스팅
                h.readBook(); // Human의 readBook 메서드 호출
            } else if (ani instanceof Tiger) {
                Tiger t = (Tiger) ani; // Tiger이면 캐스팅
                t.hunting(); // Tiger의 hunting 메서드 호출
            } else if (ani instanceof Eagle) {
                Eagle e = (Eagle) ani; // Eagle이면 캐스팅
                e.flying(); // Eagle의 flying 메서드 호출
            } else {
                System.out.println("지원되지 않는 형입니다."); // 지원되지 않는 형일 경우
            }
        }
    }
}

'''
- ![image](https://github.com/user-attachments/assets/889a55fc-6336-48d1-a8a8-be06c785e2b3)
- 
