# -The-forth-java-experimen
# 接口异常处理
## 实验目的
1.掌握Java中抽象类和抽象方法的定义；

2.掌握Java中接口的定义，熟练掌握接口的定义形式以及接口的实现方法；

3.了解异常的使用方法，并在程序中根据输入情况做异常处理；

## 实验要求
1.在 博士研究生类中实现各个接口定义的抽象方法;

2.对年学费和年收入进行统计，用收入减去学费，求得纳税额；

3.国家最新纳税标准（系数），属于某一时期的特定固定值，与实例化对象没有关系，考虑如何用static  final修饰定义。

4.实例化研究生类时，可采用运行时通过main方法的参数args一次性赋值，也可采用Scanner类实现运行时交互式输入。

5.根据输入情况，要在程序中做异常处理。

## 设计思路
首先编写接口，然后对Teacher,Students类实现接口，之后开始编写主方法，实现老师学生的实例化，同时加入异常处理模块，对setfee,getfee等方法进行监控.实现捕捉异常后，改写加入while循环，使出现问题时可以重新输入。最后编写计算税收的静态final方法，在主方法中调用并输出。至此实现所有实验要求。进行测试，检查功能的完整性。
## 核心代码
1.编写接口和接口的实现：

```
package Homework2;
interface StudentManage {
    void setfee(int fee);
    int getfee();
}
public class Student implements StudentManage,TeacherManage{
    String sex; 
    String name;
    int age;
    int spending;
    int salary;
```
2.老师和学生的实例化：

```
Student(String sex,String name,int age){
    	this.age=age;
    	this.name = name;
    	this.sex = sex;
    	System.out.println("ÒÑ¾­µ¼Èë£º"+sex+age+name);
      
Teacher(String sex,String name,int age){
    	this.age=age;
    	this.name = name;
    	this.sex = sex;
    	System.out.println(sex+age+name);
```
3.语句循环和异常扑捉

```
while(i){
			try {
				System.out.println("输入薪水");
				int salary = 0;
				salary= sc.nextInt();
				System.out.println(salary);
				li.setsalary(salary);
				//System.out.println(""+li.getfee());
			}
			catch(ArrayIndexOutOfBoundsException ne) {
				System.out.println("数组越界");
				panduan(li);
			}
			catch(NumberFormatException e) {
				System.out.println(e.getMessage()+"数字格式错误");
				panduan(li);
			}
			catch(Exception m) {
				System.out.println("出现未知错误");
				panduan(li);
			}
			finally {
              i=false;
			}
		}
```
4.计算税收的方法（静态final）

```
public final static void calculator(int salary,int fee) {
		int  year_salary = salary - fee;
		double x = 0;
		if (year_salary <= 36000) {
			x = year_salary * 0.03;
		}
		else if (36000 < year_salary && year_salary <= 144000){
			x = year_salary * 0.1 - 2520; }
		else if (144000 < year_salary && year_salary<= 300000) {
			x = year_salary * 0.2 - 16920;
		}
		else if (300000 < year_salary && year_salary<= 420000) {
			x = year_salary * 0.25 - 31920;
		}
		else if (420000 < year_salary && year_salary<= 660000) {
			x = year_salary * 0.3 - 52920;
		}
		else if (660000 < year_salary && year_salary<= 960000) {
			x = year_salary * 0.35 - 85920;
		}
		else if (960000 < year_salary) {
			x = year_salary * 0.45 - 181920;
		}
		System.out.println("需要缴纳的税款" +x);
```
## 实验结果

```
输入研究生信息
性别，姓名，年龄
男
张三
20
已经导入：男20张三
```

```
输入薪水
60000
60000
输入学费
14000
```

```
缴税信息
需要缴纳的税款：2080.0
```

```
已经导入：女23李红
输入薪水
aaaa
出现未知错误
输入薪水
70000
70000
缴税信息
需要缴纳的税款4480.0
缴税信息
需要缴纳的税款4480.0
```
