
# 12 컬렉션 프레임워크
## 🌅 공부기록
1. 제네릭
2. 컬렉션 프레임워크
3. List 인터페이스
4. Set 인터페이스
5. Map 인터페이스
## 🧠 배운 점
### 제네릭이란?
  - 어떤 값이 하나의 참조 자료형이 아닌 여러 참조 자료형을 사용할 수 있도록 프로그래밍하는 것을 제네릭 프로그래밍이라고 합니다.

- Powder,Plastic,GenericPrinter<T>클래서 정의하기

![image](https://github.com/user-attachments/assets/e92ca533-95c2-4fe8-9fb7-d4091a53c4c2)
![image](https://github.com/user-attachments/assets/a8b2a94a-11d8-4727-96c1-2b241e74d115)
![image](https://github.com/user-attachments/assets/301f9f39-4f08-4414-958d-732102e7639b)

- GenericPrinter<T> 클래스 사용하기
- 자료형을 명시하지 않은 경우
![image](https://github.com/user-attachments/assets/c8462d30-4f10-43bb-9d1a-1584a05809e2)
- 자료형을 명시한 경우
![image](https://github.com/user-attachments/assets/7ec00ffc-a374-46ef-bbdc-deaa542e0e0a)
![image](https://github.com/user-attachments/assets/a80bdc5e-7569-4201-8630-25f16dacddca)

- 제네릭 클래스에서 T 자료형에 사용할 자료형에 제한을 두는것이 가능
- 3D 출력에서 물을 출력할 수 없는거 처럼 사용할 클래스에 자료형 제한을 두는 방식으로 extends 예약어를 사용할 수 있다.
- 추상 클래스에서 상속을 받음

- Material 추상 클래스
![image](https://github.com/user-attachments/assets/336acc70-def8-407b-8628-809ff433c072)
- 그리고 다른 클래스에서 extend로 받아쓴다.

- 자료형 매개변수를 여러 개 사용하는 제네릭 메서드 예제
- 자료형 매개변수를 두 개 사용하는 클래스
![image](https://github.com/user-attachments/assets/351cce22-b933-4392-b418-646ae09039bb)

- 제네락 메서드 구현하기
![image](https://github.com/user-attachments/assets/8ceeb4bd-781d-4952-9efa-2561bab057bc)
![image](https://github.com/user-attachments/assets/745cf910-592a-42af-9324-8cc52ff66c15)

### 컬러 프레임 워크란?
- 자료를 어떤 구조로 관리할 것인가? -> 자료구조
- 자바에서 자료 구조를 미리 구현하여 java.util 패키지에서 제공한다. -> 컬렉션 프레임워크
- Collection 인터페이스
  - List를 구현한 클래스는 순차적인 자료를 관리하는 데 사용하는 클래스
  - Set 인터페이스는 중복을 허용하지 않는다.
    ![image](https://github.com/user-attachments/assets/fef0c348-039a-4a3f-a391-eddc658dcb70)

    | 메서드 | 설명 |
    | --- | --- |
    | boolean add(E e) | Collection에 객체를 추가한다 |
    | void clear() | Collection의 모든 객체를 제거 |
    | Iterator<E> Iterator | Collection를 순환할 반복자를 반환 |
    | boolean reamove(Object o) | Collection에 매개변수에 해당하는 인스턴스가 존재하면 제거 |  
    | int size | Collection에 있는 요소의 개수를 반환 |

- Map 인터페이스
  - 하나가 아닌 쌍으로 되어 있는 자료를 관리하는 메서드들이 선언되어 있다.
  - key-value 쌍이라고 표현하는데 이때 키 값은 중복될 수 없다.

    | 메서드 | 설명 |
    | --- | --- |
    | put(K key, V value) | key에 해당하는 value 값을 map에 넣습니다. |
    | get(K key) | key에 해당하는 value 값을 반환합니다. |
    | boolean isEmpty() | Map이 비었는지 여부를 반환합니다. |
    | boolean containsKey(Object key) | Map에 해당 key가 있는지 여부를 반환합니다. |
    | boolean containsValue(Object value) | Map에 해당 value가 있는지 여부를 반환합니다. |
    | Set keySet() | key 집합을 Set으로 반환합니다 (중복 안 되므로 Set). |
    | Collection values() | value를 Collection으로 반환합니다 (중복 무관). |
    | remove(K key) | key가 있는 경우 삭제합니다. |
    | boolean remove(Object key, Object value) | key가 있는 경우 key에 해당하는 value가 매개변수와 일치할 때 삭제합니다.

 - Member 클래스 구현하기
![image](https://github.com/user-attachments/assets/cc04eb07-7696-40fd-9959-5309bd123a38)

- ArrayList 활용하기
```
package chapter12.collection.arraylist;

import java.util.ArrayList;
import chapter12.collection.Member;

public class MemberArrayList {
    private ArrayList<Member> arrayList; //ArrayList 선언

    public MemberArrayList() {
        arrayList = new ArrayList<Member>(); // Member형으로 선언한 ArrayList 생성
    }
    //ArrayList에 회원을 추가하는 메서드드
    public void addMember (Member member) {
        arrayList.add(member);
    }
    //해당 아이디를 가진 회원을 ArrayList에서 찾아 제거함함
    public boolean removeMember(int memberId) {
        for(int i = 0; i < arrayList.size(); i++) {
            Member member = arrayList.get(i); // get() 메서드로 회원을 순차적으로 가져옴
            int tempId = member.getMemberId();
            if(tempId == memberId) { // 회원 아이디가 매개변수와 일치하면
                arrayList.remove(i); // 해당 회원을 삭제제
                return true;
            }
        }
        System.out.println(memberId + "가 존재하지 않습니다."); // 반복문이 끝날 때까지 해당 아이디를 찾지 못한 경우
        return false;
    }
    // 전체회원을 출력하는 메서드
    public void showAllMember() {
        for(Member member : arrayList) {
            System.out.println(member);
        }
        System.out.println();
    }
}

```
- MemberArrayListTest 클래스 구현하기
![image](https://github.com/user-attachments/assets/db4c6b62-1a38-4736-b850-791b49dd8d21)
![image](https://github.com/user-attachments/assets/54c06b8a-dec7-428b-9593-22886b90821f)

- LinkedList 클래스
  - 각 요소는 다음 요소를 가리키는 주소 값을 가진다.
  - 따라서 물리적인 메모리는 떨어져 있어도 논리적으로는 앞 뒤 순서가 존재
  - 중간에 자료를 넣고 제거하는데 시간이 적게 걸린다는 장점이 있다.
  - 크기를 동적으로 증가시킬 수 있다.
 
- LinkedList 테스트하기
![image](https://github.com/user-attachments/assets/529a63f5-c073-4656-91e2-3a2697eb428e)

- 스택 구현하기
```
package chapter12.collection.arraylist;

import java.util.ArrayList;

class MyStack {
    private ArrayList<String> arrayStack = new ArrayList<String>();
    //스택의 맨 뒤에 요소를 추가
    public void push(String data) {
        arrayStack.add(data);
    }
    //스택의 맨 뒤에서 요소 꺼냄
    public String pop() {
        int len = arrayStack.size();//ArrayList에 저장된 유효한 자료의 개수
        if(len == 0) {
            System.out.println("스택이 비었습니다.");
            return null;
        }
        return(arrayStack.remove(len-1));// 맨 뒤에 있는 자료 반환하고 배열에서 제거거
    }
}

public class StackTest {
    public static void main(String[] args) {
        MyStack stack = new MyStack();
        stack.push("A");
        stack.push("B");
        stack.push("C");

        System.out.println(stack.pop());
        System.out.println(stack.pop());
        System.out.println(stack.pop());
    }
}

```
![image](https://github.com/user-attachments/assets/4fe2f9a7-3693-4b9c-a41d-5b883ab13435)

- 큐 구현하기
```
package chapter12.collection.arraylist;

import java.util.ArrayList;

class MyQueue {
    private ArrayList<String> arrayQueue = new ArrayList<String>();
    // 큐의 맨 뒤에 추가
    public void enQueue(String data) {
        arrayQueue.add(data);
    }
    // 큐의 맨 앞에서 꺼냄냄
    public String deQueue() {
        int len = arrayQueue.size();
        if(len == 0) {
            System.out.println("큐가 비었습니다");
            return null;
        }
        return(arrayQueue.remove(0)); // 맨 앞의 자료 반환하고 배열에서 제거
    }
}
public class QueueTest {
    public static void main(String[] args) {
        MyQueue queue = new MyQueue();
        queue.enQueue("A");
        queue.enQueue("B");
        queue.enQueue("C");

        System.out.println(queue.deQueue());
        System.out.println(queue.deQueue());
        System.out.println(queue.deQueue());
    }   
}

```
![image](https://github.com/user-attachments/assets/2d6bfe38-3458-4582-a3a1-e81a03fd2178)

- HashSet 클래스
  - 집합 자료 구조를 구현하며 중복을 허용하지 않습니다.

- HashSet 테스트하기
![image](https://github.com/user-attachments/assets/9d586b52-9704-42e7-a3d0-4c688499bfe6)
![image](https://github.com/user-attachments/assets/f038bee1-6b17-423b-8f5e-b54845e3c9d4)

- HashSet 활용하기
```
package chapter12.collection.hashset;

import java.util.HashSet;
import java.util.Iterator;

import chapter12.collection.Member;
public class MemberHashSet {
    private HashSet<Member> hashSet;

    public MemberHashSet() {
        hashSet = new HashSet<Member>();
    }

    public void addMember(Member member) {
        hashSet.add(member);
    }

    public boolean removeMember(int memberId) {
        Iterator<Member> ir = hashSet.iterator();

        while(ir.hasNext()) {
            Member member = ir.next();
            int tempId = member.getMemberId();
            if(tempId == memberId) {
                hashSet.remove(member);
                return true;
            }
        }
        System.out.println(memberId + "가 존재하지 않습니다.");
        return false;
    }

    public void showAllMember() {
        for(Member member : hashSet) {
            System.out.println(member);
        }
        System.out.println();
    }
}

```
![image](https://github.com/user-attachments/assets/662000b7-99ad-464c-ace1-bce94a2f9c40)
![image](https://github.com/user-attachments/assets/c351a2cf-c7a8-4726-972b-4b1cbee4d4c5)

- TreeSet 클래스
  - 자료의 중복을 허용하지 않으면서 출력 결과 값을 정렬하는 클래스 입니다.
![image](https://github.com/user-attachments/assets/bb8d3bc8-af31-4de9-bec3-3de1f28a1563)
![image](https://github.com/user-attachments/assets/8f35b362-220b-4532-a6f6-34f52455e2d3)
```
package chapter12.collection.treeset;

import java.util.Iterator;
import java.util.TreeSet;

import chapter12.collection.Member;

public class MemberTreeSet {
    private TreeSet<Member> treeSet;

    public MemberTreeSet() {
        treeSet = new TreeSet<Member>();
    }
    //회원을 추가하는 메서드
    public void addMember(Member member) {
        treeSet.add(member);
    }
    // 회원을 삭제하는 메서드드
    public boolean removeMember(int memberId) {
        Iterator<Member> ir = treeSet.iterator();

        while(ir.hasNext()) {
            Member member = ir.next();
            int tempId = member.getMemberId();
            if(tempId == memberId) {
                treeSet.remove(member);
                return true;
            }
        }
        System.out.println(memberId + "가 존재하지 않습니다.");
        return false;
    }
    //전체 회원을 출력하는 메서드드
    public void showAllMember() {
        for(Member member : treeSet) {
            System.out.println(member);
        }
        System.out.println();
    }
}

```
![image](https://github.com/user-attachments/assets/dcbc96c0-9634-4c75-8e58-ecd95e165586)

- Comparable 인터페이스
  - 자기 자신과 전달받은 매개변수를 비교하는 인터페이스
![image](https://github.com/user-attachments/assets/0561ffd2-611e-44de-9613-7fb3f96c1d4c)

![image](https://github.com/user-attachments/assets/22e51f91-15ee-4eb3-a13b-780dba8d6433)

- HashMap 클래스
- HashMap 활용하기
```
package chapter12.collection.hashmap;

import java.util.HashMap;
import java.util.Iterator;

import chapter12.collection.Member;

public class MemberHashMap {
    private HashMap<Integer, Member> hashMap;

    public MemberHashMap() {
        hashMap = new HashMap<Integer, Member>();
    }
    //회원을 추가하는 메서드
    public void addMember(Member member) {
        hashMap.put(member.getMemberId(), member);//key-value 쌍으로 추가가
    }
    //회원을 삭제하는 메서드드
    public boolean removeMember(int memberId) {
        if(hashMap.containsKey(memberId)) { // 매개변수로 받은 키 값인 회원 아이디가 있다면
            hashMap.remove(memberId);// 해당 회원 삭제제
            return true;
        }
        System.out.println(memberId + "가 존재하지 않습니다.");
        return false;
    }
    //Iterator를 사용하여 전체 회원을 출력하는 메서드
    public void showAllMember() {
        Iterator<Integer> ir = hashMap.keySet().iterator();
        while (ir.hasNext()) {
            int key = ir.next();
            Member member = hashMap.get(key);
            System.out.println(member);
        }
        System.out.println();
    }
}

```
![image](https://github.com/user-attachments/assets/d5d56eaa-bbeb-4b45-a889-e0558c37bb64)
![image](https://github.com/user-attachments/assets/87bf6ee7-5fdc-4815-9f63-cd568a6b7800)

- TreeMap 클래스
  - key 값으로 자료를 정렬할려면 사용
```
package chapter12.collection.treemap;

import java.util.Iterator;
import java.util.TreeMap;

import chapter12.collection.Member;
public class MemberTreeMap {
    private TreeMap<Integer, Member> treeMap;

    public MemberTreeMap() {
        treeMap = new TreeMap<Integer,Member>();
    }

    public void addMember(Member member) {
        treeMap.put(member.getMemberId(), member);//key-value 쌍으로 추가가
    }
    
    public boolean removeMember(int memberId) {
        if(treeMap.containsKey(memberId)){
            treeMap.remove(memberId);//key 값에 맞는 자료 삭제제
            return true;
        }
        System.out.println(memberId + "가 존재하지 않습니다.");
        return false;

    }

    public void showAllMember() {
        Iterator<Integer> ir = treeMap.keySet().iterator();
        while (ir.hasNext()) {
            int key = ir.next();
            Member member = treeMap.get(key);
            System.out.println(member);
        }
        System.out.println();
    }
}


```
![image](https://github.com/user-attachments/assets/fae73b33-5105-4368-8348-c2b680f0a677)
![image](https://github.com/user-attachments/assets/afb0ca8c-67ac-46c0-8650-41a81a1a2dab)
