site:// https://edu.aliyun.com/lesson_35_306?spm=5176.10731542.0.0.TD0cBI#_306

https://edu.aliyun.com/lesson_36_414#_414

# Java

对象传递：	

* 栈内存 存储 实例对象的地址  即 声明对象 并存储实例化指向的地址
* 堆内存 存储 实例对象的内容  即 对对象属性赋值
* 栈 指向 堆

	​			

	对象产生 分析
	
	垃圾对象：就是堆内存里的实例化 没有 栈内存地址的指向
	
	减少 这样问题的产生


​	
属性为私有 公有的setter getter属性
在set里对属性判断

所有属性使用private封装  然后再setter getter

private 只允许本类使用

### 区别变量 跟 方法

stuName
stuName()   

* 构造方法：方法名与类名一致，没有返回值

Person per1 =  new    Person();
类名   实例   分配内存  构造方法

疑问：为什么不使用void？
	
​	
构造方法作用：
	为类中内容 初始化
	
setter有初始化和修改功能



构造方法 重载：
	参数类型个数 不同
	

匿名对象

-------------------------------------------------

## 简单java类

* 类名有意义，明确描述一个类事物
* 属性 为private
* 必须有一个无参构造方法
* 方法不出现System.out.println
* 返回类完整信息的方法



```java
class Emp{

	private int empno;
	private String ename;
	private String job;
	private double sal;
	private double comm;
	
	public Emp(){}
	public Emp(int eno,String ename,String job,double sal,double comm){
		setEmpno(eno);
	}

	public void setEmpno(int eno){
		empno = eno;
	}

	public String getInfo(){
		return 
	}
}
```

----------------------------------------------------
## 数组



静态数组

数据类型 数组名[]  = new 数据类型 [] {}

--------------------------------------------------


数组与方法调用

* 在方法的参数上接收同一个类型
* 数组上  引用传递



时间复杂度：CPU占用       算法

空间复杂度：内存占用       查询的数据量大





## 对象数组



```java
class Class_name{
    private attribute_1;
    private attribute_2;
    //构造函数
    public Class_name(String att_1,String att_2){
        attribute_1 = att_1;
        attribute_2 = att_2;
    }
    
}

public static class main(){
    public static void main(String args[]){
        Class_name c_name = new Class_name[3];
        c_name[0] = new Class_name(,);
        c_name[1] = new Class_name(,);
        c_name[2] = new Class_name(,);
        
    }
}
```



### String 类



```java
public class Stringssss {
    public static void main(String args[]){
        String str1 = "hello";
        String str2= new String("hello");
        String str3 = str1;
        System.out.println(str1==str2);   //false 比较的是地址
        System.out.println(str1==str3);   //true 指向了同一个堆内存地址
        System.out.println(str1.equals(str2)); //ture 内容
    }
}
```



字符串常量 “ ” 都是String的匿名对象，对象不能为null，否则会抛出NullPointerException异常。

```java
String str = "hello"； // 在堆内存里
```

  

```java
public class Stringssss {
    public static void main(String args[]){
        String str1 = "hello";
        String str2= new String("hello");
        String str3 = str1;
        String str4 = null;

        System.out.println(str1==str2);  //false
        System.out.println(str1==str3);  //true
        System.out.println(str1.equals(str2)); //true
        System.out.println(str1.equals(str4)); //false
        System.out.println(str4.equals(str1)); //NullPointerException异常
    }
}

```

字符串常量 “ ” 都是String的匿名对象，对象不能为null，否则会抛出NullPointerException异常。



### 对象池

对象池就是一个对象数组

直接赋值

```java
String str1 = "hello";
String str2 = "hello";
String str3 = "hello";
System.out.println(str1==str2);  //true
System.out.println(str1==str3);  //true
System.out.println(str2==str3);  //true
```



-------------------------------------------------------



使用 构造方法

会产生两个堆内存 

```java
String str = new String("hello");

// ("hello") 匿名对象
// new 开辟堆内存空间
// String str 指向 new 开辟的堆内存空间
// 因此 出现了一个匿名对象没有指向 的 垃圾
```



```java
String str1 = new String("hello");
String str2 = "hello";
System.out.println(str1 == str2);  // false

//str1 字符串常量没有保存在对象池里
```



String 入对象池方法    手工入池

```java
public String intern();
```



```java
String str1 = new String("hello").intern();
String str2 = "hello";
System.out.println(str1 == str2);  // true
```



### 字符串修改



```java
String str = "hello";
str += " world";
System.out.println(str);  // hello world 

// 刚开始 堆内存存储 hello
// + 在新的堆内存里存储hello world
// 最终str指向新的堆内存
// 即堆内存指向 的变化
// 会产生垃圾堆内存
```



注： 字符串 不要这样拼接

### 字符串 总结：

* 直接赋值
* 比较 equals（）
* 字符串尽量不要改变



## String 类



String就是一个字符数组

String类存在字符串与字符数组的互换函数（重点）

```java
String str = "hello world";
char data [] = str.toCharArray();
for(int x = 0; x < data.length; x ++){
    data[x] -= 32; // 转大写
    System.out.println(data[x]);
}

System.out.println(new String(data,5,5)); //从5开始，往后数5个
//new String(data,5,5)  构造函数
```



```java
public class Stringssss {
    public static void main(String args[]){
        String str = "12342345";
        System.out.println(isNumber(str)?"isNumber":"isnotNumber");
    }
    public static boolean isNumber(String str){
        char data[] = str.toCharArray();
        for (int i =0; i < data.length; i ++){
            if(data[i]<'0' || data[i]>'9'){
                return false;
            }
        }
        return true;
    }
}

```



字节 只适合处理二进制文件



```java
System.out.println("hello".equals("Hello"))；      //false 区分大小写
System.out.println("hello".equalsIgnoreCase("Hello"))；//true 不区分大小写
System.out.println("hello".compareTo("Hello"))；  //返回0，-1，1 可以区分大小关系
```



字符串拆分

IP拆分 

要转义

```java
String data [] = str.split("\\.");
```



```java
public class Stringssss {
    public static void main(String args[]){
        String str = "John,15|Smith,20";
        String data [] = str.split("\\|");
        for (int i =0;i<data.length;i++){
            String temp[] = data[i].split(",");
            System.out.println(temp[0] +'-'+ temp[1]);
            // System.out.println(data[i]);
        }
    }
}
```



## this关键字

* 调用本类属性
* 本类方法（普通方法，构造方法）
* 表示当前对象



### this.属性

类中访问类的属性，属性前就用this



### this 构造方法

this 构造方法的互相调用

```java
public Person(){ //无参构造
    
}
public Person(String name){ //有参构造
    this();
    this.name = name;
}
public Person(String name，int age){ //有参构造
    this(name);
    this.age = age;
}

```

注意：

* this必须在首行
* 构造函数 留有出口 



### this 当前对象







## 引用传递（进阶）



字符串是常量 每一个字符串都是一个堆内存里的

字符串的变更是 指向地址的改变

String是引用类型



字符串  按照基本数据类型 进行分析



## 对象比较



是指 两个对象属性的比较

看对象方法的返回值



本身类具备的功能，比较地址，判断是否为空，判断各个属性。



### 实际应用



```java
public class MemberCar {
    public static void main(String[] args){
        //第一步，根据关系设置相应数据
        Member member = new Member("john",20);
        Car car = new Car("本田",10000.0);
        //设置对象间的引用关系
        member.setCar(car);
        car.setMember(member);
        //第二步，根据关系拉出数据
        //通过人找到车
        System.out.println(member.getMemberInfo());
        System.out.println(member.getCar().getCarInfo());
        //通过车找到人
        System.out.println(car.getCarInfo());
        System.out.println(car.getMember().getMemberInfo());
    }
}
class Member{
    private String name;
    private int age;
    private Car car;
    public Member(String name,int age){
        this.name = name;
        this.age = age;;
    }
    public void setCar(Car car){
        this.car = car;
    }
    public Car getCar(){
        return this.car;
    }
    public String getMemberInfo(){
        return "Member name:"+this.name+",age:"+this.age;
    }
}
class Car{
    private String name;
    private double price;
    private Member member;
    public Car(String name,double price){
        this.name = name;
        this.price = price;
    }
    public void setMember(Member member){
        this.member = member;
    }
    public Member getMember(){
        return this.member;
    }
    public String getCarInfo(){
        return "Car name:"+this.name+"，pirce"+this.price;
    }
}
```



存在孩子



```java
public class MemberCar {
    public static void main(String[] args){
        //第一步，根据关系设置相应数据
        Member member = new Member("john",20);
        Car car = new Car("本田",10000.0);
        Member child = new Member("child",10);
        Car car2 = new Car("小飞",50000.0);
        //设置对象间的引用关系
        member.setCar(car);  //一个人有一辆车
        car.setMember(member);//一辆车属于一个人
        member.setChild(child);//一个人有一个孩子
        child.setCar(car2);   //孩子的车
        //第二步，根据关系拉出数据
        //通过人找到车
        System.out.println(member.getMemberInfo());
        System.out.println(member.getCar().getCarInfo());
        //通过车找到人
        System.out.println(car.getCarInfo());
        System.out.println(car.getMember().getMemberInfo());
        // 孩子的车
        System.out.println(member.getChild().getMemberInfo());
        System.out.println(member.getChild().getCar().getCarInfo());
    }
}
class Member{
    private String name;
    private int age;
    private Member child;
    private Car car;
    public Member(String name,int age){
        this.name = name;
        this.age = age;;
    }
    public void setChild(Member child){
        this.child = child;
    }
    public Member getChild() {
        return this.child;
    }
    public void setCar(Car car){
        this.car = car;
    }
    public Car getCar(){
        return this.car;
    }
    public String getMemberInfo(){
        return "Member name:"+this.name+",age:"+this.age;
    }
}
class Car{
    private String name;
    private double price;
    private Member member;
    public Car(String name,double price){
        this.name = name;
        this.price = price;
    }
    public void setMember(Member member){
        this.member = member;
    }
    public Member getMember(){
        return this.member;
    }
    public String getCarInfo(){
        return "Car name:"+this.name+"，pirce"+this.price;
    }
}
```



电脑例子



```java
class 电脑{
    private 显示器[] 对象;
    private 主机 对象;
    private 键盘 对象;
    private 鼠标 对象;
}
class 显示器{}
class 键盘{}
class 鼠标{}
class 主机{
    private 主板 对象;
}
class 主板{
    private CPU[] 对象;
    private 内存[] 对象;
    private 硬盘[] 对象；
}
class 硬盘{}
class CPU{}
class 内存{}
```



细小的类 组合到一起成为一个大类

合成设计模式



## 数据表与简单Java类



* Java类名 = 实体表名
* Java类属性 = 字段
* Java的一个对象 = 表的一行记录
* 对象数组 = 表的多行记录
* 外键关系 = 引用配置



将所有基础字段转化为类的属性

```java
class Emp{
    private int empno;
    private String ename;
    private String job;
    private double sal;
    private double comm;
    public Emp(){}
    public Emp(int empno,String ename,String job,double sal,double comm){
        this.empno = empno;
        this.ename = ename;
        this.job = job;
        this.sal = sal;
        this.comm = comm;
    }
    public String getEmpInfo(){
        return "Emp empno : " +  this.empno+",ename:" + this.ename +" ,job:" this.job+",sal:"+this.sal+",comm:"+ this.comm;
    }
}
class Dept{
    private int depno;
    private String dname;
    private String loc;
    public Dept(){}
    public Dept(int depno,String dname,String loc){
        this.depno = depno;
        this.dname = dname;
        this.loc = loc;
    }
    public String getDeptInfo(){
        return "Dept depno:"+this.depno + ",dname:"+this.dname + ",loc:"+this.loc;
    }
}
```



### 一对多关系

