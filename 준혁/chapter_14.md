## 최종 프로젝트 - 학점 산출 프로그램 만들기

- 학생 클래스
```java
class Student {
    private int studentId;
    private String studentName;
    private Subject majorSubject;

    private ArrayList<Score> scoreList = new ArrayList<>();

    public Student(int studentId, String studentName, Subject majorSubject) {
        this.studentId = studentId;
        this.studentName = studentName;
        this.majorSubject = majorSubject;
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

    public void setMajorSubject(Subject subject) {
        this.majorSubject = subject;
    }

    public ArrayList<Score> getScoreList() {
        return scoreList;
    }

    public void setScoreList(ArrayList<Score> arr) {
        this.scoreList = arr;
    }
}
```

- 강의 클래스
```java
class Subject {
    private String subjectName;
    private int subjectId;
    private int gradeType;

    private ArrayList<Student> studentList = new ArrayList<>();

    public Subject(String subjectName, int subjectId, int gradeType) {
        this.subjectName = subjectName;
        this.subjectId = subjectId;
        this.gradeType = Define.AB_TYPE;
    }

    public String getSubjectName() {
        return subjectName;
    }

    public void setSubjectName(String subjectName) {
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

- 점수 클래스
```java
class Score {
    int studentId;
    Subject subject;
    int point;

    public Score(int studentId, Subject subject, int point) {
        this.studentId = studentId;
        this.subject = subject;
        this.point = point;
    }

    public int getStudentId() {
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
        return "학번 : " + studentId + ", " + subject.getSubjectName() + " : " + point;
    }
}
```

- 상수 클래스
```java
class Define {
    public static final int KOREAN = 1001;
    public static final int MATH = 2001;

    public static final int AB_TYPE = 0;
    public static final int SAB_TYPE = 1;
}
```

- 점수 산출 인터페이스 및 기능 구현 클래스
```java
interface GradeEvaluation {
    public String getGrade(int point);
}

// 일반 과목
class BasicEvaluation implements GradeEvaluation {
    @Override
    public String getGrade(int point) {
       String grade;

       if (point >= 90 && point <= 100) grade = "A";
       else if (point >= 80) grade = "B";
       else if (point >= 70) grade = "C";
       else if (point >= 55) grade = "D";
       else grade = "F";
       return grade;
    }
}

// 전공 과목
class MajorEvaluation implements GradeEvaluation {
    @Override
    public String getGrade(int point) {
        String grade;
        if (point >= 95 && point <= 100) grade = "S";
        else if (point >= 90) grade = new String("A");
        else if (point >= 80) grade = "B";
        else if (point >= 70) grade = "C";
        else if (point >= 60) grade = "D";
        else grade = "F";
        return grade;
    }
}

// 이후 PF 강의 평가 클래스 추가가
```

- 결과 출력 클래스
```java
class GenerateGradeReport {
    School school = School.getInstance();
    public static final String TITLE = " 수강생 학점 \t\t\n";
    public static final String HEADER = " 이름 | 학번 |필수과목|점수  \n";
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
        buffer.append("\t"+subject.getSubjectName());
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
            buffer.append(student.getMajorSubject().getSubjectName() + "\t");
            buffer.append(" | ");

            getScoreGrade(student, subject.getSubjectId());

            buffer.append("\n");
            buffer.append(LINE);
        }
    }

    public void getScoreGrade(Student student, int subjectId) {
        ArrayList<Score> scoreList = student.getScoreList();
        int majorId = student.getMajorSubject().getSubjectId();

		// 평가 클래스 추가
        GradeEvaluation[] gradeEvaluations = {new BasicEvaluation(), new MajorEvaluation()};

        for (int i = 0; i < scoreList.size(); i++) {
            Score score = scoreList.get(i);
            if (score.getSubject().getSubjectId() == subjectId) {
                String grade;
                if (score.getSubject().getSubjectId() == majorId)
                    grade = gradeEvaluations[Define.SAB_TYPE].getGrade(score.getPoint());
                else 
                    grade = gradeEvaluations[Define.AB_TYPE].getGrade(score.getPoint());

                buffer.append(score.getPoint());
                buffer.append(" : ");
                buffer.append(grade);
                buffer.append(" | ");
            }
        }
    }
    
    public void makeFooter() {
        buffer.append("\n");
    }
}
```

- 학교 클래스
```java
class School {
    private static School instance = new School();

    private static String SCHOOL_NAME = "Good School?";
    private ArrayList<Student> studentList = new ArrayList<>();
    private ArrayList<Subject> subjectList = new ArrayList<>();

    private School() {}

    public static School getInstance() {
        if (instance == null) 
            instance = new School();
        return instance;
    }

    public ArrayList<Student> getStudentList() {
        return studentList;
    }

    public void addStudent(Student student) {
        studentList.add(student);
    }

    public void addSubject(Subject subject) {
        subjectList.add(subject);
    }

    public ArrayList<Subject> getSubjectList() {
        return subjectList;
    }

    public void setSubjectList(ArrayList<Subject> subjectList) {
        this.subjectList = subjectList;
    } 
}
```

- 테스트 프로그램 작성
```java
    School sh = School.getInstance();
    Subject korean;
    Subject math;
    GenerateGradeReport gradeReport = new GenerateGradeReport();

    public static void main(String[] args) {
        Test test = new Test();
        
        test.createStudent();
        test.createSubject();

        String report = test.gradeReport.getReport();
        System.out.println(report);
    }

    public void createSubject() {
	    // 전공 객체 생성
        korean = new Subject("국어", Define.KOREAN);
        math = new Subject("수학", Define.MATH);

		// PF 평가 방식의 강의의 경우 정책 지정정

		// 학교 객체에 전공 추가
        sh.addSubject(korean);
        sh.addSubject(math);
    }

    public void createStudent() {
        Student student1 = new Student(111111, "aaa", korean);
        Student student2 = new Student(222222, "bbb", math);
        Student student3 = new Student(333333, "ccc", korean);
        Student student4 = new Student(444444, "ddd", korean);
        Student student5 = new Student(555555, "eee", math);

        sh.addStudent(student1);
        sh.addStudent(student2);
        sh.addStudent(student3);
        sh.addStudent(student4);
        sh.addStudent(student5);

        korean.register(student1);
        korean.register(student2);
        korean.register(student3);
        korean.register(student4);
        korean.register(student5);

        math.register(student1);
        math.register(student2);
        math.register(student3);
        math.register(student4);
        math.register(student5);

        addScoreForStudent(student1, korean, 95);
        addScoreForStudent(student1, math, 56);
        
        addScoreForStudent(student2, korean, 95);
        addScoreForStudent(student2, math, 95);
        
        addScoreForStudent(student3, korean, 100);
        addScoreForStudent(student3, math, 88);
        
        addScoreForStudent(student4, korean, 89);
        addScoreForStudent(student4, math, 95);
        
        addScoreForStudent(student5, korean, 85);
        addScoreForStudent(student5, math, 56);
    }

    public void addScoreForStudent(Student student, Subject subject, int point) {
        Score score = new Score(student.getStudentId(), subject, point);
        student.addSubjectScore(score);
    }
}
```