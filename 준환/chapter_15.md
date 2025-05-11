
# 14 자바 입출력
## 🌅 공부기록
1. 자바 입출력과 스트림
2. 표준 입출력
3. 바이트 단위 스트림
4. 문자 단위 스트림
5. 보조 스트림
6. 직렬화
7. 그 외 입출력 클래스
## 🧠 배운 점
### 스트림이란?
- 입출력 장치와 무관하고 일관성 있게 프로그램을 구현할 수 있도록 일종의 가상 통로인 스트림을 제공하는 것
- 자료를 읽어 들이려는 소스 와 자료를 쓰려는 대상에 따라 각각 다른 스트림 클래스를 제공합니다.

- 입력 스트림과 출력 스트림
  - 입력 자료의 이동이 출력 자료의 이동과 한 스트림에서 동시에 일어날 수 없기 때문에(단방향)
  - 어떤 스트림이 있다고 하면 그 스트림은 입력 스트림이거나 출력 스트림 입니다


- 바이트 단위 스트림과 문자 스트림
  - 자바의 스트림은 바이트 단위로 입출력이 이루어진다.
  - 라지만 문자를 나타내는 char형 2바이트이기 때문에 1바이트만 읽으면 한글 같은 문자는 깨진다
  - 입출력 중 가장 많이 사용하는 자료인 문자를 위해 문자 스트림을 별도로 제공

- 기반 스트림과 보조 스트림
  - 기반 스트림
    - 읽어 들일 곳이나 써야 할 곳에서 직접 읽고 쓸 수 있으며 입출력 대상에 직접 연결되어 생성되는 스트림
  - 보조 스트림
    - 직접 읽고 쓰는 기능은 없음 따라서 항상 다른 스트림을 포함하여 생성 된다.


- 표준 입출력

- 문자 하나를 입력받기
![image](https://github.com/user-attachments/assets/a1decf3c-ca06-43b1-a5d3-24fa9737ad54)
![image](https://github.com/user-attachments/assets/f18eba71-3309-4271-8677-d36be935733e)

- 문자 여러 개를 입력받기
![image](https://github.com/user-attachments/assets/4d4d153c-1c17-4bca-ab2c-19e133b7f563)
![image](https://github.com/user-attachments/assets/f673f57b-f9ed-49ae-a6eb-0fcffe19209b)

- Scanner 테스트 하기
![image](https://github.com/user-attachments/assets/cf0d1b07-166f-47f0-b3e2-e86f57161489)
![image](https://github.com/user-attachments/assets/22fc1630-e024-4bb2-8982-5fce083e7966)

- Console 테스트 하기
![image](https://github.com/user-attachments/assets/5c1f5718-0e98-4569-b0dc-ebc777f3c488)
![image](https://github.com/user-attachments/assets/57fc307f-6b3a-4231-a54d-debe408eb78b)

- FileInputStream 사용하기
![image](https://github.com/user-attachments/assets/f0c5fe00-a471-480c-b450-a48e4c584f5a)
![image](https://github.com/user-attachments/assets/73055784-c910-45c0-a1f6-d4aadbfb0731)

- 파일 끝까지 읽기
![image](https://github.com/user-attachments/assets/50a91e98-2483-46d8-9ed5-3fb4727cad69)
![image](https://github.com/user-attachments/assets/9faea9ec-119e-42db-8a8b-49c7d0d69b92)

- byte 배열로 읽기
![image](https://github.com/user-attachments/assets/5c907cfc-f2db-4454-b451-1ad9c8306ae8)
![image](https://github.com/user-attachments/assets/f4ef282f-32f6-46ca-8cda-8a92c26ba21e)

- 파일에 한 바이트씩 출력하기
![image](https://github.com/user-attachments/assets/746e0957-386f-4890-bad0-9269093111c6)
![image](https://github.com/user-attachments/assets/dac7c117-9458-452c-bc5a-e133b590e17b)
![image](https://github.com/user-attachments/assets/389de19e-4457-4a98-a82c-23d0780a72aa)

- 파일에 바이트 배열로 출력하기
![image](https://github.com/user-attachments/assets/0ef5be67-cc1f-4263-8081-be5766df9178)
![image](https://github.com/user-attachments/assets/02fbe494-4d47-48b1-9af8-269170a4fb54)
![image](https://github.com/user-attachments/assets/a652cef7-24ce-4e55-b7a8-2126296beb49)

- 파일에 바이트 배열로 출력하기
![image](https://github.com/user-attachments/assets/4c656b77-1020-4078-9e8d-b9c38ccabe46)
![image](https://github.com/user-attachments/assets/4c2b4501-3bd9-47f3-aa8b-80df9c606f66)
![image](https://github.com/user-attachments/assets/dfdf1eb8-9b1c-4e7c-87b6-d56ccc46008f)

- FileReader로 읽기
![image](https://github.com/user-attachments/assets/5fad2c66-48a9-4c9d-9182-1b96540eb512)
![image](https://github.com/user-attachments/assets/8ca83561-7626-403b-a079-5456e8a36e04)

- FileWriter로 쓰기
![image](https://github.com/user-attachments/assets/8039b272-06eb-42d0-8c1d-62d0843648df)
![image](https://github.com/user-attachments/assets/685e8364-aa5b-413c-8e51-b4efb81eb7db)
![image](https://github.com/user-attachments/assets/9214bb68-4a6e-4509-847e-645f2435bcd0)

- InputStreamReader 사용하기
![image](https://github.com/user-attachments/assets/b6f46926-065f-4274-ac16-b9ac6e683dfb)
![image](https://github.com/user-attachments/assets/4a4f588a-e707-45d0-959f-597aed8d8db1)

- 파일 복사하기
![image](https://github.com/user-attachments/assets/6fff3198-9731-4b0f-a11c-61c1e2d495d7)

- 버퍼링 기능으로 파일 복사하기
![image](https://github.com/user-attachments/assets/c1da8d50-b228-4f2e-a56e-98c5650d1ed3)

- DataInputStream / DataOutputStream 테스트 하기
```
package chapter15.stream.decorator;

import java.io.DataInputStream;
import java.io.DataOutputStream;
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.IOException;

public class DataStreamTest {
    public static void main(String[] args) {
        // 데이터를 파일에 쓰기
        try (FileOutputStream fos = new FileOutputStream("/home/alpaca/Java/src/chapter15/data.txt");
                DataOutputStream dos = new DataOutputStream(fos)) {
            // 각 자료형에 맞게 자료를 씀
            dos.writeByte(100);
            dos.writeChar('A');
            dos.writeInt(10);
            dos.writeFloat(3.14f);
            dos.writeUTF("Test");

        } catch (IOException e) {
            e.printStackTrace();
        }

        // 파일에서 데이터 읽기
        try (FileInputStream fis = new FileInputStream("/home/alpaca/Java/src/chapter15/data.txt");
                DataInputStream dis = new DataInputStream(fis)) {
            // 자료형에 맞게 자료를 읽어 출력함. 파일에 쓴 순서와 같은 순서 같은 메서드로 읽어야 함함
            System.out.println(dis.readByte());
            System.out.println(dis.readChar());
            System.out.println(dis.readInt());
            System.out.println(dis.readFloat());
            System.out.println(dis.readUTF());

        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}

```
![image](https://github.com/user-attachments/assets/456c15b9-9b2b-4cc5-8512-3b0f485d77b2)

