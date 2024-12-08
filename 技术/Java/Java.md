# 一.集合

## 1).List

```java
package demo;
public class Main {
    String name;
    int age;
    public Main(String name, int age) {
        this.name = name;
        this.age = age;
    }
    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
    public int getAge() {
        return age;
    }
    public void setAge(int age) {
        this.age = age;
    }
    public String toString()
    {
        return "Name: " + name + ", Age: " + age;
    }
}


package demo;
import java.util.ArrayList;
import java.util.List;
public class MainTest {
    public static void main(String[] args) {
        //类
        List<Main> list = new ArrayList<>();

        //对象
        Main m1 = new Main("李明",23);
        Main m2 = new Main("张三",18);
        Main m3 = new Main("郑国林",34);
        
        //添加
        list.add(m1);
        list.add(m2);
        list.add(m3);
        
        //替换
        Main xuxiang = new Main("许翔",19);
        list.set(1,xuxiang);
        
        //删除
        list.remove(2);

        //it
        for(Main s:list){
            System.out.println(s.toString());
        }
    }
}
```
## 2).Set
```java
package demo;
public class Main {
    String name;
    int age;
    public Main(String name, int age) {
        this.name = name;
        this.age = age;
    }
    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
    public int getAge() {
        return age;
    }
    public void setAge(int age) {
        this.age = age;
    }
    public String toString()
    {
        return "Name: " + name + ", Age: " + age;
    }
}


package demo;
import java.util.ArrayList;
import java.util.HashSet;
import java.util.List;
public class MainTest {
    public static void main(String[] args) {
        //类
        HashSet<Main> list = new HashSet<Main>();

        //对象
        Main m1 = new Main("李明",23);
        Main m2 = new Main("张三",18);
        Main m3 = new Main("郑国林",34);

        //添加
        list.add(m1);
        list.add(m2);
        list.add(m3);


        //删除
        list.remove(2);

        //it
        for(Main s:list){
            System.out.println(s.toString());
        }
    }
}
```
## 3).Map
```java

```
# 二.反射机制











# 三.泛型















# 四.序列化机制





















# 五.多线程机制





















# 六.网络编程





























七.数据库编程













# 八.设计模式