```java
public class Emp {
    public static void main(String args[]){
        // 类对象间关系
        //实例化对象
        Emps ea = new Emps(1113,"james3","普通",1000.0,0.0);
        Emps eb = new Emps(1112,"james2","中层",2000.0,0.0);
        Emps ec = new Emps(1111,"james1","高层",3000.0,0.0);
        Dept dept = new Dept(10,"Accounting","Beijing");
        //雇员领导间关系
        ea.setHead(eb);
        eb.setHead(ec);
        //雇员与部门关系
        ea.setDept(dept);
        eb.setDept(dept);
        ec.setDept(dept);
        //部门与雇员的关系
        dept.setEmp(new Emps[]{ea,eb,ec});
        //取出数据
        //一个部门有多个雇员
        System.out.println(dept.getDeptInfo());
        for(int i = 0;i<dept.getEmp().length;i++){
            System.out.println("\t|-"+dept.getEmp()[i].getEmpInfo());

            if(dept.getEmp()[i].getHead() != null){
                System.out.println("\t\t|-"+dept.getEmp()[i].getHead().getEmpInfo());
            }
        }
        System.out.println("---------------------------------------");
        //根据一个雇员找到雇员对应的领导信息和雇员所属部门信息
        System.out.println(eb.getEmpInfo());
        if(eb.getHead()!=null){
            System.out.println("\t|-"+eb.getHead().getEmpInfo());
        }
        if(eb.getDept()!=null){
            System.out.println("\t\t|-"+eb.getDept().getDeptInfo());
        }
    }
}
class Emps{
    private int empno;
    private String ename;
    private String job;
    private double sal;
    private double comm;
    private Emps head; //员工领导
    private Dept dept;//员工所属部门
    public Dept getDept() {
        return dept;
    }
    public void setDept(Dept dept) {
        this.dept = dept;
    }
    public Emps getHead() {
        return head;
    }
    public void setHead(Emps head) {
        this.head = head;
    }
    public Emps(){}
    public Emps(int empno,String ename,String job,double sal,double comm){
        this.empno = empno;
        this.ename = ename;
        this.job = job;
        this.sal = sal;
        this.comm = comm;
    }
    public String getEmpInfo(){
        return "[Emp] - empno:"+ this.empno+
      ",ename:" + this.ename+
       ",job:"+ this.job+
       ",sal:"+ this.sal+
        ",comm:"+this.comm;
    }
}
class Dept{
    private int deptno;
    private String dname;
    private String loc;
    private Emps[] emps; //部门里的员工
    public Emps[] getEmp() {
        return this.emps;
    }
    public void setEmp(Emps[] emps) {
        this.emps = emps;
    }
    public Dept(){}
    public Dept(int deptno,String dname,String loc){
        this.deptno = deptno;
        this.dname = dname;
        this.loc = loc;
    }
    public String getDeptInfo(){
        return "[Dept]-deptno:"+this.deptno + ",dname:"+this.dname + ",loc:"+this.loc;
    }
}

```



### 多对多关系

学生跟课程间的关系

一门课有多个学生，一个学生上多门课



```java
public class Stu {
    public static void main(String[] args){
        //根据结构进行关系的设置
        //1.创建对象
        Student stu1 = new Student(1,"张三",18);
        Student stu2 = new Student(2,"王五",16);
        Student stu3 = new Student(3,"赵四",17);
        Course ca = new Course(1001,"数学",3);
        Course cb = new Course(1002,"语文",2);
        Course cc = new Course(1003,"英文",3);
        //2.设置学生与课程的关系，
        stu1.setStudentCourse(new StudentCourse[]{
                new StudentCourse(stu1,ca,99),
                new StudentCourse(stu1,cb,96),
                new StudentCourse(stu1,cc,93)
        });
        stu2.setStudentCourse(new StudentCourse[]{
                new StudentCourse(stu2,ca,88),
                new StudentCourse(stu2,cc,82)
        });
        stu3.setStudentCourse(new StudentCourse[]{
                new StudentCourse(stu3,ca,79),
                new StudentCourse(stu3,cb,79)
        });
        //3.设置课程与学生的关系
        ca.setStudentCourse(new StudentCourse[]{
                new StudentCourse(stu1,ca,99),
                new StudentCourse(stu2,ca,88),
                new StudentCourse(stu3,ca,79)
        });
        cb.setStudentCourse(new StudentCourse[]{
                new StudentCourse(stu1,cb,96),
                new StudentCourse(stu3,cb,79)
        });
        cc.setStudentCourse(new StudentCourse[]{
                new StudentCourse(stu1,cc,93),
                new StudentCourse(stu2,cc,82)
        });
        //根据结构取出数据
        //找出一门课程，以及参加此课程的所有学生信息，以及他的成绩
        System.out.println(ca.getInfo());
        for(int i =0;i<ca.getStudentCourse().length;i++){
            System.out.println("\t|-"+ca.getStudentCourse()[i].getStudent().getInfo()+
                               ",score:"+ca.getStudentCourse()[i].getScore());
        }
        System.out.println("----------------------------------");
        System.out.println(stu1.getInfo());
        for(int i = 0;i<stu1.getStudentCourse().length;i++){
            System.out.println("\t|-"+stu1.getStudentCourse()[i].getCourse().getInfo()+
                               ",score:"+stu1.getStudentCourse()[i].getScore());
        }
    }
}

class Student{
    private int stuid;
    private String name;
    private int age;
    private StudentCourse studentCourse[];
    public StudentCourse[] getStudentCourse() {
        return studentCourse;
    }
    public void setStudentCourse(StudentCourse[] studentCourse) {
        this.studentCourse = studentCourse;
    }
    public Student(){}
    public Student(int stuid,String name,int age){
        this.stuid = stuid;
        this.name = name;
        this.age = age;
    }
    public String getInfo(){
        return "Student stuid:"+this.stuid+",name:"+this.name+",age"+this.age;
    }
}
class Course{
    private int cid;
    private String name;
    private int credit;
    private StudentCourse studentCourse[];
    public StudentCourse[] getStudentCourse() {
        return studentCourse;
    }
    public void setStudentCourse(StudentCourse[] studentCourse) {
        this.studentCourse = studentCourse;
    }
    public Course(){}
    public Course(int cid,String name,int credit){
        this.cid = cid;
        this.name = name;
        this.credit = credit;
    }
    public String getInfo(){
        return "Course cid:"+this.cid+",name:"+this.name+",credit:"+this.credit;
    }
}
//学生选课
class StudentCourse{
    private Student student;
    private Course course;
    private double score;
    public StudentCourse(){}
    public StudentCourse(Student student,Course course,double score){
        this.student = student;
        this.course = course;
        this.score = score;
    }
    public Student getStudent(){
        return this.student;
    }
    public Course getCourse(){
        return this.course;
    }
    public double getScore(){
        return this.score;
    }
}
```



### 角色与权限





## static关键字



### 1.static 属性



```java
class Person{
    private String name;
    private int age;//封装：getter setter
    String country = "中国";
    public Person(String name,int age){
        this.name = name;
        this.age = age;
    }
    public String getInfo(){
        return "Person name:"+ this.name +",age:"+ this.age 
            + ",country:"+this.country;
    }
}
public class P{
    public static void main(String args[]){
        Person p1 = new Person("张三",10);
        Person p2 = new Person("李四",12);
        Person p3 = new Person("王五",11);
        System.out.println(p1.getInfo());
        System.out.println(p2.getInfo());
        System.out.println(p3.getInfo());
    }
}
```

输出

```java
Person name:张三,age:10,country:中国
Person name:李四,age:12,country:中国
Person name:王五,age:11,country:中国
```



将一个属性变为共享属性，即在该属性前 加 static 关键字即可。



```java
class Person11{
    private String name;
    private int age;//封装：getter setter
    static String country = "中国";
    public Person11(String name,int age){
        this.name = name;
        this.age = age;
    }
    public String getInfo(){
        return "Person name:"+ this.name +",age:"+ this.age
                + ",country:"+this.country;
    }
}
public class P{
    public static void main(String args[]){
        Person11 p1 = new Person11("张三",10);
        Person11 p2 = new Person11("李四",12);
        Person11 p3 = new Person11("王五",11);
        Person11.country = "民国";    //只改了一个对象
        System.out.println(p1.getInfo());
        System.out.println(p2.getInfo());
        System.out.println(p3.getInfo());
    }
}
```

输出

```java
Person name:张三,age:10,country:民国
Person name:李四,age:12,country:民国
Person name:王五,age:11,country:民国
```

结论：使用static关键字的属性， 则该属性保存在全局数据区的内存空间中，所有对象都可以访问该数据区。

访问 static属性都是用类名称

* 所有非static属性，必须实例化后才可以使用
* 所有static属性，与实例化无关

注意：非static属性 与 static属性

当不想受到实例化对象控制时，使用static

### 2.static 方法

static定义的方法，也可以直接被类名称访问。



非static方法与 static方法

* 所有static方法 不允许 调用非static属性或方法
* 所有非static方法允许 访问 static属性或方法



原因：所有static方法 可以 在没有实例化对象的时候 访问

​           而 非static 需要在实例化后 访问



static方法 目的 ：不受类的限制，在没有实例化的时候 就可以使用static 方法



### 3.主方法组成



static方法 是 独立于 类之外的使用原则



主方法组成：

public static 数据类型 main

* public : 表示是公共的，主方法
* static：执行java程序是类名称，不受类是否实例化影响
* void：主方法是一切的起点
* main：系统定义好的名称
* String args[]：表示该类执行时的传入参数



### 4.static 应用

使用static做对象产生计数的统计功能

```java
class Person{
    private static int count = 0;
    public Person(){
        System.out.println(" "+ ++count);
    }
}
public class T{
    public static void main(String args[])
    	new Person;
    	new Person;
}
```



## 代码块

* 普通代码块
* 构造块：构造块 优先 构造方法先执行
* 静态块
  * 在主类的静态块：优先主方法执行。
  * 在非主类的静态块：优先构造块先执行，且只执行一次，作用就是为static属性初始化。



## 内部类



```java
class Outer{	//外部类
    private String msg = "hello";
    class Inner{	//内部类
        public void print(){   //定义一个普通方法
            System.out.println(msg);	//调用msg属性
        }
    }
    
    public void fun(){
        Inner in = new Inner();
        in.print();
    }
}
public class OI{
    public static void main(String args[]){
        Outer outer = new Outer();
        outer.fun();
    }
}
```

访问内部类就需要调用外部类的方法。

另外一种方法：

​		外部类.内部类  内部类对象 =  new 外部类().new  内部类()

```java
class Outer{	//外部类
    private String msg = "hello";
    class Inner{	//内部类
        public void print(){   //定义一个普通方法
            System.out.println(msg);	//调用msg属性
        }
    }
}
public class OI{
    public static void main(String args[]){
        //声明内部类对象
        Outer.Inner in = new Outer().new Inner();
        in.print();
    }
}
```



```java
class Outer{	//外部类
    private String msg = "hello";
    private class Inner{	//内部类
        public void print(){   //定义一个普通方法
            System.out.println(msg);	//调用msg属性
            //System.out.println(Outer.this.msg);	//调用外部类的msg属性
            // 如果是this.msg 是调用Inner的。
            // 调用外部类 Outer 这是 外部类.this.属性
        }
    }
     public void fun(){
        Inner in = new Inner();
        in.print();
    }
}
public class OI{
    public static void main(String args[]){
        new.Outer().fun();
    }
}
```



### static 内部类(了解)



```java
class Outer{
    private static String msg;
    static class Inner{
        //静态内部类 只能调用外部类中的static操作
        System.out.println();
    }
}
public class Test{
    public static void main(String args[]){
        Outer.Inner in = new Outer.Inner();
        in.print();
    }
}
```



### 在方法上的内部类



理论上内部类可以定义在类的任意位置，类中，方法中，代码块中



在方法中定义内部类是最多的



```java
class Outer{
    private String msg;
    public void fun(int num){
         class Inner{//静态内部类
        	public void print(){
                System.out.println("num="+num);
                System.out.println("msg="+msg);
            }
    	}
        new Inner().print();//产生内部类，并调用方法
    }
}
public class Test{
    public static void main(String args[]){
        Outer out = new Outer();
        out.fun(100);
    }
}
```

注意：jdk1.8之前有问题。 在参数前加final



jdk1.7及以前，



内部类特点：

* 破坏了程序的结构
* 方便进行私有属性的访问（外部类，内部类的）
* 当发现类名称出现“.”，就是内部类



## 继承



在已有功能上扩充



class 子类 extends 父类;



