
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

### 학점 산출 프로그램 만들기

- 학생 클래스 구현
```
package project.school;

import java.util.ArrayList;


public class Student {
    private int studentId;
    private String studentName;
    private Subject majorSubject;

    private ArrayList<Score> scoreList = new ArrayList<Score>();

    public Student (int studentId, String studentName, Subject majSubject) {
        this.studentId = studentId;
        this.studentName = studentName;
        this.majorSubject = majSubject;
    }

    public void addSubjectScore(Score score) {
        scoreList.add(score);
    }

    public int getStudentId() {
        return studentId;
    }

    public void setStudentId(int studentId) {
        this.studentId = studentId;
    }

    public String getStudentName() {
        return studentName;
    }

    public void setStudentName(String studentName) {
        this.studentName = studentName;
    }

    public Subject getMajorSubject() {
        return majorSubject;
    } 

    public void setMajorSubject(Subject majorSubject) {
        this.majorSubject = majorSubject;
    }

    public ArrayList<Score> getScoreList() {
        return scoreList;
    }

    public void setScoreList(ArrayList<Score> scoreList) {
        this.scoreList = scoreList;
    }


}
```

- 과목 클래스 구현
```
package project.school;

import java.util.ArrayList;
import project.school.utils.Define;


public class Subject {
    private String subjectName;
    private int subjectId;
    private int gradeType;
    
    private ArrayList<Student> studentList = new ArrayList<Student>();

    public Subject(String subjectName, int subjectId) {
        this.subjectName = subjectName;
        this.subjectId = subjectId;
        this.gradeType = Define.AB_TYPE;
    }

    public String getSubjectName() {
        return subjectName;
    }

    public void getSubjectName(String subjectNaem, String subjectName) {
        this.subjectName = subjectName;
    }

    public int getSubjectId() {
        return subjectId;
    }

    public void setSubjectId(int subjectId) {
        this.subjectId = subjectId;
    }

    public ArrayList<Student> getStudentList() {
        return studentList;
    }

    public void setStudentList(ArrayList<Student> studentList) {
        this.studentList = studentList;
    }

    public int getGradeType() {
        return gradeType;
    }

    public void setGradeType(int gradeType) {
        this.gradeType = gradeType;
    }

    public void register(Student student) {
        studentList.add(student);
    }

}

```

- 점수 클래스 구현
```
package project.school;
public class Score {
    int studentId;
    Subject subject;
    int point;

    public Score(int studentId, Subject subject, int point) {
        this.studentId = studentId;
        this.subject = subject;
        this.point = point;
    }

    public int getStudenId() {
        return studentId;
    }

    public void setStudentId(int studentId) {
        this.studentId = studentId;
    }

    public Subject getSubject() {
        return subject;
    }

    public void setSubject(Subject subject) {
        this.subject = subject;
    }

    public int getPoint() {
        return point;
    }

    public void setPoint(int point) {
        this.point = point;
    }

    public String toString() {
        return "학번:" + studentId + "," + subject.getSubjectName() + ":" + point;
    }
}
```

