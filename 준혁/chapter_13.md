## 15. 자바 입출력
### 15-1 자바 입출력과 스트림
- 입출력 장치의 호환성을 보장하기 위해 만들어진 스트림
- 입력, 출력, 바이트, 문자, 기반, 보조 스트림이 존재함

### 15-2 표준 입출력
- `System.out` : 표준 출력 스트림
- `System.in` : 표준 입력 스트림
- `System.err` : 표준 오류 스트림

그 외 클래스

- `Scanner` : `java.util` 에서 제공하는 입력 스트림 클래스
- `Console` :  입력 스트림 클래스

### 15-3 바이트 단위 스트림

- `InputStream` : 바이트 단위로 읽는 스트림 중 최상위
- `FileInputStream` : 파일 읽기
```java
public static void main(String[] args) {
	FileInputStream fis = null;
	try {
		fis = new FileInputStream("input.txt");
		System.out.println(fis.read());
	} catch(IOException e) {
		System.out.println(e);
	} finally {
		try {
			fis.close();
		} catch(IOException e) {
			System.out.println(e);
		} catch(NullPointerException e) {
			System.out.println(e);
		}
		System.out.println("end");
	}
}
```
- `OutputStream`
- `FileOutputStream`

### 15-4 문자 단위 스트림

- `Reader`
- `FileReader`
- `Writer`
- `FileWriter`

### 15-5 보조 스트림

- `FilterInputStream`, `FilterOutputStream` : 보조 스트림의 상위 클래스
- `BufferdStream` : 버퍼 기능을 추가해 더 빠른 입출력을 제공
- `Data[Input, Output]Stream` : 메모리에 저장된 0, 1 상태를 그대로 읽고 씀.

### 15-6 직렬화

> 인스턴스의 순간 상태를 그대로 저장하거나 네트워크를 통해 전송하는 것.

- 역직렬화 : 저장된 내용이나 전송받은 내용을 다시 복원하는 것

생성자

- `ObjectInputStream`
- `ObjectOutputStream`

### 15-7 그 외 입출력 클래스

- `File` 클래스
- `RandomAccessFile` 클래스