* 调用子类对象， 默认先调用父类的构造方法，再调用子类的构造方法

  * 如果父类的构造方法没有无参的，则在子类里需要用super明确的指出。

  ```java
  class Person{
      public Person(String name,int age){//构造方法
          
      }
  }
  class Students extends Person{
      public Students(String name,int age,String school){
          super(name,age);
          
      }
  }
  ```

  


不允许多继承，可以多层继承



隐式继承，private的属性 不能直接使用，需要用get





## 覆写

### 方法覆写

子类定义了与父类方法名，参量类型个数一样的



* 看new哪个类
* 看是否覆写了吗



方法覆写的访问权限不能比父类更严格

private<default<public



方法写public

属性写private



如果父类方法使用了private，则该方法只能被父类使用



#### 重载与覆写的区别

* 重载overloading  覆写override
* 方法名相同，参数类型及个数不同（重载）
* 方法名相同，返回值类型，参数个数类型完全相同（覆写）
* 一个类中（重载）
* 继承关系里（覆写）
* 权限没有限制（重载）



### 属性覆写



### super

子类调用父类的方法，就用super

super是子类访问父类

this是访问本类





## 数组操作（例子）



```java
public class Arrayss {
    public static void main(String [] args){
        ReverseArray arr = new ReverseArray(5);
        System.out.println(arr.add(1));
        System.out.println(arr.add(3));
        System.out.println(arr.add(54));
        System.out.println(arr.add(234));
        System.out.println(arr.add(23));
        System.out.println(arr.add(23));
        int res[] = arr.getData();
        for (int i = 0; i<res.length;i++){
            System.out.print(res[i]+",");
        }
    }
}
class Array{
    private int [] data;
    private int foot = 0;
    public Array(int len){
        if (len>0){//正常数组
            this.data = new int[len];//开辟空间
        }else{
            this.data = new int [1]; //开辟一个空间
        }
    }
    public boolean add(int num){
        if(this.data.length<=this.foot){ //没有空间
            return false;
        }
        this.data[this.foot++] = num;  //赋值
        return true;
    }
    public int[] getData(){ //获取数据
        return  this.data;
    }
    public void inc(int n){//动态扩展数组

    }
}
//数组排序
class SortedArray extends Array{
    public SortedArray(int len){
        super(len);
    }
    public int[] getData(){ //获取数据
        java.util.Arrays.sort(super.getData());
        return super.getData();
    }
}
//数组翻转
class ReverseArray extends Array{
    public ReverseArray(int len){
        super(len);
    }
    public int [] getData(){
        int center = super.getData().length/2;
        int head = 0;
        int tail = super.getData().length - 1;
        for(int i = 0; i<center;i++){
            int temp = super.getData()[head];
            super.getData()[head] = super.getData()[tail];
            super.getData()[tail] = temp;
            head ++;
            tail --;
        }
        return super.getData();
    }
}

```



继承、覆写



## final

终结器

可以定义类，方法，常量

* final定义的**类**  **不能有子类**
* final定义的**方法** **不能被子类覆写**
* final定义的**常量 ** **必须在声明时赋值，且不能修改**

开发中定义常量是用public static final  来定义全局常量

常量标识符 使用 全大写



## 多态性

* 方法多态性
  * 方法的重载：同一个方法名称可以根据参数类型个数的不同调用不同的方法
  * 方法的覆写：同一个父类的方法，根据子类
* 对象的多态性：（前提：方法覆写）
  * （自动）对象的向上转型：父类 父类对象 = 子类实例；
  * （强制）对象的向下转型：子类 子类对象  = （子类）父类实例；

不管是哪一个向上转型，核心是看使用了哪一个子类(new)，其向上转型（父类）方法是否被子类覆写。



向下转型：将父类对象变为子类对象

原因（为什么向下转型）：当需要子类扩充操作时，就需要向下转型。



子类向上转型到父类之后，才能向下转型到指定的子类



```java
public class AB {
    public static void main(String[] args){
        A a = new B();
        System.out.println(a instanceof A);
        System.out.println(a instanceof B);
    }
}
class A{
    public void print(){
        System.out.println("A print");
    }
}
class B extends A{
    public void print(){
        System.out.println("B print");
    }
    public void prints(){
        System.out.println("B prints");
    }
}

```



对象的向上转型有一个最核心的用处：操作参数统一。

```java
class Person{
    public void takeoff(){
        System.out.println("脱");
    }
}
class Student extends Person{
    public void takeoff(){
        System.out.println("学生脱");
    }
}
class Worker extends Person{
    public void takeoff(){
        System.out.println("工人脱");
    }
}
public class Test{
    public static void main(String [] args){
    	in(new Student());
        in(new Worker());
	}
    public static void in(Person per){
        per.takeoff();
    }
}
//结果：
//学生脱
//工人脱

```



* 多态性实行了方法的覆写
* 对象向上转型可以实现接受参数的统一
* 两个没有关系的对象，是不能进行转型。



## 抽象类

不要一个类去继承一个已经实现好了的类。

只继承抽象类或接口



对象多态性的核心在于方法的覆写。



### 抽象类的基本概念



抽象方法指 的是 只声明 而 未实现（没有方法体，没有大括号）

abstract关键字类定义



使用原则：

* 抽象类必须有子类
* 抽象类的子类（不是抽象类）必须覆写抽象类的全部抽象方法
* 抽象类对象可以通过对象多态性，利用其子类为其实例化



还有其他形式：



```java
abstract class A{
    private String msg = "123"; //属性
    public void print(){ //普通方法
        System.out.println();
    }
    
    //一种形式
    public static A getInstance(){//取得A类对象
        class B extends A{ //定义抽象类的子类(内部类)
            public void fun(){
                System.out.println("内部");
            }
        }
        return new B();
    }
    
    public abstract void fun();//抽象方法
}
public class Test{
    public static void main(String [] args){
        A a = A.getInstance();
        a.fun();
    }
}
```









* 进行类的加载
* 类对象空间开辟
* 类对象中属性初始化（构造函数）

结论：如果构造方法没有执行，那么对象中的属性一定是对应数据类型的默认值。



抽象类中允许定义没有任何抽象方法



抽象类一定不能用final，因为使用final定义的类不能有子类

也不能用private定义，因为抽象方法必须被覆写



抽象类也分为内部抽象类和外部抽象类。内部抽象类可以用static定义，描述为外部抽象类。







## 接口

抽象方法和全局常量的集合

子类使用接口，则要用implements关键字，

如果子类不是抽象类，则子类必须覆写 接口 中的 全部抽象方法

通过子类的向上转型，实例化对象得到接口的实例化对象

```java
interface IMessage{
    public static final String MSG = "aaa";
    public abstract void print();
}
interface INews{
    public abstract String get();
}

//一个类可以实现多个接口
class MessageImpl implements IMessage,INews{
    public void print(){
        System.out.println(IMessage.MSG);
    }
    public String get(){
        return IMessage.MSG;   //访问常量都建议加上类名称
    }
}

public class Test{
    public static void main(String args[]){
        IMessage m = new MessageImpl();//子类为父接口实例化
        m.print();
        ((MessageImpl) m).get();   
    }
}

```

通过子类实例化父接口后，父接口之间互相转换。





接口里 只允许有public权限



接口里多是抽象方法



子类要实现接口 又要继承抽象类的时候，先使用extends继承一个抽象类，implements实现多个接口



子类继承抽象类 实现接口，可以通过子类实例化，抽象类和接口可以互相转换。



一个接口可以extends继承多个父接口



接口可以定义一系列内部接口

其中static内部接口，就相当于外部接口



### 接口标准

* 定义操作标准

  * 例子

    * ```java
      interface USB{
          public void setup();
          public void work();
      }
      
      class Computer{
          public void plugin(USB usb){	//只能插USB设备
              usb.setup();
              usb.work();
          }
      }
      
      class Flash implements USB{
          public void setup(){
              System.out.println("flash安装");
          }
          public void work(){
              System.out.println("flash工作");
          }
      }
      class Printer implements USB{
          public void setup(){
              System.out.println("Printer安装");
          }
          public void work(){
              System.out.println("Printer工作");
          }
      }
      
      public class Test{
          public static void main(String args[]){
              Computer com = new Computer();
              com.plugin(new Flash());
              com.plugin(new Printer());
          }
      }
      ```

    * 使用接口和对象多态性的概念结合之后，对于参数的统一更加明确了。

    * 而且可以发现 接口是在类之上的设计抽象。

    * 停车场停车：

      * 停车场   定义了车的接口（即车的标准）  符合车标准的车到停车场

    * 先设计接口，再写类。

* 表示能力

* 在分布式中暴露远程服务方法



### 工厂设计模式（重点）

经常使用的是（工厂，代理，单例）



```java
interface IFruit{ // 
    public void eat();
}
class Apple implements IFruit{
    public void eat(){
        System.out.println("削皮吃苹果");
    }
}
class Orange implements IFruit{
    public void eat(){
        System.out.println("剥皮吃橘子");
    }
}
public class Test{
    public static void main(String args[]){
        //子类为接口进行对象的实例化处理
        //IFruit fruit = new Apple();
        IFruit fruit = new Orange();
        fruit.eat();
    }
}
```

分析：

此程序实现的关键是IFruit fruit = new Apple();，如果没有此语句，接口对象无法实例化。

主方法是个客户端，程序的修改不应该影响到客户端。



Java实现可移植性的关键是JVM，



new 是整个开发的最大耦合元凶。解耦合的关键是引入第三方 Factory来描述。



```java
interface IFruit{ // 
    public void eat();
}

class Factory{
    //此时 Factory 产生实例化对象没有意义。
    public static IFruit getInstance(String classname){
        if("apple".equals(classname)){
            return new Apple();
        }
        if("orange".equals(classname)){
            return new Orange();
        }
        return null;
    }
}
class Apple implements IFruit{
    public void eat(){
        System.out.println("削皮吃苹果");
    }
}
class Orange implements IFruit{
    public void eat(){
        System.out.println("剥皮吃橘子");
    }
}
public class Test{
    public static void main(String args[]){
        if(args.length!=1){//没有传递一个参数
            System.out.println("程序错误");
            System.exit(1);//退出程序
        }
        IFruit fruit = Factory.getInstance(args[0]);
        fruit.eat();
    }
}
```

当切换IFruit子类的时候，主方法没有任何变化。

此方式为工厂模式。



### 代理设计模式（Proxy）

所谓代理，严格讲，两个子类共同实现一个接口，其中一个子类负责真实的业务实现，另一个负责完成辅助主题业务操作。



代理设计



```java
interface ISubject{ //核心功能
    public void save();
}
class RealSubject implements ISubject{//负责主业务
    public void save(){
        System.out.println("。。。");
    }
}
class ProxySubject implements ISubject{//代理，辅助类
    private ISubject subject;//真正操作业务
    //在创建代理类对象的时候，必须设置要代理的真实主题。
    public ProxySubject(ISubject subject){
        this.subject = subject;
    }
    public void broken(){
        System.out.println("1.进门");
    }
    public void get(){
        System.out.println("2.获得表彰");
    }
    public void save(){//接口子类一定要实现抽象方法
        this.broken();//真实操作前的准备
        this.subject.save();//调用真实的业务
        this.get();//收尾
    }
}
class Factory{
    public static ISubject getInstance(){
        return new ProxySubject(new RealSubject()); 
    }
}
public class Test{
    public static void main (String args[]){
        ISubject sub = Factory.getInstance();
        //通过代理类对象发出，利用代理类来实现真实业务调用。
        sub.save();
    }
}
```



代理的本质：所有真实业务操作都有一个与之辅助的功能类共同完成。



### 抽象类与接口的区别



接口优先选择。抽象类可以定义普通方法。

* 关键字
* 结构组成
  * 抽象类：抽象方法、普通方法、全局常量、全局变量、属性、构造方法
  * 接口：抽象方法、全局常量
* 权限：
  * 抽象类：全部
  * 接口：public
* 子类使用
  * 抽象类：extends
  * 接口：implements
* 关系：
  * 抽象类：一个抽象类可以实现多个接口
  * 接口：一个接口不能继承抽象类，但是可以用extends来继承过个父接口。
* 子类限制
  * 抽象类：一个子类只能继承一个抽象类
  * 接口：一个子类可以实现多个接口

