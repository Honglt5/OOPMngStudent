# OOPMngStudent

# ManageStudent
## Môi trường phát triển
+ Bộ công cụ Netbeans version 8.1

##Ôn tập
+ Tạo mảng sinh viên 
+ [Sử dụng kiến thức lập trình OOP](http://javae.net/object-va-class-trong-java-phan-2/)
+ Nhập và Hiển thị Danh sách Sinh viên từ bàn phím [(sử dụng 1 trong 3 cách: Scanner, BufferReader, JoptionPlane)](https://www.sites.google.com/site/ttkuzze/hoctap/java/nhap-xuat-trong-java)
+ Tạo phương thúc tính tổng điểm của từng sinh viên
+ Tìm điểm trung bình cộng trong danh sách sinh viên
+ Tạo phương thức sắp xếp tổng điểm danh sách sinh viên (theo thứ tự tăng dần và thứ tự giảm dần) 
+ Tìm tổng điểm cao nhất trong danh sách sinh viên
+ Tìm tổng điểm thấp nhất trong danh sách sinh viên

##Định nghĩa Class: Student
```
public class Student {
    int ID;
    String name;
    String country;
    int age;
    String gender;
    float score_math;
    float score_literature;
    float score_english;
    
    //dinh nghia ham khoi tao Contructor
    public void Student(){
        this.ID = ID;
        this.name = name;
        this.gender = gender;
        this.country = country;
        this.age = age;
        this.score_math = score_math;
        this.score_literature = score_literature;
        this.score_english = score_english;
    }

    public int getID() {
        return ID;
    }

    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }

    public String getGender() {
        return gender;
    }

    public String getCountry() {
        return country;
    }          

    public float getScore_math() {
        return score_math;
    }

    public float getScore_literature() {
        return score_literature;
    }

    public float getScore_english() {
        return score_english;
    }               
}
```

##Tính tổng điểm của từng Sinh viên
```
//dinh nghia ham tinh tong diem
    float sumScore(float math, float literature, float english)
    {
        float sumScore;
        
        sumScore = math + literature + english;
        return sumScore;        
    }

//dinh nghia phuong thuc tinh tong diem tung sinh vien
    public void sumScoreStudent(Student[] oStudents, int n)
    {
        float sumScore=0;
        
        for(int i=0; i<n ; i++)
        {
            sumScore = sumScore(oStudents[i].getScore_math(),
                                oStudents[i].getScore_literature(),
                                oStudents[i].getScore_english());
            System.out.println("+ Tong diem cua sinh vien co ma sinh vien " + oStudents[i].getID() + " la: " + sumScore);
        }
        
    }
```

##Tính Trung bình cộng tổng điểm của từng sinh viên
```
//dinh nghia ham tinh tong diem trung binh
    float averageScore(float math, float literature, float english)
    {
        float averageScore;
        
        averageScore = (math + literature + english)/3;
        return averageScore;        
    }
    
    //dinh nghia phuong tinh tinh tong diem trung binh cua tung sinh vien
    public void averageScoreStudent(Student[] oStudents, int n)
    {
        float averageScoreStudent;
        
        for(int i=0; i<n; i++)
        {
            averageScoreStudent = averageScore(oStudents[i].getScore_math(), 
                                               oStudents[i].getScore_literature(), 
                                               oStudents[i].getScore_english());
            System.out.println("+ Tong diem trung binh cong cua sinh vien co ma " + oStudents[i].getID() + " la: " + averageScoreStudent);
        }
    }
```

##Sắp xếp danh sách Danh sách Sinh viên theo tổng điểm
```
public void BubbleSortStudent(Student[] oStudents, int n)
    {                       
        for(int j=0; j<n; j++)
        {            
            for(int i=n-1; i>j; i--)
            
                if(sumScore(oStudents[i].getScore_math(),
                            oStudents[i].getScore_literature(),
                            oStudents[i].getScore_english()) < sumScore(oStudents[i-1].getScore_math(),
                                                                oStudents[i-1].getScore_literature(),
                                                                oStudents[i-1].getScore_english()))
                    //Swap(oStudents[i], oStudents[i-1]);
                {    
                    Student temp = oStudents[i];
                    oStudents[i] = oStudents[i-1];
                    oStudents[i-1] = temp;
                };
        }
    }
```

##Tìm Tổng Điểm cao nhất của Sinh viên
```
public float max_sumScoreStudent(Student[] oStudents, int n)
    {
        float maxScore = sumScore(oStudents[0].getScore_math(), 
                                  oStudents[0].getScore_literature(), 
                                  oStudents[0].getScore_english());
        
        for(int i=0; i<n; i++ )            
            if(maxScore<sumScore(oStudents[i].getScore_math(),
                                oStudents[i].getScore_literature(),
                                oStudents[i].getScore_english()))
                maxScore = sumScore(oStudents[i].getScore_math(), 
                                      oStudents[i].getScore_literature(), 
                                      oStudents[i].getScore_english());
        
        return maxScore;            
    }
```

##Tìm Tổng điểm thấp nhất của Sinh viên
```
public float min_sumScoreStudent(Student[] oStudents, int n)
    {
        float minScore = sumScore(oStudents[0].getScore_math(), 
                                  oStudents[0].getScore_literature(), 
                                  oStudents[0].getScore_english());
        
        for(int i=0; i<n; i++ )            
            if(minScore>sumScore(oStudents[i].getScore_math(),
                                oStudents[i].getScore_literature(),
                                oStudents[i].getScore_english()))
                minScore = sumScore(oStudents[i].getScore_math(), 
                                      oStudents[i].getScore_literature(), 
                                      oStudents[i].getScore_english());
        
        return minScore;            
    }
```