- 상수 값 정의
![image](https://github.com/user-attachments/assets/f898f1f9-8f49-4d81-8a08-d35936f3ff41)

- 인터페이스 정의
![image](https://github.com/user-attachments/assets/22f29475-0f71-47ab-8139-f4c482151d0d)

- 일반 과목 학점 정책 클래스
![image](https://github.com/user-attachments/assets/c054f6a4-ce6f-4629-bbdc-b73d3dab283f)

- 필수 과목 학점 정책 클래스
![image](https://github.com/user-attachments/assets/12a01cab-3223-4efb-b3d4-9db8b4368c29)

- 리포트 클래스 구현
```
package project.school.report;

import java.util.ArrayList;

import project.grade.BasicEvaluation;
import project.grade.GradeEvaluation;
import project.grade.MajorEvaluation;
import project.grade.PassFailEvaluation;
import project.school.School;
import project.school.Score;
import project.school.Student;
import project.school.Subject;
import project.school.utils.Define;

public class GenerateGradeReport {

    School school = School.getInstance();

    public static final String TITLE = "수강생 학점 \t\t\n";
    public static final String HEADER = " 이름 | 학번 |필수과목 | 점수 \n";
    public static final String LINE = "-------------------------------------\n";

    private StringBuffer buffer = new StringBuffer();

    public String getReport() {
        ArrayList<Subject> subjectList = school.getSubjectList();

        for (Subject subject : subjectList) {
            makeHeader(subject);
            makeBody(subject);
            makeFooter();
        }

        return buffer.toString();
    }

    public void makeHeader(Subject subject) {
        buffer.append(GenerateGradeReport.LINE);
        buffer.append("\t" + subject.getSubjectName() + "\n");
        buffer.append(GenerateGradeReport.TITLE);
        buffer.append(GenerateGradeReport.HEADER);
        buffer.append(GenerateGradeReport.LINE);
    }

    public void makeBody(Subject subject) {
        ArrayList<Student> studentList = subject.getStudentList();

        for (int i = 0; i < studentList.size(); i++) {
            Student student = studentList.get(i);
            buffer.append(student.getStudentName());
            buffer.append(" | ");
            buffer.append(student.getStudentId());
            buffer.append(" | ");
            buffer.append(student.getMajorSubject().getSubjectName());
            buffer.append(" \t");

            getScoreGrade(student, subject.getSubjectId());
            buffer.append("\n");
            buffer.append(LINE);
        }
    }

    public void getScoreGrade(Student student, int subjectId) {
        ArrayList<Score> scoreList = student.getScoreList();
        int majorId = student.getMajorSubject().getSubjectId();

        GradeEvaluation[] gradeEvaluation = {
            new BasicEvaluation(), // 일반 과목
            new MajorEvaluation(),  // 필수 과목
            new PassFailEvaluation()
        };

        for (int i = 0; i < scoreList.size(); i++) {
            Score score = scoreList.get(i);

            if (score.getSubject().getSubjectId() == subjectId) {
                String grade;

                if (score.getSubject().getSubjectId() == majorId) {
                    grade = gradeEvaluation[Define.SAB_TYPE].getGrade(score.getPoint());
                } else {
                    grade = gradeEvaluation[Define.AB_TYPE].getGrade(score.getPoint());
                }

                buffer.append(score.getPoint());
                buffer.append(":");
                buffer.append(grade);
                buffer.append(" ");
            }
        }
    }

    public void makeFooter() {
        buffer.append("\n");
    }
}

```
- Pass/Fail 학점 클래스 구현
![image](https://github.com/user-attachments/assets/8d7b8a69-2792-44b9-a948-4500b44f25ff)

- 학교 클래스
![image](https://github.com/user-attachments/assets/71680f59-41f7-46b4-9799-ee262eb0c32e)

- 테스트 클래스
```
package project.test;

import project.school.School;
import project.school.Score;
import project.school.Student;
import project.school.Subject;
import project.school.report.GenerateGradeReport;
import project.school.utils.Define;

public class TestMain {

    School goodSchool = School.getInstance();
    Subject korean;
    Subject math;
    Subject dance;

    GenerateGradeReport gradeReport = new GenerateGradeReport();

    public static void main(String[] args) {
        TestMain test = new TestMain();

        test.createSubject();
        test.createStudent();

        String report = test.gradeReport.getReport(); // 성적 결과 생성
        System.out.println(report);
    }

    public void createSubject() {
        korean = new Subject("국어", Define.KOREAN);
        math = new Subject("수학", Define.MATH);
        dance = new Subject("방송댄스", Define.DANCE);

        dance.setGradeType(Define.PF_TYPE);

        goodSchool.addSubject(korean); // 테스트 과목 생성
        goodSchool.addSubject(math);
        goodSchool.addSubject(dance);
    }

    public void createStudent() {
        Student student1 = new Student(181213, "안성일", korean);
        Student student2 = new Student(181518, "윤태웅", math);
        Student student3 = new Student(171230, "이순신", korean);
        Student student4 = new Student(171255, "조승연", korean);
        Student student5 = new Student(171590, "최태영", math);

        goodSchool.addStudent(student1); // goodSchool에 학생 추가
        goodSchool.addStudent(student2);
        goodSchool.addStudent(student3);
        goodSchool.addStudent(student4);
        goodSchool.addStudent(student5);

        korean.register(student1); // 국어 과목을 수강하는 학생 등록
        korean.register(student2);
        korean.register(student3);
        korean.register(student4);
        korean.register(student5);

        math.register(student1); // 수학 과목을 수강하는 학생 등록
        math.register(student2);
        math.register(student3);
        math.register(student4);
        math.register(student5);

        dance.register(student1);
        dance.register(student2);
        dance.register(student3);

        // 각 학생의 과목 점수 추가
        addScoreForStudent(student1, korean, 95);
        addScoreForStudent(student1, math, 56);
        addScoreForStudent(student1, dance, 95);

        addScoreForStudent(student2, korean, 95);
        addScoreForStudent(student2, math, 95);
        addScoreForStudent(student2, dance, 85);

        addScoreForStudent(student3, korean, 100);
        addScoreForStudent(student3, math, 88);
        addScoreForStudent(student3, dance, 85);

        addScoreForStudent(student4, korean, 89);
        addScoreForStudent(student4, math, 95);

        addScoreForStudent(student5, korean, 85);
        addScoreForStudent(student5, math, 56);
    }

    // 과목별 점수를 추가하는 메서드
    public void addScoreForStudent(Student student, Subject subject, int point) {
        Score score = new Score(student.getStudentId(), subject, point);
        student.addSubjectScore(score);
    }
}

```
![image](https://github.com/user-attachments/assets/afd1535c-0416-4344-ad34-b11eaf64b257)