除了单继承外，抽象类与接口都是类似的，但是实际开发中，抽象类的设计要比接口复杂。



总结：

* 接口的细分：接口的继承
* 抽象类实现一个接口
* 子类继承抽象类
* 实例化子类



接口是java核心

优先考虑接口，以避免单继承局限



## 匿名内部类



基本上是在接口或者抽象类上使用匿名内部类



## Object类

Object是java里的基础类，除了Object类，其他的类都具有继承关系的。默认继承Object父类。



Object类是参数的最高级统一类型。但是，Object类本身具备一些定义的方法：



熟悉 Object类中的普通方法



### 获得对象信息

默认得到的是对象地址编码，而String类的时候，得到的就是内容，原因在toString（）方法问题。

Object 类中听  toString方法只能得到一个对象的地址（这是所有对象都有的共同特征）

如果不满意，就覆写toString方法



toString（）取得对象信息

字符串是最重要的。

遇到字符串，不管什么类型都会变成字符串。



### 对象比较



equals()



### 接受引用数据类型



包括：数组，接口



Object真正达到了参数的统一，如果有一个类 希望接收所有的数据类型，就使用Object。



## 包装类

将基本数据类型包装为一个类对象的本质 就是在于方便使用Object进行接收处理。



* 对象型(Object直接子类)：Boolean, Character
* 数值型(Number直接子类)：

Number类

* Number类定义：public abstract class Number
* 在Number类里面定义了6个重要方法：intValue(), shortValue(), byteValue(), longValue(), floatValue(), doubleValue().



### 装箱拆箱



```java
Integer num = new Integer(10); //装箱
int x = num.intValue();   //拆箱
```



自动装箱 自动拆箱



使用int 还是Integer

* 在接收数据，一定使用int，保存数据的会用Integer
  * Integer可以赋值为null
* 简单java类，不再使用简单数据类型，全换为包装类



### 字符串与基本数据类型的转换



开发中，都是字符串的输入，需要将字符串转成其他基本数据类型。 

因此需要包装类的支持

* String变成 int类型

  * 用到的是Integer类 public static int parseInt(String s);

  * ```java
    String str = "123";
    int num = Integer.parseInt(str);
    ```

    

* String变成 double类型

  * 用到的是Double类 public static int parseDouble(String s);

  * ```java
    String str = "123";
    double num = Double.parseDouble(str);
    ```

    

* String变成 Boolean类型

  * 用到的是Boolean类 public static int parseBoolean(String s);

  * ```java
    String str = "123";
    boolean num = Boolean.parseBoolean(str);
    ```

  * 如果字符串不是true或者false，则统一按false来处理。

注意： 如果字符串中有非数字，则转数字过程中就出现错误。NumberFormatException





基本数据类型转成字符串，则有两种方式

* 任何数据类型使用了“+” 连接空白字符串就变成字符串类型（会产生垃圾内存）

* 使用String类Valueof()

  * ```java
    String str = String.valueOf(100);
    ```

    

## 包的定义







## jar命令



保存*.class文件的压缩包



jar需要在CLASSPATH中配置后，才可以使用





## 单例设计模式



是指 一个类只允许产生一个实例化对象



类  一旦无参构造方法是私有化，则外部无法调用无参构造进行实例化

如果要使用类中的普通方法， 则必须要提供实例化对象。可以在类内部产生实例化对象。

```java
class Singleton{
    //在类内部是允许访问私有的结构，所以在类内部产生实例化对象
    static Singleton instance = new Singleton();//内部产生实例化对象
    private Singleton(){}// 私有化的无参构造方法
    public void print(){
        System.out.print("aaa");
    }
}


public class Test{
    public static void main(String args[]){
        Singleton s = null;  //声明
        s = Singleton.instance; //实例化
        s.print();
    }
}
```



```java
class Singleton{
    //在类内部是允许访问私有的结构，所以在类内部产生实例化对象
    private final static Singleton INSTANCE = new Singleton();//内部产生实例化对象
    public static Singleton getInstance(){
        return INSTANCE;
    }
    
    
    private Singleton(){}// 私有化的无参构造方法
    public void print(){
        System.out.print("aaa");
    }
}


public class Test{
    public static void main(String args[]){
        Singleton s = null;  //声明
        s = Singleton.getInstance; //实例化
        s.print();
    }
}
```



单例设计模式：懒汉式、饿汉式

上面的例子就是饿汉式



懒汉式：只有当第一次调用Singleton类 才会进行实例化的处理操作。



### 多例

只是比单例追加了更多个内部实例化对象的产生



```java
class Sex{
    public static final int MALE_CMD = 1;
    public static final int FEMALE_CMD = 2;
    private static finale Sex MALE = new Sex("男");
    private static finale Sex FEMALE = new Sex("女");
    private String title;
    private Sex(String title){   //构造方法必须私有化
        this.title = title;
    }
    
    public static Sex getInstance(int ch){
        switch(ch){
            case MALE_CMD:
                return MALE;
            case FEMALE_CMD:
                return FEMALE;
            default:
                return null;
        }
    }
    public String toString(){
        return this.title;
    }
}

public class Test{
    public static void main(String args[]){
        Sex a = Sex.getInstance(Sex.MALE_CMD);
        System.out.println(a);
    }
}
```

* 构造方法私有化
* 类内部一定会提供一个static方法，用于取得类的实例化对象



代码结构需清楚

多例 已被 枚举取代了





## 异常捕获与处理



```java
try{

}catch(Exception e){
	e.printStackTrace();
}finally{
    
}

```



throws

```java
class 
```

方法上使用了throws，则在main里要用try...catch



throw





## 链表

数据结构 主要核心是  引用 + 递归

数组是固定长度，链表



链表基本雏形：

```java
class Node{  //只有Node类才可以在保存数据的同时 设置数据的前后关系
    private Object data;   // 真正要保存的数据
    private Node next;//定义下一个节点
    public Node(Object data){   //保存数据
        this.data = data;
    }
    public void setData(Object data){
        this.data = data;
    }
    public Object getData(){
        return this.data;
    }
    public void setNext(Node next){
        this.next = next;
    }
    public Node getNext(){
        return this.next;
    }
}
public class Test{
    public static void main(String args[]){
        //1.封装几个节点
        Node root = new Node("头");
        Node n1 = new Node("A");
        Node n2 = new Node("B");
        Node n3 = new Node("C");
        //2.设置节点的关系
        root.setNext(n1);
        n1.setNext(n2);
        n2.setNext(n3);
                
        //设置好关系之后，取数据 要用递归的方式取
        // 递归：自己调用自己，有结束条件
        print(root);
        
    }
    
    public static void print(Node node){
        if(node != null){ //当前存在节点
            System.out.println(node.getData());
            print(node.getNext());
        }
        
    }
}
```

结论：整个链表的实现过程中Node类的核心作用：保存数据以及前后关系。



```java

class Link{						// 负责链表的操作
    // 将Node类定义为内部类，表示Node类只被Link调用
    private class Node{ 		// 负责数据与节点关系的匹配
        private Object data;	// 保存节点数据
        private Node next;		//下一个节点
        public Node(Object data){
            this.data = data;
        }
        //第一次调用addNode，this = Link.root
        //第二次调用：this = Link.root.next
        //第三次调用：this = Link.root.next.next
        public void addNode(Node newNode){
            //处理节点关系
            if(this.next == null){ //当前节点下一个为空，表示可以保存
                this.next = newNode;
            }else{ 				//现在当前节点下一个不为空
                this.next.addNode(newNode);
            }
        }
        //第一次调用：this = Link.root
        //第二次调用：this = Link.root.next 
        public void toArrayNode(){
            Link.this.reData[Link.this.foot ++] = this.data;
            if(this.next！=null){ //现在还有下一个节点
                this.next.toArrayNode();
            }
        }
	}
    //=================以下为Link类=======================//
    // 增加，删除，修改，取出某数据
    private Object[] reData; //返回类型
    private int foot = 0;// 操作的脚标
    private int count = 0; //当前保存的个数
    private Node root; //属于根节点，没有根节点就无法进行数据的保存
    public void add(Object data){
        if(data == null){
            return ; 	//方法结束
        }
        // 如果要进行数据的保存，则必须将数据封装到Node
        // 如果没有封装，则无法确定好节点的前后顺序
        Node newNode = new Node(data);
        if(this.root == null){
            this.root = newNode;
        }else{//根节点存在
            //把此时的节点顺序的处理，交给Node自己处理
            this.root.addNode(newNode);
        }
        this.count ++ ;
    }
    public int size(){
        return this.count;
    }
    //为空判断，与个数是捆绑一起的
    public boolean isEmpty(){
        return this.root == null && this.count == 0;
    }
    // 在link类中定义一个返回类型的属性（数组）
    public Object[] toArray(){
        if(this.count == 0){
            return null;
        }
        //现在链表中存在有数据，则开辟指定长度的数组
        // 该数组一定要交给Node类进行处理。
        this.reData = new Object[this.count];
        this.foot = 0;// 进行清零处理，需要进行脚标操作
        this.root.toArrayNode();//将数据的取出处理交给Node类完成。
        return this.reData;
    }
}
public class Test{
    public static viod main(String args[]){
        Link all = new Link();
       // System.out.println(all.size());
       // all.add("A");
       // all.add("B");
       // all.add("C");
       // System.out.println(all.size());
       	all.add("A");
        all.add("B");
        all.add("C");
        Object result[] = all.toArray();
        for(int x=0;x<result.length;x++){
            System.out.println(result[x]);
        }
    }
}
```

链表是动态对象数组，既然是动态对象数组，返回的内容也应该是一个对象数组。

数组的返回，就需首先开辟一个数组（数组的长度就是count属性内容）







数据的存储和返回是在开发之中链表使用最多的功能。



#### 查询数据



```java
class Link{						// 负责链表的操作
    // 将Node类定义为内部类，表示Node类只被Link调用
    private class Node{ 		// 负责数据与节点关系的匹配
        private Object data;	// 保存节点数据
        private Node next;		//下一个节点
        public Node(Object data){
            this.data = data;
        }
        //第一次调用addNode，this = Link.root
        //第二次调用：this = Link.root.next
        //第三次调用：this = Link.root.next.next
        public void addNode(Node newNode){
            //处理节点关系
            if(this.next == null){ //当前节点下一个为空，表示可以保存
                this.next = newNode;
            }else{ 				//现在当前节点下一个不为空
                this.next.addNode(newNode);
            }
        }
        //第一次调用：this = Link.root
        //第二次调用：this = Link.root.next
        public void toArrayNode(){
            Link.this.reData[Link.this.foot ++] = this.data;
            if(this.next != null){ //现在还有下一个节点
                this.next.toArrayNode();
            }
        }
        
         // 查询某数据是否存在
        //第一次调用：this = Link.root
        //第二次调用：this = Link.root.next
        public boolean containNode(Object search){
            if(search.equals(this.data)){ //找到了 
                return true;
                
            }else{
                if(this.next != null){
                    return this.next.containNode(search);
                }else{ // 没有其他节点
                    return false;
                }    
            }
        }
    }

    //=================以下为Link类=======================//
    // 增加，删除，修改，取出某数据
    private Object[] reData; //返回类型
    private int foot = 0;// 操作的脚标
    private int count = 0; //当前保存的个数
    private Node root; //属于根节点，没有根节点就无法进行数据的保存
    public void add(Object data){
        if(data == null){
            return ; 	//方法结束
        }
        // 如果要进行数据的保存，则必须将数据封装到Node
        // 如果没有封装，则无法确定好节点的前后顺序
        Node newNode = new Node(data);
        if(this.root == null){
            this.root = newNode;
        }else{//根节点存在
            //把此时的节点顺序的处理，交给Node自己处理
            this.root.addNode(newNode);
        }
        this.count ++ ;
    }
    public int size(){
        return this.count;
    }
    //为空判断，与个数是捆绑一起的
    public boolean isEmpty(){
        return this.root == null && this.count == 0;
    }
    
    // 查询某数据是否存在
    public boolean contains(Object search){
        //没有要查询的内容 或者链表为空
        if (search == null || this.root == null){
            return false;
        }
        return this.root.containNode(search);
    }
    // 在link类中定义一个返回类型的属性（数组）
    public Object[] toArray(){
        if(this.count == 0){
            return null;
        }
        //现在链表中存在有数据，则开辟指定长度的数组
        // 该数组一定要交给Node类进行处理。
        this.reData = new Object[this.count];
        this.foot = 0;// 进行清零处理，需要进行脚标操作
        this.root.toArrayNode();//将数据的取出处理交给Node类完成。
        return this.reData;
    }
}
public class LinkArray{
    public static void main(String args[]){
        Link all = new Link();
        // System.out.println(all.size());
        // all.add("A");
        // all.add("B");
        // all.add("C");
        // System.out.println(all.size());
        all.add("A");
        all.add("B");
        all.add("C");
        Object result[] = all.toArray();
        for(int x=0;x<result.length;x++){
            System.out.println(result[x]);
        }
        System.out.println("===================");
        System.out.println(all.contains("A"));
    }
}
```

