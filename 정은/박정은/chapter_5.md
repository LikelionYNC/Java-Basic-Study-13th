<학생 클래스 구현현>
package school;

import java.util.ArrayList;

public class Student {
    private int studentID;
    private String studentName;
    private Subject majorSubject;

    prinvate ArrayList<Score> scoreList = new ArrayList<Score>();

    public Student(int student, String student, Subject majorSubject) {

        this.studentId = studentId;
        this.studentName = studentName;
        this.majorSubject = majorSubject;
    }

    public void addSubjectScore (Score score) { 
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

    public void setStudent Name (String studentName) { 
        this.studentName = studentName;
    }

    public Subject getMajorSubject() {
        return majorSubject;
    }

    public void setMajorSubject (Subject majorSubject) { 
        this.majorSubject = majorSubject;
    }

    public ArrayList<Score> getScoreList() {
        return scoreList;
    }

    public void setScoreList (ArrayList<Score> scoreList) { 
        this.scoreList = scoreList;
    }
}


<과목 클래스 구현>
package school;

import java.util.ArrayList;
import utils.Define;

public class Subject {
    private String subjectName;
    private int subjectId;
    private int gradeType;

    private ArrayList<Student> studentList = new ArrayList<Student>();

    public Subject(String subjectName, int subjectId) {
        this.subjectName = subjectName;
        this.subjectId = subjectId;
        this.gradeType = Define. AB_TYPE;
    }

    public String getSubjectName() {
        return subjectName;
    }

    public void setSubject Name (String subjectName) {
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

    public void setStudent List (ArrayList<Student> studentList) {
        this.studentList = studentList;
    }

    public int getGradeType() {
        return gradeType;
    }

    public void setGradeType(int gradeType) { 
        this.gradeType = gradeType;
    }

    public void register (Student student) { 
        studentList.add(student);
    }
}


<리포트 클래스 구현>
package school.report;

import java.util.ArrayList;

import grade.BasicEvaluation; 
import grade.GradeEvaluation;
import grade.MajorEvaluation;
import school.School;
import school.Score;
import school.Student;
import school.Subject;
import utils.Define;

public class GenerateGradeReport {
    School school = School.getInstance();
    public static final String TITLE = " 수강생 학점 \t\t\n";
    public static final String HEADER = "이름 | 학번 |필수과목 |점수 \n";
    public static final String LINE = "---------------------------------\ㅜ";

private StringBuffer buffer = new StringBuffer( );

public String getReport( ) {
    ArrayList<Subject> subjectList = school.getSubjectList( );

    for(Subject subject : subjectList) {
        makeHeader(subject);
        makeBody(subject);
        makeFooter( );
    }
    return buffer.toString( );  
}

public void makeHeader(Subject subject) {
    buffer.append(GenerateGradeReport.LINE);
    buffer.append("\t" + subject.getSubjectName( ));
    buffer.append(GenerateGradeReport.TITLE);
    buffer.append(GenerateGradeReport.HEADER);
    buffer.append(GenerateGradeReport.LINE);
}

public void makeBody(Subject subject) {
    ArrayList<Student> studentList = subject.getStudentList( );

    for(int i = 0; i < studentList.size( ); i++) {
        Student student = studentList.get(i);
        buffer.append(student.getStudentName( ));
        buffer.append(" ");
        buffer.append(student.getStudentId( ));
        buffer.append(" ");
        buffer.append(student.getMajorSubject( ).getSubjectName( ) + "\t");
        buffer.append(" ");
        getScoreGrade(student, subject.getSubjectId( ));  
        buffer.append("\n");
        buffer.append(LINE);
    }
}

public void getScoreGrade(Student student, int subjectId) {

    ArrayList<Score> scoreList = student.getScoreList();
    int majorId = student.getMajorSubject().getSubjectId();

    GradeEvaluation[] gradeEvaluation = {new BasicEvaluation(), new MajorEvaluation()};

    for(int i=0; i<scoreList.size(); i++) {
     Score score = scoreList.get(i);
     if(score.getSubject().getSubjectId() == subjectId) {
        String grade;
        if(score.getSubject().getSubjectId() == majorId) 
            grade = gradeEvaluation[Define.SAB_TYPE].getGrade(score.getPoint());
        else 
            grade = gradeEvaluation[Define.AB_TYPE].getGrade(score.getPoint());

        buffer.append(score.getPoint());
        buffer.append(":");
        buffer.append(grade);
        buffer.append(" | ");
      }
    }
  }

public void makeFooter() {
    buffer.append("\n");
  }
}
