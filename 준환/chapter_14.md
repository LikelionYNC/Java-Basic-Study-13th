
# 14 예외 처리
## 🌅 공부기록
1. 예외 클래스
2. 예외 처리하기
3. 예외 처리 미루기
4. 사용자 정의 예외
## 🧠 배운 점
###오류란?
- 프로그램 오류는 2가지가 있다.
  - 컴파일 오류
  - 실행 오류

- 실행 오류
   - 시스템 오류
      - 사용 가능한 동적 메모리가 없는 경우, 스택 메모리의 오버플로가 발생한 경우
   - 예외
      - 파일을 읽어 사용하려는데 파일이 없는경우, 네트워크로 데이터를 전송하려는데 연결이 안된 경우
- 오류클래스
  - 모두 Throwable 클래스에서 상속을 받습니다. Error 클래스의 하위 클래스는 시스템에서 발생하는 오류를 다루며 프로그램에서 제어하지 않는다.
  - 프로그램 에서 제어하는 부분은 Exception 클래스와 그 하위에 있는 예외 클래스 이다.
 
  - try-catch문
  ```
  try{
    예외가 발생할 수 있는 코드 부분
  }catch(처리할 예외 타입 e) {
    try 블록 안에서 예외가 발생했을 때 예외를 처리하는 부분
  }
  ```
  ![image](https://github.com/user-attachments/assets/2f98e6a7-508a-4d90-8258-1708a2773260)
  ![image](https://github.com/user-attachments/assets/53fd3c1c-bbb1-488c-880c-2fcf50d7ff5f)

  ![image](https://github.com/user-attachments/assets/b81d5c39-2dfb-4edd-b67c-888ec678c774)
  ![image](https://github.com/user-attachments/assets/6efe9b21-c45a-479b-9640-831352d4adcf)

  - try-catch-finally
  ```
    try{
    예외가 발생할 수 있는 코드 부분
  }catch(처리할 예외 타입 e) {
    예외를 처리하는 부분
  } finally {
    항상 수행되는 부분
  }
  ```
  - finally 블록 사용하기
  ![image](https://github.com/user-attachments/assets/32e116c1-08bc-42fd-863d-fd643e2ad366)
  ![image](https://github.com/user-attachments/assets/bbb09efe-691e-4a25-8024-aa6b5b313e4c)

  - try-with-resources

  - AutoCloseable 인터페이스 구현
  ![image](https://github.com/user-attachments/assets/c80db23d-b1a0-43b3-b5c3-f7087c58305e)


  - try-with-resources 사용하기
  ![image](https://github.com/user-attachments/assets/d1a1b11e-f3ad-4fdf-9b05-31a463152202)
  ![image](https://github.com/user-attachments/assets/d6262fe9-fb3f-4490-868c-2a141d6a702c)


  - throws로 예외 미루기
  ![image](https://github.com/user-attachments/assets/29d851f8-699f-4e0c-8ea7-3e29ab338cc1)


  - 사용자 정의 예외 클래스 구현하기
  ![image](https://github.com/user-attachments/assets/d18c1639-7539-40f6-bb9b-832065e59c47)
    ```
      package chapter14.exception;
    
    public class IDFormatTest {
        private String userID;
    
        public String getUserID() {
            return userID;
        }
    
        public void setUserID(String userID) throws IDFormatException {
            if (userID == null) {
                throw new IDFormatException("아이디는 null일 수 없습니다");
            } else if (userID.length() < 8 || userID.length() > 20) {
                throw new IDFormatException("아이디는 8자 이상 20자 이하로 쓰세요");
            }
            this.userID = userID;
        }
    
        public static void main(String[] args) {
            IDFormatTest test = new IDFormatTest();
    
            String userID = null;
            try {
                test.setUserID(userID);
            } catch (IDFormatException e) {
                System.out.println(e.getMessage());
            }
    
            userID = "1234567";
            try {
                test.setUserID(userID);
            } catch (IDFormatException e) {
                System.out.println(e.getMessage());
            }
        }
    }
    ```
    ![image](https://github.com/user-attachments/assets/44c61179-dbd1-41d7-bba2-3fa94e13adf6)