查看操作要 equals()方法的支持。

如果是一个自定义类，则一定要覆写equals()方法。





#### 根据索引取数据



```java
class Link{						// 负责链表的操作
    // 将Node类定义为内部类，表示Node类只被Link调用
    private class Node{ 		// 负责数据与节点关系的匹配
        private Object data;	// 保存节点数据
        private Node next;		//下一个节点
        public Node(Object data){
            this.data = data;
        }
        //第一次调用addNode，this = Link.root
        //第二次调用：this = Link.root.next
        //第三次调用：this = Link.root.next.next
        public void addNode(Node newNode){
            //处理节点关系
            if(this.next == null){ //当前节点下一个为空，表示可以保存
                this.next = newNode;
            }else{ 				//现在当前节点下一个不为空
                this.next.addNode(newNode);
            }
        }
        //第一次调用：this = Link.root
        //第二次调用：this = Link.root.next
        public void toArrayNode(){
            Link.this.reData[Link.this.foot ++] = this.data;
            if(this.next != null){ //现在还有下一个节点
                this.next.toArrayNode();
            }
        }

        // 查询某数据是否存在
        //第一次调用：this = Link.root
        //第二次调用：this = Link.root.next
        public boolean containNode(Object search){
            if(search.equals(this.data)){ //找到了
                return true;

            }else{
                if(this.next != null){
                    return this.next.containNode(search);
                }else{ // 没有其他节点
                    return false;
                }
            }
        }

        // 按索引查数据
        //第一次调用：this = Link.root
        //第二次调用：this = Link.root.next
        public Object getNode(int index){
            if(Link.this.foot ++ == index){
                return this.data;
            }else{
                this.next.getNode(index);
            }
            return null;
        }

        public void setNode(int index,Object newData){
            if(Link.this.foot ++ == index) {//索引相同
                this.data = newData;
            }else {
                if(this.next!=null){
                    this.next.setNode(index,newData);
                }
            }
        }

    }

    //=================以下为Link类=======================//
    // 增加，删除，修改，取出某数据
    private Object[] reData; //返回类型
    private int foot = 0;// 操作的脚标
    private int count = 0; //当前保存的个数
    private Node root; //属于根节点，没有根节点就无法进行数据的保存
    public void add(Object data){
        if(data == null){
            return ; 	//方法结束
        }
        // 如果要进行数据的保存，则必须将数据封装到Node
        // 如果没有封装，则无法确定好节点的前后顺序
        Node newNode = new Node(data);
        if(this.root == null){
            this.root = newNode;
        }else{//根节点存在
            //把此时的节点顺序的处理，交给Node自己处理
            this.root.addNode(newNode);
        }
        this.count ++ ;
    }
    public int size(){
        return this.count;
    }
    //为空判断，与个数是捆绑一起的
    public boolean isEmpty(){
        return this.root == null && this.count == 0;
    }

    // 查询某数据是否存在
    public boolean contains(Object search){
        //没有要查询的内容 或者链表为空
        if (search == null || this.root == null){
            return false;
        }
        return this.root.containNode(search);
    }
    // 在link类中定义一个返回类型的属性（数组）
    public Object[] toArray(){
        if(this.count == 0){
            return null;
        }
        //现在链表中存在有数据，则开辟指定长度的数组
        // 该数组一定要交给Node类进行处理。
        this.reData = new Object[this.count];
        this.foot = 0;// 进行清零处理，需要进行脚标操作
        this.root.toArrayNode();//将数据的取出处理交给Node类完成。
        return this.reData;
    }

    //
    public Object get(int index){
        if(index>this.count){ //超过个数了
            return null;
        }
        this.foot = 0;
        return this.root.getNode(index);
    }
    //修改指定数据
    public boolean set(int index,Object newData){
        if(index>this.count){ //超过个数了
            return false; // 结束方法调用
        }
        this.foot = 0;// 清零
        this.root.setNode(index,newData);
        return true;
    }

}
public class LinkArray{
    public static void main(String args[]){
        Link all = new Link();
        // System.out.println(all.size());
        // all.add("A");
        // all.add("B");
        // all.add("C");
        // System.out.println(all.size());
        all.add("A");
        all.add("B");
        all.add("C");
        all.set(1,"asdf");
        Object result[] = all.toArray();
        for(int x=0;x<result.length;x++){
            System.out.println(result[x]);
        }
        System.out.println("===================");
        System.out.println(all.contains("A"));

        System.out.println("===================");
        System.out.println(all.get(1));


    }
}
```





#### 数据删除



删除数据分两种情况：

* 是根节点
  * 要在Link里处理
* 不是根节点
  * 让Node处理

需要数据匹配，使用equals

```java
class Link{						// 负责链表的操作
    // 将Node类定义为内部类，表示Node类只被Link调用
    private class Node{ 		// 负责数据与节点关系的匹配
        private Object data;	// 保存节点数据
        private Node next;		//下一个节点
        public Node(Object data){
            this.data = data;
        }
        //第一次调用addNode，this = Link.root
        //第二次调用：this = Link.root.next
        //第三次调用：this = Link.root.next.next
        public void addNode(Node newNode){
            //处理节点关系
            if(this.next == null){ //当前节点下一个为空，表示可以保存
                this.next = newNode;
            }else{ 				//现在当前节点下一个不为空
                this.next.addNode(newNode);
            }
        }
        //第一次调用：this = Link.root
        //第二次调用：this = Link.root.next
        public void toArrayNode(){
            Link.this.reData[Link.this.foot ++] = this.data;
            if(this.next != null){ //现在还有下一个节点
                this.next.toArrayNode();
            }
        }

        // 查询某数据是否存在
        //第一次调用：this = Link.root
        //第二次调用：this = Link.root.next
        public boolean containNode(Object search){
            if(search.equals(this.data)){ //找到了
                return true;

            }else{
                if(this.next != null){
                    return this.next.containNode(search);
                }else{ // 没有其他节点
                    return false;
                }
            }
        }

        // 按索引查数据
        //第一次调用：this = Link.root
        //第二次调用：this = Link.root.next
        public Object getNode(int index){
            if(Link.this.foot ++ == index){
                return this.data;
            }else{
                this.next.getNode(index);
            }
            return null;
        }

        public void setNode(int index,Object newData){
            if(Link.this.foot ++ == index) {//索引相同
                this.data = newData;
            }else {
                if(this.next!=null){
                    this.next.setNode(index,newData);
                }
            }
        }
        
        //第一次调用是：this = Link.root.next,	previouos = Link.root;
        //第二次调用是：this = Link.root.next.next,	previouos = Link.root.next;
        public void removeNode(Node previous,Object data){
            if(this.data.equals(data)){//当前节点为要删除节点
                previous.next = this.next;
            }else{
                this.next.removeNode(this,data);
            }
        }

    }

    //=================以下为Link类=======================//
    // 增加，删除，修改，取出某数据
    private Object[] reData; //返回类型
    private int foot = 0;// 操作的脚标
    private int count = 0; //当前保存的个数
    private Node root; //属于根节点，没有根节点就无法进行数据的保存
    public void add(Object data){
        if(data == null){
            return ; 	//方法结束
        }
        // 如果要进行数据的保存，则必须将数据封装到Node
        // 如果没有封装，则无法确定好节点的前后顺序
        Node newNode = new Node(data);
        if(this.root == null){
            this.root = newNode;
        }else{//根节点存在
            //把此时的节点顺序的处理，交给Node自己处理
            this.root.addNode(newNode);
        }
        this.count ++ ;
    }
    public int size(){
        return this.count;
    }
    //为空判断，与个数是捆绑一起的
    public boolean isEmpty(){
        return this.root == null && this.count == 0;
    }

    // 查询某数据是否存在
    public boolean contains(Object search){
        //没有要查询的内容 或者链表为空
        if (search == null || this.root == null){
            return false;
        }
        return this.root.containNode(search);
    }
    // 在link类中定义一个返回类型的属性（数组）
    public Object[] toArray(){
        if(this.count == 0){
            return null;
        }
        //现在链表中存在有数据，则开辟指定长度的数组
        // 该数组一定要交给Node类进行处理。
        this.reData = new Object[this.count];
        this.foot = 0;// 进行清零处理，需要进行脚标操作
        this.root.toArrayNode();//将数据的取出处理交给Node类完成。
        return this.reData;
    }

    //
    public Object get(int index){
        if(index>this.count){ //超过个数了
            return null;
        }
        this.foot = 0;
        return this.root.getNode(index);
    }
    //修改指定数据
    public boolean set(int index,Object newData){
        if(index>this.count){ //超过个数了
            return false; // 结束方法调用
        }
        this.foot = 0;// 清零
        this.root.setNode(index,newData);
        return true;
    }
    public void remove(Object data){
        if(this.contains(data)){//判断该数据是否存在
            if(this.root.data.equals(data)){//判断是否为root节点的数据
                this.root = this.root.next; //根节点变为下一个节点
            }else{ //不是根节点
                this.root.removeNode(this.root,data);
            }
        }
        this.count --;
    }

}
public class LinkArray{
    public static void main(String args[]){
        Link all = new Link();
        // System.out.println(all.size());
        // all.add("A");
        // all.add("B");
        // all.add("C");
        // System.out.println(all.size());
        all.add("A");
        all.add("B");
        all.add("C");
        all.set(1,"asdf");
        Object result[] = all.toArray();
        for(int x=0;x<result.length;x++){
            System.out.println(result[x]);
        }
        System.out.println("===================");
        System.out.println(all.contains("A"));

        System.out.println("===================");
        System.out.println(all.get(1));


    }
}
```



## 宠物店例子



```java
class Link{
    
}
//宠物的标准
interface Pet{
    public String getName();
    public String getColor();
    public int getAge();
}
//宠物商店 只关心宠物的标准，不关心具体的宠物
class PetShop{
    private Link pets = new Link(); //开辟一个链表，保存多个宠物
    public void add(Pet pet){ //上架的宠物
        this.pets.add(pet); //向链表保存数据
    }
    public void delete(Pet pet){ // 下架
        this.pets.remove(pet);
    }
    public Link getPets(){ // 取得全部宠物
        return this.pets;
    }
    public Link search(String keyword){
        Link res = new Link();
        Object [] data = this.pets.toArray();
        for (int x = 0 ; x< data.length; x++){
            Pet pet = (Pet) data[x];
            if (pet.getName().contains(keyword) || pet.getColor().contains(keyword)){
                res.add(pet);
            }
        }
        return res;
    }
}
// 定义宠物狗
class Dog implements Pet{
    private String name;
    private int age;
    private String color;
    public Dog(String name,int age ,String color){
        this.name = name;
        this.age = age;
        this.color = color;
    }
    //接口方法覆写
    public String getName(){
        return this.name;
    }
    public int getAge(){
        return this.age;
    }
    public String getColor(){
        return this.color;
    }
    // 删除操作，必须覆写equals方法
    public boolean equals(Object obj){
        if(obj == null){
            return false;
        }
        if(this == obj){
            return true;
        }
        if(!(obj instanceof Dog)){
            return false;
        }
        Dog pet = (Dog) obj;
        return this.name.equals(pet.name)  && this.age == pet.age && this.color.equals(pet.color);
    }
    
    public String toString(){ 
        return "[Dog ]name = "+ this.name + ",age = " + this.age+",color = "+ this.color;
    }
}

// 定义宠物猫
class Cat implements Pet{
    private String name;
    private int age;
    private String color;
    public Cat(String name,int age ,String color){
        this.name = name;
        this.age = age;
        this.color = color;
    }
    //接口方法覆写
    public String getName(){
        return this.name;
    }
    public int getAge(){
        return this.age;
    }
    public String getColor(){
        return this.color;
    }
    // 删除操作，必须覆写equals方法
    public boolean equals(Object obj){
        if(obj == null){
            return false;
        }
        if(this == obj){
            return true;
        }
        if(!(obj instanceof Cat)){
            return false;
        }
        Cat pet = (Cat) obj;
        return this.name.equals(pet.name)  && this.age == pet.age && this.color.equals(pet.color);
    }
    
    public String toString(){ 
        return "[Cat ]name = "+ this.name + ",age = " + this.age+",color = "+ this.color;
    }
}



public class Test{
    public static void main(String args[]){
        PetShop ps = new PetShop();
        ps.add(new Dog("black dog",2,"黑色"));
        ps.add(new Dog("golden dog",4,"金色"));
        ps.add(new Dog("white dog",5,"白色"));
        ps.add(new Cat("1 Cat",1,"白色"));
        ps.add(new Cat("2 Cat",2,"黑色"));
        ps.add(new Cat("3 Cat",1,"白色"));
        
        Link all = ps.search("黑");
        Object [] data = all.toArray();
        for(int x = 0; x < data.length; x++){
            System.out.println(data[x]);
        }
        
    }
}
```



## 泛型



在类定义的时候不设置 类中属性或方法参数的具体类型，在使用的时候再定义。





避免向下转型的时候，安全隐患消除了。 尽量不使用向下转型



```java
class Pointers<T> {    // T 是占位符
    public T getY() {
        return y;
    }
    public void setY(T y) {
        this.y = y;
    }
    public T getX() {
        return x;
    }
    public void setX(T x) {
        this.x = x;
    }
    private  T x;
    private  T y;
}

public class fanxing {
    public static void main(String [] args){
        //Pointers<String> p = new Pointers<String>(); // 两种都可以
        Pointers<String> p = new Pointers();          // 在声明实例化的时候 定义数据类型
        p.setX("东经10");
        p.setY("北纬20");
        String x =  p.getX();
        String y =  p.getY();
        System.out.println(x +"-"+ y);
    }
}

```



### 通配符



泛型类型只允许设置类跟接口，而不能使用基本数据类型。





？ 

* ？ extends 类：设置泛型上限（方法声明）
  * ？ extends Number 表示只能设置Number或其子类，
* ？ super 类    ：设置泛型下限（参数上）
  * ？ super String      表示只能设置String或其父类Object



### 泛型接口



### 泛型方法



## 枚举

多例模式的 特点：构造方法私有化，类内部需要提供多个实例化对象，而后，通过static方法返回。

例子：

```java
class Color{
    private static final Color RED = new Color("RED");
    private static final Color GREEN = new Color("GREEN");
    private static final Color BLUE = new Color("BLUE");
    private String title;
    private Color(String title){
        this.title = title;
    }
    public static Color getInstance(int ch){
        switch(ch){
            case 0: return RED;
            case 1: return GREEN;
                case 2: return BLUE;
                default : return null;
        }
    }
    public String toString(){
        return this.title;
    }
}
public class Test{
    public static void main(String args[]){
        System.out.println(Color.getInstance(0));
    }
}
```



基于枚举

```java
enum Color{
    RED,GREEN,BLUE;
}
public class Test{
    public static void main(String args[]){
        System.out.println(Color.RED);
    }
}
```

所谓的枚举，就是高级的多例设计模式。



### Enum类



继承了java.lang.Enum父类

```java
enum Color{
    RED,GREEN,BLUE;
}
public class Test{
    public static void main(String args[]){
        for(Color temp: Color.values()){
            System.out.println(temp.ordinal()+" = "+temp.name());
        }
    }
}
```

解释enum与Enum的区别

enum是关键字，使用enum定义的枚举类，本质上就相当于一个类继承了Enum抽象类。





```java
enum Color{
    RED("红色"),GREEN("绿色"),BLUE("蓝色");//如果定义很多内容，枚举对象必须写在第一行
    private String title;
    private Color (String title){ // 构造方法绝对不能使用public
        //原因 多例设计模式
        this.title = title;
        
    }
    public String toString(){
        return this.title;//覆写Object类的方法
    }
}
public class Test{
    public static void main(String args[]){
        System.out.println(Color.RED);
       // for(Color temp: Color.values()){
       //     System.out.println(temp.ordinal()+" = "+temp.name());
        
        
        
        }
    }
}
```

枚举可以实现接口。

```java
interface IColor{
    public String getColor();
}

enum Color implements IColor{//实现IColor接口
    RED("红色"),GREEN("绿色"),BLUE("蓝色");//如果定义很多内容，枚举对象必须写在第一行
    private String title;
    private Color (String title){ // 构造方法绝对不能使用public
        //原因 多例设计模式
        this.title = title;
        
    }
    public String toString(){
        return this.title;//覆写Object类的方法
    }
    public String getColor(){
        return this.title;
    }
}
public class Test{
    public static void main(String args[]){
        IColor ic = Color.RED;
        System.out.println(ic.getColor());
       // for(Color temp: Color.values()){
       //     System.out.println(temp.ordinal()+" = "+temp.name());
        
        
        
        }
    }
}
```







## Annotation



注解：

主要看3个注解

* @Override   （准确覆写）
* @Deprecated（过期声明）
* @SuppressWarnings（压制警告）



@Override   （准确覆写）

发生在 **继承关系** 中，子类定义了与父类方法名相同，参数类型及个数、返回值类型相同的时候。被覆写的方法不能有比父类更严格的访问权限。



```java
class Person{
    @Override //追加了此注解后将明确的表示该方法是一个覆写的方法,如果覆写错误，则会提示语法错误。
    public String toString(){
        return "asdf";
    }
}
```



@Deprecated（过期声明）

```java
class Person{
    @Deprecated  //表示该方法已经不建议使用，但是使用不会报错。
    public Person(){}
    public Person(String name){}
    public void fun(){}
}
```

平台支持上 出现的过。





@SuppressWarnings（压制警告）

当调用了某些操作可能会产生问题的时候就会出现警告信息，





## 接口定义加强

 



## Lambda 表达式



@FunctionalInterface   //函数式编程接口，只允许有一个方法



```java
(参数)-> 单行语句;




@FunctionalInterface   //函数式编程接口，只允许有一个方法
interface IMessage{
    public void print();
}

public class Test{
    public static void main(String args[]){
        IMessage msg = ()->System.out.println("hello");
        msg.print();
    }
}
```

多行则用{}

```java
IMessage msg = ()->{
    System.out.println("hello");
    System.out.println("world");
    System.out.println("hello");
};
```

如果表达式里是

```java
@FunctionalInterface   //函数式编程接口，只允许有一个方法
interface IMath{
    public int add(int x,int y);
}
public class Test{
    public static void main(String args[]){
        IMath msg = (p1,p2)->p1+p2;
        System.out.println(msg.add(10,20));
    }
}

```



基于java的函数式编程语言 -> Scala



## 方法引用

最开始引用基本上都是针对于引用类型完成的，也就是数组，类，接口。

本质：就是别名。

所以方法引用也是别名的使用。

有四种方法引用形式

* 引用静态方法： 

  ```java
  类名称 :: static 方法名称
  ```

  ```java
  @FunctionalInterface   //函数式编程接口，只允许有一个方法
  interface IUtil<P,R>{
      public R exchange(P p);
  }
  public class Test{
      public static void main(String args[]){
          IUtil<Integer,String> iu = String :: valueOf;   //进行方法的引用
          String str = iu.exchange(1000);//相当于：String.valueOf(1000)  放回值为string
      }
  }
  ```

  就相当于给方法起了别名

  

* 引用某个对象的方法：

  ```java
  实例化对象 :: 普通方法
  ```

  ```java
  @FunctionalInterface   //函数式编程接口，只允许有一个方法
  interface IUtil<R>{
      public R exchange();
  }
  public class Test{
      public static void main(String args[]){
          IUtil<String> iu = "hello"::toUpperCase;   //进行方法的引用
          String str = iu.exchange();//相当于：转换"hello"
          System.out.println(iu.exchange());
      }
  }
  ```

  

* 引用某个特定类的方法：

  ```java
  类名称 :: 普通方法
  ```

  ```java
  @FunctionalInterface   //函数式编程接口，只允许有一个方法
  interface IUtil<P,R>{
      public R compare(P p1,P p2);
  }
  public class Test{
      public static void main(String args[]){
          IUtil<Integer,String> iu = String :: compareTo;   //进行方法的引用
          System.out.println(iu.compare("H","h"));
      }
  }
  ```

  区别是对象操作，类本身操作

* 引用构造方法：

  ```java
  类名称 :: new
  ```

  ```java
  class Person{
      private String name;
      private int age;
      public Person(String name,int age){
          this.name = name;
          this.age = age;
      }
      @Override
      public String toString(){
          return "Person [name="+ name + "，age = "+  age + "]" ;
      }
  }
  @FunctionalInterface   //函数式编程接口，只允许有一个方法
  interface IUtil<R,FP,SP>{
      public R create(FP p1,SP p2);
  }
  public class Test{
      public static void main(String args[]){
          IUtil<Person,String,Integer> iu = Person :: new;   //进行方法的引用
          System.out.println(iu.create("John",20));
      }
  }
  ```

  这些都属于lambda的补充，



## 内建函数式接口



函数式编程在于lambda，函数式接口的核心在于 只有一个方法。

其实只需要四类接口

* 功能性函数式接口

  ```java
  public interface Function<T,R>
  {
  	public R aplly{T t};
  }
  ```

  ```java
  public static void main(String args[]){
      Function<Integer,String> fun = String :: valueOf;
      System.out.println(fun.apply(1000));
  }
  ```

  功能性是指 输入一个数据，而后将数据处理后再进行输出。

  会有扩展的function接口，

* 供给型函数式接口

  ```java
  public interface Supplier <T>
  {
  	public T get();
  }
  ```

  ```java
  public static void main(String args[]){
      Supplier<String> sup = "hello" :: toUpperCase;
      System.out.println(sup.get()); 
  }
  ```

  

* 消费性函数式接口

  ```java
  public interface Consumer <T>
  {
      public void accept(T t);  
  }
  ```

  ```java
  public static void main(String args[]){
      Consumer<String> cons = System.out :: println;
      cons.accept("Hello");  //输出了
  }
  ```

  

* 断言型函数式接口

  ```java
  public interface Predicate<T>{
      public boolean test(T t);
  }
  ```

  ```java
  public static void main(String args[]){
      Predicate<String> pre = "##hello" :: startsWith;
      System.out.println(pre.test("##"));  //输出了
  }
  ```



如果使用复杂的lambda运算，就用这类函数式接口操作。





## 多线程

### 进程 线程

进程：

线程是比进程更小的单位。

很明显，线程启动所花费的时间一定是短的，也就是说，进程要比线程慢。



思考问题：java中的多线程应用体现在哪里呢？



主程序主类->多线程主类

* 继承一个thread类（单继承限制）
* [**推荐**]实现 **runnable** / **callable**接口



启动多线程方法：start();

正确执行：

```java

```

start()方法调用run()方法。

源代码：jdk安装目录下



每个线程对象只能启动一次，如果启动多次就会报错



在**start()**方法里调用了一次**start0( )**方法。**start0( )**是只声明，而未实现的方法，同时使用了**native**关键字定义。**native**指的是调用**本机原生系统函数**。

JVM协调不同系统，移植性高，就是需要调用本机原生系统函数。



### Runnable接口

```java
@FunctionalInterface
public interface Runnable{
    public void run();
}
```



```java
//解决继承类单继承的问题，但是Runnable接口里只有run()方法，没有start()方法，需要Thread类协助，Thread类的构造函数
class MyThread implements Runnable{
    private String title;
    public MyThread(String title){
        this.title = title;
    }
    public void run(){
        for(int x = 0; x< 10;x++){
            System.out.println(this.title + ",x="+x);
        }
    }
}
public class Test{
    public static void main(String args[]){
        MyThread mt1 = new MyThread("线程A");
        MyThread mt2 = new MyThread("线程B");
        MyThread mt3 = new MyThread("线程C");
        mt1.start();
        mt2.start();
        mt3.start();
    }
}
```



```java
//构造方法  public Thread(Runnable target)
//启动多线程

class MyThread implements Runnable{
    private String title;
    public MyThread(String title){
        this.title = title;
    }
    public void run(){
        for(int x = 0; x< 10;x++){
            System.out.println(this.title + ",x="+x);
        }
    }
}
public class Test{
    public static void main(String args[]){
        MyThread mt1 = new MyThread("线程A");
        MyThread mt2 = new MyThread("线程B");
        MyThread mt3 = new MyThread("线程C");
        new Thread(mt1).start();
        new Thread(mt2).start();
        new Thread(mt3).start();
    }
}

// 启动多线程 永远是使用Thread类的start()方法。

```

(**推荐**)匿名内部类

```java
//匿名内部类
public class Test{
    public static void main(String args[]){
        new Thread(new Runnable(){
            
            public void run(){
                System.out.println("Hello world");
            }
        }).start();
    }
}
```

使用lambda表达式

```java
public class Test{
    public static void main(String args[]){
        new Thread(()->System.out.println("hello world")).start();
    }
}
```



### Thread与Runnable的区别



```java
public class Thread extends Object implements Runnable
```



原来Thread类是Runnable接口的子类。

Thread类应该覆写了Runnable接口的run()方法。

```java


private void init(ThreadGroup g,Runnable target,String){
    init(g,target,name,stackSize,null);
}


//------------------------------------
public Thread(Runnable target){
    init(null,target,"Thread-" + nextThreadNum(),0);
}

//------------------------------------
public void run(){
    if(target != null){
        target.run();
    }
}
```





```java

```



Runnable接口

[**代理**]Thread类：资源调度

[**真实**]实现接口的MyThread类：核心业务





多线程处理上，使用的是**代理设计模式**。

还有一个特点：Runnable 可以很好的表述数据共享的概念（并不是说Thread不能）





```java
class MyThread implements Runnable{
    private int ticket = 10;
    public void run(){
        for(int x = 0;x < 20;x++){
            if(this.ticket >0){
                System.out.println("卖票 ticket=" + this.ticket --);
                
            }               
        }
    }
}
public class Test{
    public static void main(String args[]){
        MyThread  mt = 
    }
}
```





## 线程运行状态



执行**start()**方法后，不是立刻执行，而是进入**就绪状态**，等待调度后执行，需要将资源分配给你运行后才可以执行多线程中的代码（**run()中的代码**），当你执行了一段时间后，需要让出资源，让其他线程继续执行。重新进入等待状态，等待分配新资源。





## 通过callable实现多线程



java.util.concurrent   这个开发包主要是进行**高性能编程**。有高并发操作使用的类。

```java
@FunctionalInterface
public interface Callable<V>{
    public V call() ;
}
```

Runnable 中的run()方法没有返回值。遵循了主方法的设计原则：线程开始别回头。

有返回值得用Callable



```java
class MyThread implements Callable<String>{
    public String call(){
        for(int x  =0 ; x<20;x++){
                System.out.println("卖票 x " + x); 
        }
        return "完了";
    }
}
public class Test{
    public static void main(String args[]){
        FutureTask<String> task = new FutureTask<String>(new MyThread());
        new Thread(task).start(); // 启动多线程
        System.out.println(task.get()); 
    }
}
```



## 多线程常用操作方法



* public Thread(Runnable target, String name)
  * 构造方法
  * 创建线程对象的时候设置好名字
* public final void setName()
  * 普通方法
  * 设置线程的名字
* public final String getName()
  * 普通方法
  * 取得线程名字



### 线程对象



如果要取得线程的对象，在Thread类里面提供一个方法：

* 取得当前线程对象：

  * public static Thread currentThread();

  * static 可以直接被类名称调用

  * ```java
    class MyThread implements Runnable{
        public void run(){
            for(int x = 0; x < 10:x++){
                System.out.println(Thread.currentThread().getName() + "，x= " +x);
            }
        }
    }
    public class Test{
        public static void main(String args[]){
            MyThread mt = new MyThread();
            new Thread(mt).start(); //没设置名字
            new Thread(mt).start();//没设置名字
            new Thread(mt,"有名线程").start();//设置名字
        }
    }
    ```

  * 如果没有设置线程名字，则会自动分配一个名字。**注意**如果要设置，请避免重复，中间不要修改。



```java
class MyThread implements Runnable{
    public void run(){
        System.out.println(Thread.currentThread().getName());
    }
}
public class Test{
    public static void main(String args[]){
        MyThread mt = new MyThread();
        mt.run();//直接通过对象调用run()方法  是  main
        new Thread(mt).start(); //没有设置名字，通过线程调用
    }
}


//输出结果
main
Thread-0
```

结论：

主方法就是一个线程，所有的线程都是通过主线程创建并启动的。



## 线程休眠

模拟延迟操作



* 方法：public static void sleep(long millis) throws InterruptedExecption;
  * 休眠时间使用毫秒作为单位



```java
class MyThread implements Runnable{
    public void run(){
        for(int x =0 ;x<20；x++){
            try{
                Thread.sleep(1000);
            }catch(InterruptedExecption e){
                e.printStackTrace();
            }
            System.out.println(Thread.currentThread().getName() + "，x = " + x);
		}
    }
}
public class Test{
    public static void main(String args[]){
        MyThread mt = new MyThread();
        new Thread(mt).start(); //没有设置名字，通过线程调用
        new Thread(mt).start(); //没有设置名字，通过线程调用
        new Thread(mt).start(); //没有设置名字，通过线程调用
        new Thread(mt).start(); //没有设置名字，通过线程调用
    }
}

```

真正进入方法的对象 可能是一个 也可能是多个，所以所有的进入代码的顺序可能有差异，延迟可能有差异，但是总体的执行是并发的。



## 线程的优先级





* 设置 public final void setPriority(int newPriority)
* 取得 public final int getPriority();



优先级设置  可以通过Thread类里的几个常量来设置。

* 最高优先级:
  * public static final int MAX_PRIORITY
  * value :10
* 中等优先级: 
  * public static final int NORM_PRIORITY 
  * value :5
* 最低优先级:
  * public static final int MIN_PRIORITY 
  * value :1



```java
class MyThread implements Runnable{
    public void run(){
        for(int x =0 ;x<20;x++){
             System.out.println(Thread.currentThread().getName() + "，x = " + x);
}
        
    }
}
public class Test{
    public static void main(String args[]){
        MyThread mt = new MyThread();
        Thread t1 = new Thread(mt,"线程A"); //通过线程调用
        Thread t2 = new Thread(mt,"线程B"); //通过线程调用
        Thread t3 = new Thread(mt,"线程C"); //通过线程调用
        t1.start();
        t2.start();
        t3.start();
    }
}

```



设置优先级

```java
class MyThread implements Runnable{
    public void run(){
        for(int x =0 ;x<4;x++){
            System.out.println(Thread.currentThread().getName() + "，x = " + x);
        }

    }
}
public class Test{
    public static void main(String args[]){
        MyThread mt = new MyThread();
        Thread t1 = new Thread(mt,"线程A"); //通过线程调用
        Thread t2 = new Thread(mt,"线程B"); //通过线程调用
        Thread t3 = new Thread(mt,"线程C"); //通过线程调用
        t1.setPriority(Thread.MIN_PRIORITY);
        t2.setPriority(Thread.MAX_PRIORITY);
        t3.setPriority(Thread.MAX_PRIORITY);
        t1.start();
        t2.start();
        t3.start();
    }
}



// 结果
线程A，x = 0
线程B，x = 0
线程B，x = 1
线程A，x = 1
线程B，x = 2
线程B，x = 3
线程C，x = 0
线程C，x = 1
线程C，x = 2
线程C，x = 3
线程A，x = 2
线程A，x = 3
```



主方法的优先级是 中等优先级



且 有可能按着设置的来。



## 同步问题



线程的**同步与死锁**是 多线程里面最重要的问题



核心问题：每一个线程对象操作的延迟问题 （或者轮番抢占资源的问题）



卖票问题

```java
class MyThread implements Runnable{
    private int ticket = 20;
    public void run(){
        for(int x = 0;x<20;x++){
            if(this.ticket > 0){
                try{
                   Thread.sleep(200);  //模拟网络延迟
                }catch(InterruptedException e){
                    e.printStackTrace();
                }
                System.out.println(Thread.currentThread().getName()
                                   +"卖票，ticket = " + this.ticket--);
            }
        }
    }
}
public class Test{
    public static void main(String args[]){
        MyThread mt = new MyThread();
        new Thread(mt,"A");
        new Thread(mt,"B");
        new Thread(mt,"C");
    }
}
```





### 同步处理

所谓同步，就是所有的线程不是一起进入到方法中执行，而是按照**顺序**一个一个进来。



**synchronized** 关键字 处理 同步问题

* 同步代码块

  * 必须设一个要锁定的对象，所以一般锁定当前对象：this

  * 

    ```java
    class MyThread implements Runnable{
        private int ticket = 10;
    
        public void run(){
            for(int x = 0;x<20;x++){
                synchronized(this){
                    if(this.ticket > 0){
                        try{
                            Thread.sleep(100);  //模拟网络延迟
                        }catch(InterruptedException e){
                            e.printStackTrace();
                        }
                        System.out.println(Thread.currentThread().getName()
                                           + "卖票，ticket = " + this.ticket --);
                    }
                }
            }
        }
    }
    public class Test{
        public static void main(String args[]){
            MyThread mt = new MyThread();
            new Thread(mt,"A").start();
            new Thread(mt,"B").start();
            new Thread(mt,"C").start();
        }
    }
    ```

    

* 同步方法

  * 

    ```java
    class MyThread implements Runnable{
        private int ticket = 10;
    
        public void run(){
            for(int x = 0;x<20;x++){
                this.sale();
            }
        }
        public synchronized void sale(){
            if(this.ticket > 0){  // 还有票可卖
                try{
                    Thread.sleep(100);  //模拟网络延迟
                }catch(InterruptedException e){
                    e.printStackTrace();
                }
                System.out.println(Thread.currentThread().getName() 
                                   +"卖票，ticket = " + this.ticket --);
            }
        }
    }
    public class Test{
        public static void main(String args[]){
            MyThread mt = new MyThread();
            new Thread(mt,"A").start();
            new Thread(mt,"B").start();
            new Thread(mt,"C").start();
        }
    }
    ```

    

    同步虽然可以保证数据的完整性（线程安全操作），但是其执行的速度会很慢。

### 死锁





## 生产者与消费者

### 基本模型

生产者和消费者 最经典的供求案例。



生产者负责生产数据，而生产者每生产一个完整的数据之后，消费者就要把这些数据取走。



```java
class Data{ //数据保存
    private String title;
    private String note;

    public String getTitle() {
        return title;
    }

    public void setTitle(String title) {
        this.title = title;
    }

    public String getNote() {
        return note;
    }

    public void setNote(String note) {
        this.note = note;
    }
}

class DataProvider implements Runnable{
    private Data data;
    public DataProvider(Data data){
        this.data = data;
    }
    public void run(){
        for(int x = 0; x<50;x++){
            if(x%2 == 0){
                this.data.setTitle("老李");
                try {
                    Thread.sleep(1000);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
                this.data.setNote("是个好人");
            }else{
                this.data.setTitle("老wang");
                this.data.setNote("是个huai人");
            }
        }
    }
}

class DataConsumer implements Runnable{
    private Data data;
    public DataConsumer(Data data){
        this.data = data;
    }
    public void run(){
        for(int x = 0; x< 50;x++){
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            System.out.println(this.data.getTitle() + " = " + this.data.getNote());
        }
    }
}
public class Test{
    public static void main(String args[]){
        Data data = new Data();
        new Thread(new DataProvider(data)).start();
        new Thread(new DataConsumer(data)).start();
    }
}


//结果

老李 = 是个huai人
老李 = 是个huai人
老李 = 是个huai人
老李 = 是个huai人
老李 = 是个huai人
老李 = 是个huai人
老李 = 是个huai人
老李 = 是个huai人
老李 = 是个huai人
老李 = 是个huai人
老李 = 是个huai人
老李 = 是个huai人
老李 = 是个huai人
老李 = 是个huai人
老李 = 是个huai人
老李 = 是个huai人
老李 = 是个huai人
老李 = 是个huai人
老李 = 是个huai人
老李 = 是个好人
老李 = 是个huai人
老李 = 是个huai人
老李 = 是个huai人
老李 = 是个好人
老wang = 是个huai人
老wang = 是个huai人
老wang = 是个huai人
老wang = 是个huai人
老wang = 是个huai人
老wang = 是个huai人
老wang = 是个huai人
老wang = 是个huai人
老wang = 是个huai人
老wang = 是个huai人
老wang = 是个huai人
老wang = 是个huai人
老wang = 是个huai人
老wang = 是个huai人
老wang = 是个huai人
老wang = 是个huai人
老wang = 是个huai人
老wang = 是个huai人
老wang = 是个huai人
老wang = 是个huai人
老wang = 是个huai人
老wang = 是个huai人
老wang = 是个huai人
老wang = 是个huai人
老wang = 是个huai人
老wang = 是个huai人
```

以上代码出现问题：

* 数据不完整
* 数据重复操作（重复设置，重复取出）



### 解决数据同步问题

使用synchronized关键字解决同步操作方法。

```java
class Data{ //数据保存
    private String title;
    private String note;
    public synchronized void get(){
        try {
            Thread.sleep(1000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println(this.title + ","+ this.note);
    }
    public synchronized void set(String title,String note){
        this.title = title;
        try {
            Thread.sleep(1000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        this.note = note;
    }
    public String getTitle() {
        return title;
    }

    public void setTitle(String title) {
        this.title = title;
    }

    public String getNote() {
        return note;
    }

    public void setNote(String note) {
        this.note = note;
    }
}

class DataProvider implements Runnable{
    private Data data;
    public DataProvider(Data data){
        this.data = data;
    }
    public void run(){
        for(int x = 0; x<50;x++){
            if(x%2 == 0){
                this.data.set("老李","是个好人");
            }else{
                this.data.set("老wang","是个huai人");
            }
        }
    }
}

class DataConsumer implements Runnable{
    private Data data;
    public DataConsumer(Data data){
        this.data = data;
    }
    public void run(){
        for(int x = 0; x< 50;x++){
            this.data.get();
        }
    }
}
public class Test{
    public static void main(String args[]){
        Data data = new Data();
        new Thread(new DataProvider(data)).start();
        new Thread(new DataConsumer(data)).start();
    }
}
```

只解决同步问题，

### 解决重复操作问题



增加等待与唤醒机制  必须参考Object类中提供的方法。



| 方法                                                 | 作用                                                   |
| ---------------------------------------------------- | ------------------------------------------------------ |
| public final void wait() throws InterruptedException | 死等                                                   |
| public final void notify()                           | 唤醒等待第一个线程                                     |
| public final void notifyAll()                        | 唤醒等待全部线程<br />哪个优先级高，哪个有可能优先执行 |





```java
class Data{ //数据保存
    private String title;
    private String note;
    //flag = true 允许生产，但是不允许消费者取走
    //flag = false 表示陈胜完毕，允许消费者取走，但是不能生产
    private boolean flag = false;

    public synchronized void get(){
        if(flag == false){ //已经生产了，不允许重复生产
            try {
                super.wait();
            } catch (InterruptedException e) {
                e.printStackTrace();
            }

        }
        try {
            Thread.sleep(10);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println(this.title + ","+ this.note);
        this.flag = false;//表示已经生产过，不允许再生产
        super.notify();//唤醒等待线程
    }
    public synchronized void set(String title,String note){
        if(this.flag == true){ // 现在不允许取走
            try {
                super.wait();
            } catch (InterruptedException e) {
                e.printStackTrace();
            }

        }
        this.title = title;
        try {
            Thread.sleep(100);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        this.note = note;
        this.flag = true;//继续生产
        super.notify();//唤醒其他
    }
    public String getTitle() {
        return title;
    }

    public void setTitle(String title) {
        this.title = title;
    }

    public String getNote() {
        return note;
    }

    public void setNote(String note) {
        this.note = note;
    }
}

class DataProvider implements Runnable{
    private Data data;
    public DataProvider(Data data){
        this.data = data;
    }
    public void run(){
        for(int x = 0; x<50;x++){
            if(x%2 == 0){
                this.data.set("老李","是个好人");

            }else{
                this.data.set("老wang","是个huai人");

            }
        }
    }
}

class DataConsumer implements Runnable{
    private Data data;
    public DataConsumer(Data data){
        this.data = data;
    }
    public void run(){
        for(int x = 0; x< 50;x++){
            this.data.get();
        }
    }
}
public class Test{
    public static void main(String args[]){
        Data data = new Data();
        new Thread(new DataProvider(data)).start();
        new Thread(new DataConsumer(data)).start();

    }
}
```





问题：解释sleep() 和wait()区别

* sleep()是Thread类中定义的方法， 到了一定的时间后该休眠的线程可以自动唤醒。
* wait()是Object类中定义的方法，如果该想唤醒，必须使用notify()，notifyAll()方法才可以唤醒。



## 线程池

**java.util.concurrent.ExecutorsService**类

* 普通线程池： java.util.concurrent  interface  ExecutorService 
* 调度线程池：java.util.concurrent  interface  ScheduledExecutorService  



**java.util.concurrent.Executors**类

* 创建无大小限制的线程池：public static ExecutorService newCachedThreadPool();
* 创建固定大小的线程池：public static ExecutorService newFixedThreadPool(int nThreads);
* 单线程池：public static ScheduledExecutor newSingleThreadScheduledExecutor();
* 创建定时调度池：public static ScheduledExecutorService newScheduledExecutorPool();



### 线程池实现

创建无限大小的线程池

```java
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

public class Test{
    public static void main(String args[]) throws Exception{
//现在创建一个线程池的模型，但是里面没有线程
        ExecutorService newCachedThreadPool = Executors.newCachedThreadPool();
        for(int x = 0 ;x < 10; x++){
            Thread.sleep(100);
            int index = x; //保存一下x的内容
            newCachedThreadPool.submit(()->System.out.println(Thread.currentThread().getName() + ",x = " +index)); //执行线程的操作
        }
        newCachedThreadPool.shutdown(); //关闭线程池
    }
}

//结果
pool-1-thread-1,x = 0
pool-1-thread-2,x = 1
pool-1-thread-3,x = 2
pool-1-thread-2,x = 5
pool-1-thread-1,x = 6
pool-1-thread-3,x = 4
pool-1-thread-4,x = 3
pool-1-thread-4,x = 8
pool-1-thread-3,x = 9
pool-1-thread-5,x = 7
```

创建单线程线程池

```java
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

public class Test{
    public static void main(String args[]) throws Exception{

        ExecutorService newCachedThreadPool = Executors.newSingleThreadExecutor();
        for(int x = 0 ;x < 10; x++){
            //Thread.sleep(100);
            int index = x;
            newCachedThreadPool.submit(()->System.out.println(Thread.currentThread().getName() + ",x = " +index));
        }
        newCachedThreadPool.shutdown();
    }
}


//结果
pool-1-thread-1,x = 0
pool-1-thread-1,x = 1
pool-1-thread-1,x = 2
pool-1-thread-1,x = 3
pool-1-thread-1,x = 4
pool-1-thread-1,x = 5
pool-1-thread-1,x = 6
pool-1-thread-1,x = 7
pool-1-thread-1,x = 8
pool-1-thread-1,x = 9
```

创建固定大小的线程池

```java
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

public class Test{
    public static void main(String args[]) throws Exception{

        ExecutorService newCachedThreadPool = Executors.newFixedThreadPool(3);  //3个线程池
        for(int x = 0 ;x < 10; x++){
            //Thread.sleep(100);
            int index = x;
            newCachedThreadPool.submit(()->System.out.println(Thread.currentThread().getName() + ",x = " +index));
        }
        newCachedThreadPool.shutdown();
    }
}




//结果

pool-1-thread-1,x = 0
pool-1-thread-2,x = 1
pool-1-thread-3,x = 2
pool-1-thread-3,x = 3
pool-1-thread-1,x = 4
pool-1-thread-2,x = 5
pool-1-thread-1,x = 7
pool-1-thread-3,x = 6
pool-1-thread-1,x = 9
pool-1-thread-2,x = 8
```

定时调度池

```java
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.ScheduledExecutorService;
import java.util.concurrent.TimeUnit;

public class Test{
    public static void main(String args[]) throws Exception{
        //创建一个具备有3个线程大小的定时调度线程池
        ScheduledExecutorService newCachedThreadPool = Executors.newScheduledThreadPool(3);
        for(int x = 0 ;x < 10; x++){
            //Thread.sleep(100);
            int index = x;
            newCachedThreadPool.scheduleAtFixedRate(new Runnable() {
                @Override
                public void run() {
                    System.out.println(Thread.currentThread().getName() + ",x = " +index);
                }
            },3,2, TimeUnit.SECONDS); // 使用的是秒 单位，表示3秒后执行，而后每2秒执行一次。

        }
        newCachedThreadPool.shutdown();
    }
}
```





## StringBuffer类



回顾：String类特点

任何的字符串常量都是String对象，而且String的常量一旦声明，则不可改变，如果改变对象的内容，其实改变的是其引用的指向。

StringBuffer类提供可以修改内容，用append()方法，添加数据。

**String**跟**StringBuffer**的区别：String的内容无法修改，而StringBuffer的内容允许修改。

多还是使用String类。



**String**跟**StringBuffer **两个类都是"CharSequence"接口子类。这个接口描述都是字符集。

String 跟 StringBuffer不能直接转换。

如果要转换，则采用如下规则

* String变为StringBuffer：利用StringBuffer的构造，append()

  * ```java
    String str = "Hello";
    StringBuffer buf = new StringBuffer();
    buf.append(str);
    System.out.println(buf);
    ```

* StringBuffer变为String：

  * ```java
    String str = "Hello";
    StringBuffer buf = new StringBuffer();
    buf.append(str);
    System.out.println(buf.toString());
    ```



**StringBuffer** 特有的特点

* 支持字符串反转： public StringBuffer reverse();

* 删除指定范围的数据：public StringBuffer delete(int start, int end);

* 插入数据：public StringBuffer insert(int offset, 数据类型 b);

  * ```java
    StringBuffer buf = new StringBuffer("HelloWorld");
    System.out.println(buf.delete(5,10).insert(0,"你好").reverse());
    
    //结果
    olleH好你
    ```



面试题：String，StringBuffer，StringBuilder的区别？

* **String不可修改**，StringBuffer，StringBuilder可修改。
* **StringBuffer**采用同步处理，属于线程安全操作，**StringBuilder**采用异步处理，属于线程不安全操作。

优先考虑**String**，StringBuffer和StringBuilder只是作为备选方案。



## Runtime类

runtime类构造方法私有化，因此无法看到，使用了单例设计模式，因此在类内部提供有一个取得对象的方法：

* 取得Runtime类的对象：public static Runtime getRuntime();
  * public long maxMemory();
  * public long totalMemory();
  * public long freeMemory();
  * public void gc(); // 回收垃圾  garbage collector 用于释放无用的内存空间
    * 两种处理形式：1.不定期自动调用 2.使用runtime类中的gc()方法手工调用。



## System类

public static long currentTimeMillis(); 获取当前日期时间的方法。  毫秒



public static void gc(); 也提供一个垃圾收集方法。调用了Runtime类的gc()方法。



一个类对象的创建一定要使用构造方法，，一个对象不再使用，则应该释放，释放的方法。所以要收尾操作，覆写Object类中的finalize()方法。定义如下：

protected void finalize() throws Throwable;

无论在finalize()方法里是否出现异常或者错误，结果不会改变，也不会导致程序出错。



问题：final，finally ，finalize的区别

* final是一个关键字，用于定义不能继承的父类，不能覆写的方法，常量。
* finally 异常处理的统一出口
* finalize是Object类的方法，用于在对象回收。





## 对象克隆

表示一种能力。













