# 
Java查缺补漏
整理复习一下Java核心的基础内容。

## 基本数据类型

- byte

8位
有符号的，以二进制补码表示的整数
默认值0

- short

16位
有符号的，以二进制补码表示的整数
默认值0

- int

32位
有符号的，以二进制补码表示的整数
默认值0

- long

64位
有符号的，以二进制补码表示的整数
默认值0L

---


- float

32位单精度浮点型
默认值0.0f

- double 

64位双精度浮点型
默认值0.0d

---


- char

一个单一的 16 位 Unicode 字符；
最小值：\u0000(0)
最大值：\uffff(65535)

- boolean

默认值false;

---


### 自动类型转换
**整型、实型（常量）、字符型数据可以混合运算。运算中，不同类型的数据先转化为同一类型，然后进行运算**
转换从低级到高级
byte->short->char->int->long->float->double

- 转换规则
1. bool类型不能进行类型转换
2. 不能把对象类型转换成不相关类的对象
3. 把容量大的类型转容量小的类型时必须使用强制类型转换
4. 转换过程中可能导致溢出或损失精度
5. 转换前的数据类型位数必须小于转换后的数据类型位数
```java
public static void main(String[] args) {
    char c = 'a';
    byte b = 4;
    int i = 10;
    float f = 2.22f;
    double d = 10.0;
    long ln = 1000;
    short s = 11;
    //byte转short
    short s1 = b;
    System.out.println("byte转short:"+s1);
    //short转char
    char c1 = (char) s;
    System.out.println("short转char:"+c1);
    //char转int
    int i1 = c;
    System.out.println("char转int:"+i1);
    //int转long
    long l1 = i;
    System.out.println("int转long:"+l1);
    //long转float
    float f1 = ln;
    System.out.println("long转float:"+f1);
    //float转double
    double d2 = f;
    System.out.println("float转double:"+d2);
}
```
```java
byte转short:4
short转char:•
char转int:97
int转long:10
long转float:1000.0
float转double:2.2200000286102295
```
### 强制类型转换

- (type) value 其中type是要强制类型转换后的数据类型。
- 条件是转换的数据类型必须是兼容的。
### 隐含强制类型转换

- 整数的默认类型是int
- 浮点型不存在这种情况，因为在定义 float 类型时必须在数字后面跟上 F 或者 f。

---


## Java中的变量
![image.png](https://cdn.nlark.com/yuque/0/2023/png/35164588/1676292321094-0833312e-6e8d-4680-bc49-579dde8ca9a9.png#averageHue=%23fdfafa&clientId=u959a413f-46fb-4&from=paste&id=uc6f2dddb&name=image.png&originHeight=632&originWidth=1419&originalType=url&ratio=1.5&rotation=0&showTitle=false&size=104257&status=done&style=none&taskId=u7d3ddd4d-bcaf-4689-95e3-ec8129a10ad&title=)
## Java 修饰符

---


分类

- 访问修饰符
- 非访问修饰符
### 访问控制修饰符
Java中支持4种，用来保护类、变量、方法和构造方法的访问。

1. **private**:**同一类内可见**，使用对象：变量、方法【**外部类除外**】
2. **protected**:**对同包内的类可见和所有子类可见**。使用对象：变量、方法、同样不能修饰**外部类**。
3. **default**:**同包内可见**，不使用任何修饰符。使用对象：类、**接口、**变量、方法。
4. **public**：对**所有类可见**。使用对象：类、**接口**、变量、方法。

[注]以上列举按照其访问权限范围又小到大
### 默认访问修饰符
使用默认访问修饰符声明的变量和方法，对同一个包内的类是可见的。接口里的变量都隐式声明为 **public static final**,而接口里的方法默认情况下访问权限为 **public**。
### 私有访问修饰符
私有访问修饰符是最严格的访问级别，所以被声明为 **private** 的方法、变量和构造方法只能被所属类访问，并且类和接口不能声明为 **private**。
声明为该类型的变量只能通过类中的get/set方法被外部类访问。
### 公有访问修饰符
被声明为 public 的类、方法、构造方法和接口能够被任何其他类访问。
如果几个相互访问的 public 类分布在不同的包中，则需要导入相应 public 类所在的包。由于类的继承性，类所有的公有方法和变量都能被其子类继承。
### 受保护的访问修饰符
protected 需要从以下两个点来分析说明：

- **子类与基类在同一包中**：被声明为 protected 的变量、方法和构造器能被同一个包中的任何其他类访问；
- **子类与基类不在同一包中**：那么在子类中，子类实例可以访问其从基类继承而来的 protected 方法，而不能访问基类实例的protected方法。

protected 可以修饰数据成员，构造方法，方法成员，**不能修饰类（内部类除外）**
**_### _访问控制和继承**
请注意以下方法继承的规则：

- 父类中声明为 public 的方法在子类中也必须为 public。
- 父类中声明为 protected 的方法在子类中要么声明为 protected，要么声明为 public，不能声明为 private。
- 父类中声明为 private 的方法，不能够被继承。
### 非访问修饰符
**static** 修饰符，用来修饰类方法和类变量。
**final** 修饰符，用来修饰类、方法和变量，final 修饰的类**不能够被继承**，修饰的方法不能被继承类重新定义，修饰的变量为常量，是不可修改的。
**abstract** 修饰符，用来创建抽象类和抽象方法。
**synchronized** 和 **volatile** 修饰符，主要用于线程的编程。

---


## 对象和类
### JVM内存模型
**JVM**在启动时会申请一块内存，它将内存分为若干子区域，用来存放不同形式的数据。
比如可以分为：

- 堆
- 栈
- 方法区

![image.png](https://cdn.nlark.com/yuque/0/2023/png/35164588/1676292321015-3c6a27e3-970b-4399-985c-7a84013f23eb.png#averageHue=%23f6dfbd&clientId=u959a413f-46fb-4&from=paste&id=uafa8aa1c&name=image.png&originHeight=151&originWidth=191&originalType=url&ratio=1.5&rotation=0&showTitle=false&size=3275&status=done&style=none&taskId=ud3c8ae25-c07e-462b-865e-4b2c37df3b8&title=)
当然，这里只是列出了一些常用的基本区域，更多的信息可以参考**JVM**虚拟机相关的知识。

- 堆用来存储引用类型的数据，这些数据相互之间是无序的，并且堆中的数据可以反复使用，产生的垃圾由JVM定期清理。
- 栈以方法为单元存储数据，这样的单元叫方法栈帧，其中存放的数据是有序的，遵循先进后出的规则，方法调用结束后，它占有的方法栈帧将会被立即释放。

即入栈顺序是和方法的调用顺序是一致的，所以一般后调用的方法会先被释放。
#### 对象的创建过程
参考代码
```java
public static void main(String[] args) {
    Car c1 = new Car();
    c1.brand = "路虎";
    c1.color = "黑色";
    c1.maxSpeed=5000;
    c1.run();
}
```
![image.png](https://cdn.nlark.com/yuque/0/2023/png/35164588/1676292321194-369defec-b562-4c6a-a5f8-7089f28c0be8.png#averageHue=%23f9f7f6&clientId=u959a413f-46fb-4&from=paste&id=u8a452249&name=image.png&originHeight=1000&originWidth=1697&originalType=url&ratio=1.5&rotation=0&showTitle=false&size=170339&status=done&style=none&taskId=u8da0f32d-068e-430a-98e8-f9dcfdeca5f&title=)

- 执行**new Car()**,在堆内存中开辟一个空间，地址为**0x0001**。此时由于属性没有作赋值操作，均为各类型的默认值。
- **main**方法会先在栈中创建一块内存空间，**main栈帧**。
- 执行**=**号左边的操作，会在**main栈帧**中创建一块空间,存放变量**c**。
- **c**中存放了执行对象的地址**0x0001**,指向堆中的对象。

执行赋值的操作：
```java
c1.brand = "路虎";
c1.color = "黑色";
c1.maxSpeed=5000;
```

- 通过**c**找到引用的对象中的**brand**、**color**属性。
- 由于二者均为**String**引用类型，所以赋值之后的数据存放在其他地方，而堆中存放的只是这些值的一个引用地址。

执行方法的调用：
 c1.run();
### stastic关键字
修饰的成员是类的成员，该成员属于类，不属于单个对象。**static**可以修饰成员变量、方法、初始化块、内部内，不能修饰构造方法。
#### 类变量

1. 以**static**修饰的成员变量叫类变量(静态变量)
2. 类变量属于类，它随类的信息存储在方法去(1份)，并不随对象存储在堆中。
3. 类变量可以通过类名访问，也可以通过对象名来访问，建议通过类名访问。
#### 类方法

1. 以**static**修饰的方法叫类方法(静态方法)。
2. 类方法属于类，可以通过类名访问，也可以通过对象访问，建议通过类名访问。
#### 静态块

1. 以**static**修饰的初始化块叫静态初始化块；
2. 静态块也属于类，它的加载的时候被隐式的调用一次，之后便会再被调用。
#### 注意
类成员不能访问实例成员，因为可能出现类成员在实例成员还未初始化完之前就已经完成了初始化。
### 内部类
定义在其他类的内部的类叫内部类，而包含了该内部类的类叫外部类。
#### 内部类的作用

1. 内部类提供了一种新的封装方式，可以将内部类隐藏在外部类的内部，便于访问外部类中的成员，如成员内部类可以直接访问外部类的私有成员；
2. 对于哪些仅需要使用一次的类，采用内部类(匿名内部类)实现会更加方便。
#### 内部类的分类
**成员内部类**

- 定义在外部类的内部，与其他成员平级，他是一种新的成员。
- 可以被任意的访问修饰符修饰，一共存在着四种访问级别。
- 被**static**修饰的成员内部类叫做静态内部类，否则叫非静态内部类。

**局部内部类**
在方法内定义的内部类叫做局部内部类，它仅仅在这个方法内部有效(不常用)。
**匿名内部类**
通常在方法调用时，它没有类名，适合创建只需要使用一次的类。
#### 非静态内部类

- 非静态内部类中不可以定义任何静态成员；
- 非静态内部类 可以访问外部类的实例变量；
- 外部类的静态初始化块、静态方法不能访问非静态内部类；
- 同名的变量可以使用**this.**、**外部类.this.**来进行区分；
- 在外部类的外部，也可以实例化非静态内部类：

外部类.内部类 变量名 = 外部类实例.new 内部类构造方法();
```java
package 面向对象.内部类;
/**
* @author: Tisox
* @date: 2022/3/29 9:54
* @description:
* @blog:www.waer.ltd
*/
public class OutFirst {
    private int width = 1024;
    public void print(){
        //外部类中访问非静态内部类
        Inner inner = new Inner(100,50);
        inner.print();
        System.out.println("外部类中访问内部类:"+inner.width);
        System.out.println("外部类访问内部类:"+inner.height);
    }
    /**
* 静态块中不能访问非静态
*/
    public static void show(){
        // Inner inner = new Inner()
    }

    /**
* 非静态内部类
*/
    public class Inner{
        private int width;
        private int height;

        public Inner(int width, int height) {
            this.width = width;
            this.height = height;
        }
        public void print() {
            System.out.println("内部类:"+this.width);
            System.out.println("内部类:"+this.height);
            //在非静态内部类中访问外部类的实例成员
            System.out.println("内部类中访问外部类的成员变量:"+OutFirst.this.width);
        }
        //在非静态内部类中不能定义静态成员 ，当然，静态块、静态方法也都是不允许的
        //public static int i;
    }
}
```
```java
/**
* @author: Tisox
* @date: 2022/3/29 10:04
* @description: 演示在其他类中访问内部类
* @blog:www.waer.ltd
*/
public class InnerDemo {
    public static void main(String[] args) {
        /**
* 在外部访问非静态内部类的方式
* 需要先对内部类所在的外部类进行实例化，
* 再根据这个实例new一个内部类的实例
*/
        OutFirst.Inner fInner = new OutFirst().new Inner(100,233);
        fInner.print();
    }
}
```
#### 静态内部类

- 可以包含静态成员(理所应当)，也可以包含非静态成员(**反过来就不行**)。
- 静态内部类**不能**访问外部类的实例成员，**只能**访问它的静态成员。
- 外部类的所有方法、初始化块都能访问其内部类定义的静态内部类；
- 在外部类的外部，也可以实例化静态内部类：

外部类.内部类 变量名 = new 外部类.内部类构造方法();
```java
package 面向对象.内部类;

/**
* @author: Tisox
* @date: 2022/3/29 10:42
* @description: 外部类，配合演示静态内部类
* @blog:www.waer.ltd
*/
public class OutSecond {
    private int  size=100;
    private static int count=200;

    public void print(){
        System.out.println("外部类中访问内部类:"+Inner.color);
        Inner.show();
        Inner inner = new Inner("test");
        System.out.println(inner.name);
        //访问内部类中的非静态的成员方法
        inner.print();
    }

    public static void show(){
        System.out.println("外部类中访问内部类:"+Inner.color);
        Inner.show();
        Inner inner = new Inner("test");
        System.out.println(inner.name);
        //访问内部类中的非静态的成员方法
        inner.print();
    }

    //静态内部类
    public static class Inner{
        private String name;
        private static String color;

        static {
            color = "RED";
        }

        public Inner(String name) {
            this.name = name;
        }

        public void print() {
            //内部类中的非静态方法中可以访问它的非静态的成员
            System.out.println("内部类Inner:"+this.name);
            //静态内部类中访问外部类的静态成员
            System.out.println("内部类Inner访问外部类静态成员:"+OutSecond.count);
            //静态内部类中不可以访问外部类的非静态成员
            //  System.out.println("内部类Inner访问外部的实例:"+OutSecond.this.size);

        }
        public static void show() {
            System.out.println("内部类:"+color);
            //内部类静态方法中不能访问本类中的非静态有
            //System.out.println("内部类:"+name);
            //在内部类中的静态方法中可以访问外部类中的静态成员
            System.out.println("内部类:"+OutSecond.count);
        }
    }
}
```
在类的外部访问静态内部类
```java
//静态内部类
OutSecond.Inner.show();
//通过实例访问内部类的非静态方法
OutSecond.Inner inner = new OutSecond.Inner("DEMO");
inner.print();
```
#### 匿名内部类

- 匿名内部类**没有名称**，适合创建只需要使用一次的类；
- 创建匿名内部类时，会立刻得到这个类的一个实例；
- 匿名内部类在创建时，必须**继承一个父类或者实现一个接口。**
```java
new 父类构造器(参数列表【如果有的话】){
    ....
    }
```
上面的场景一般使用在抽象类中，且方法体一般是对抽象方法的方法进行实现。接口也是类似的。
```java
new 待实现的接口(){
    ....
}
```
### 枚举类
可以使用枚举类来定义一些有限且固定的数据，比如性别、季节、方向等等。尽管上述的功能也可以通过使用**final**常量来表示，但它有一些不足的地方： 
public static final int SPRING = 1;
类型不安全，可以当作整型参数参与计算，并且输出的意义不够明确！
所以有必要引入一种特殊的类，可以清晰的枚举出每一项数据，可以避免错误的运算，这就是枚举类。
#### 枚举类的规范

- 枚举类是特殊的类，通过**enum**关键字进行定义；
- 枚举类可以定义成员变量、成员方法、构造方法、也可以实现接口；
- 枚举类默认实现于**java.lang.Enum**类，并且不能被继承于其他父类；
- **非抽象**的枚举类默认使用**final**修饰，所以枚举类不能被派生出子类；
- 枚举类的所有实例都必须在类中的第一行显示列出，他们默认是**public static final**的。
#### 使用
**没有构造器的枚举**
```java
public enum Season {
    /**
* 春夏秋冬
*/
    SPRING,SUMMER,FALL,WINTER
}
```
**带有构造器的枚举**
```java
package 面向对象.Enum;

/**
* @author: Tisox
* @date: 2022/3/29 15:34
* @description:
* @blog:www.waer.ltd
*/
public enum Direction {
    /**
* 方向枚举类
*/
    EAST("东"), SOUTH("南"), WEST("西"), NORTH("北");

    private final String name;


    Direction(String name) {
        this.name = name;
    }

    public String getName() {
        return this.name;
    }
}
```
**使用枚举类**
```java
package 面向对象.Enum;

import java.util.concurrent.BrokenBarrierException;

/**
* @author: Tisox
* @date: 2022/3/29 15:18
* @description:
* @blog:www.waer.ltd
*/
@SuppressWarnings({"all"})
    public class EnumDemo {
        public static void main(String[] args) {
            printSeasonWord(Season.SPRING);
            //遍历枚举值
            for (Season value : Season.values()){
                System.out.println(value);
            }
            //调用带构造器的枚举类
            System.out.println(Direction.NORTH.getName());
        }

        public static void printSeasonWord(Season season){
            switch (season){
                case SPRING:
                    System.out.println("春天来了兄弟们");
                    break;
                case  SUMMER:
                    System.out.println("阳光海滩");
                    break;
                case FALL:
                    System.out.println("枫叶飘飘");
                    break;
                case WINTER:
                    System.out.println("白雪皑皑");
                    break;
            }
        }
    }
```
#### 抽象的枚举类

1. 可以在枚举类中定义抽象方法，此时枚举类为抽象类，但不能用**abstract**修饰。
2. 枚举类需要显式的创建枚举值，所以每个枚举值都需要实现抽象方法，否则会编译错误。

**枚举类实现接口**
```
package 面向对象.Enum;

/**
 * @author: Tisox
 * @date: 2022/3/29 15:56
 * @description:
 * @blog:www.waer.ltd
 */

@SuppressWarnings({"all"})
public enum Gender implements Printer{
    /**
     * 性别
     */
    MALE(){
        @Override
        public void print() {
            System.out.println("男");
        }
    },
    FEMALE(){
        @Override
        public void print() {
            System.out.println("女");
        }
    }

    //    @Override
    //    public void print() {
    //        switch (this){
    //            case MALE :
    //                System.out.println("男");
    //                break;
    //            case FEMALE:
    //                System.out.println("女");
    //                break;
    //        }
    //    }
}

interface Printer{
    void print();
}
```
**抽象枚举类**
```
package 面向对象.Enum;

/**
 * @author: Tisox
 * @date: 2022/3/29 16:08
 * @description:
 * @blog:www.waer.ltd
 */
public enum Status {
    /**
     * 抽象枚举类
     */
    ON(){
        @Override
        public void print() {
            System.out.println("打开");
        }
    },
    OFF(){
        @Override
        public void print() {
            System.out.println("关闭");
        }
    };

    public abstract void print();
}
```
### 继承

- 特性
   - 子类拥有父类非 private 的属性、方法。
   - 子类可以拥有自己的属性和方法，即子类可以对父类进行扩展。
   - 子类可以用自己的方式实现父类的方法。
   - Java 的继承是单继承，但是可以多重继承，单继承就是一个子类只能继承一个父类，多重继承就是，例如 A 类继承 B 类，B 类继承 C 类，所以按照关系就是 C 类是 B 类的父类，B 类是 A 类的父类，这是 Java 继承区别于 C++ 继承的一个特性。
   - 提高了类之间的耦合性（继承的缺点，耦合度高就会造成代码之间的联系越紧密，代码独立性越差）。
### 多态

- 优点
   - 消除类型之间的耦合关系
   - 可替换性
   - 可扩充性
   - 接口性
   - 灵活性
   - 简化性
- 必要条件
   - 继承
   - 重写
   - 父类引用指向子类对象
- 实现方式
   - 重写
   - 接口
   - 抽象类和抽象方法
### 接口
### 接口和类的相似点

- 一个接口可以有多个方法。
- 接口文件保存在 .java 结尾的文件中，文件名使用接口名。
- 接口的字节码文件保存在 .class 结尾的文件中。
- 接口相应的字节码文件必须在与包名称相匹配的目录结构中
### 接口和类的区别

- 接口不能用于实例化对象
- 接口没有构造方法
- 接口中所有的方法必须是抽象方法
- 接口不能包含成员变量，除了static和final变量
- 接口不是被类继承了，而是要被类实现
- 接口支持多继承。
### 接口特性

- 接口中每一个方法也是隐式抽象的，接口中的方法会被隐式的指定为 **public abstract**（只能是 public abstract，其他修饰符都会报错）
- 接口中可以含有变量，但是接口中的变量会被隐式的指定为 **public static final** 变量（并且只能是 public，用 private 修饰会报编译错误）。
- 接口中的方法是不能在接口中实现的，只能由实现接口的类来实现接口中的方法。
### 抽象类和接口的区别

- 抽象类中的方法可以有方法体，也就是能实现方法的具体功能，而接口中的方法不行。
- 抽象类中的成员变量可以是各种类型的，而接口中的成员变量只能是 **public static final** 类型的。
- 接口中不能含有静态代码块以及静态方法(用 static 修饰的方法)，而抽象类是可以有静态代码块和静态方法。
- 一个类只能继承一个抽象类，而一个类却可以实现多个接口。

[注]：JDK 1.8 以后，接口里可以有静态方法和方法体了。

---


## 重写和重载

- **重写**

重写是子类对父类中允许访问的方法的实现过程进行重写，**返回值和形参都不能改变**。
重写方法不能抛出新的检查异常或者比被重写方法声明更加**宽泛**的异常。

- **方法重写的一些规则**
   - 参数列表必须与被重写的方法相同
   - 返回类型与被重写方法的返回类型可以不相同，但是必须是父类返回值的派生类
   - 访问权限不能比父类中被重写的方法的访问权限更低【如父类的方法被声明为public，子类重写该方法时就不能声明为protected】
   - 父类的成员方法只能被它的子类重写
   - 声明为final的方法不能被重写。
   - 声明为static的方法不能被重写，但是可以被再次声明。
   - 子类和父类在同一个包中，那么子类可以重写父类所有方法，除了上声明为private和final的方法。
   - 子类和父类不在同一个包中，那么子类只能重写父类声明为public和protected的非final方法。
   - 重写方法能够抛出任何非强制异常，无论被重写的方法是否抛出异常。但是，重写的方法不能抛出新的强制性异常，或者比被重写方法声明的更广泛的强制性异常，反之则可以。
   - 构造方法不能被重写。
   - 如果不能继承一个方法，则不能重写这个方法。
- **重载**重载是在一个类里面，方法名字相同，而参数不同。返回值类型则可以相同也可以不同。每个重载的方法(或者构造函数)都必须有一个独一无二的参数类型列表。
- **重载的一些规则**
   - 被重载二点方法必须改变参数列表(参数个数或类型不一样)。
   - 被重载的方法可以改变返回类型。
   - 被重载的方法可以改变访问修饰符。
   - 被重载的方法可以声明新的或更广的检查异常。
   - 方法能够在同一个类中或者在一个子类中被重载。
   - 无法以返回值类型作为重载函数的区分标准。
- **重写与重载之间的区别**
| 区别点 | 重载方法 | 重写方法 |
| --- | --- | --- |
| 参数列表 | 必须修改 | 一定不能修改 |
| 返回类型 | 可以修改 | 一定不能修改 |
| 异常 | 可以修改 | 可以减少或删除，一定不能抛出新的或者更广的异常 |
| 访问 | 可以修改 | 一定不能做更严格的限制（可以降低限制） |


---


## Java抽象类

- **一些总结**
   - 抽象类不能被实例化，否则会报错。只有抽象类的非抽象子类可以创建对象。
   - 抽象类不一定包含抽象方法，但包含抽象方法的类一定是抽象类。
   - 抽象类中的抽象方法只是声明方法，不做方法体的具体实现。
   - 构造方法、类方法(static修饰的方法)不能声明为抽象方法。
   - 抽象类的子类必须给出抽象方法的具体实现，除非该子类也是抽象类。

---


## Java接口

---


## Java核心API
### Number/Math类
下表是其一些常用的方法。

| 序号 | 方法与描述 |
| --- | --- |
| 1 | [xxxValue()](https://www.nowcoder.com/tutorial/10001/2797087539014dee8396911ac42d8509)
 将 Number 对象转换为xxx数据类型的值并返回。 |
| 2 | [compareTo()](https://www.nowcoder.com/tutorial/10001/f0cd4db757624a009cc67779e88bb167)
 将number对象与参数比较。 |
| 3 | [equals()](https://www.nowcoder.com/tutorial/10001/14c21753fc704165a29c077f0176c8c8)
 判断number对象是否与参数相等。 |
| 4 | [valueOf()](https://www.nowcoder.com/tutorial/10001/478e52f8b47e4337b12c4e3c4db974a6)
 返回一个 Number 对象指定的内置数据类型 |
| 5 | [toString()](https://www.nowcoder.com/tutorial/10001/eb684cd56922470782f6729e48858fc9)
 以字符串形式返回值。 |
| 6 | [parseInt()](https://www.nowcoder.com/tutorial/10001/808aa78e4f884573ac2be32beda0c4d4)
 将字符串解析为int类型。 |
| 7 | [abs()](https://www.nowcoder.com/tutorial/10001/6aa98722694f4e04bc446c817b14df28)
 返回参数的绝对值。 |
| 8 | [ceil()](https://www.nowcoder.com/tutorial/10001/042ed2d8205a4511bea09a43c602bab3)
 返回大于等于( >= )给定参数的的最小整数，类型为双精度浮点型。 |
| 9 | [floor()](https://www.nowcoder.com/tutorial/10001/1223183a330641ca9b2fc9f2e74ba0d9)
 返回小于等于（<=）给定参数的最大整数 。 |
| 10 | [rint()](https://www.nowcoder.com/tutorial/10001/c7c4bba20dd14e998c6c198030c19236)
 返回与参数最接近的整数。返回类型为double。 |
| 11 | [round()](https://www.nowcoder.com/tutorial/10001/5924b7cd539a4307b5577b7cc465e0da)
 它表示**四舍五入**，算法为 **Math.floor(x+0.5)**，即将原来的数字加上 0.5 后再向下取整，所以，Math.round(11.5) 的结果为12，Math.round(-11.5) 的结果为-11。 |
| 12 | [min()](https://www.nowcoder.com/tutorial/10001/bbf430b888fd44e6bd1ce2970e763b91)
 返回两个参数中的最小值。 |
| 13 | [max()](https://www.nowcoder.com/tutorial/10001/c4e4eb809ff948fd8b03430e5dbf02c9)
 返回两个参数中的最大值。 |
| 14 | [exp()](https://www.nowcoder.com/tutorial/10001/fd1516ec0e32422fba59f3d090586420)
 返回自然数底数e的参数次方。 |
| 15 | [log()](https://www.nowcoder.com/tutorial/10001/6b9ece5243d845b0a4bbe21efd464040)
 返回参数的自然数底数的对数值。 |
| 16 | [pow()](https://www.nowcoder.com/tutorial/10001/66937036e21c463b8a7b905fe924d2f5)
 返回第一个参数的第二个参数次方。 |
| 17 | [sqrt()](https://www.nowcoder.com/tutorial/10001/ab096eee26af41a5b55ee74839f079e9)
 求参数的算术平方根。 |
| 18 | [sin()](https://www.nowcoder.com/tutorial/10001/103288d6801a426995f90a7973e55f75)
 求指定double类型参数的正弦值。 |
| 19 | [cos()](https://www.nowcoder.com/tutorial/10001/e069415dd391441989ad689f087eb973)
 求指定double类型参数的余弦值。 |
| 20 | [tan()](https://www.nowcoder.com/tutorial/10001/8a31b2de02494aeba5911331b6e34371)
 求指定double类型参数的正切值。 |
| 21 | [asin()](https://www.nowcoder.com/tutorial/10001/f4d79e1e43fa4eb4b09dbe4688c28b62)
 求指定double类型参数的反正弦值。 |
| 22 | [acos()](https://www.nowcoder.com/tutorial/10001/bb3cd2186fff4347826bb27803af8d83)
 求指定double类型参数的反余弦值。 |
| 23 | [atan()](https://www.nowcoder.com/tutorial/10001/41930f88b9cb4c4aa0075e17b09f03e1)
 求指定double类型参数的反正切值。 |
| 24 | [atan2()](https://www.nowcoder.com/tutorial/10001/3710220a932d4035b9b2c16ec8d3cfa5)
 将笛卡尔坐标转换为极坐标，并返回极坐标的角度值。 |
| 25 | [toDegrees()](https://www.nowcoder.com/tutorial/10001/4fad832ad5aa45269d8964b4d9a6afb2)
 将参数转化为角度。 |
| 26 | [toRadians()](https://www.nowcoder.com/tutorial/10001/cb873023ad35494796a9a21ef09a101a)
 将角度转换为弧度。 |
| 27 | [random()](https://www.nowcoder.com/tutorial/10001/325e1b355e0649e2b40c287a528d0b34)
 返回一个随机数。 |

其中，一下四个方法容易混淆，需要特别理解好。

| 8 | [ceil()](https://www.nowcoder.com/tutorial/10001/042ed2d8205a4511bea09a43c602bab3)
 返回大于等于( >= )给定参数的的最小整数，类型为双精度浮点型。 |
| --- | --- |
| 9 | [floor()](https://www.nowcoder.com/tutorial/10001/1223183a330641ca9b2fc9f2e74ba0d9)
 返回小于等于（<=）给定参数的最大整数 。 |
| 10 | [rint()](https://www.nowcoder.com/tutorial/10001/c7c4bba20dd14e998c6c198030c19236)
 返回与参数最接近的整数。返回类型为double。 |
| 11 | [round()](https://www.nowcoder.com/tutorial/10001/5924b7cd539a4307b5577b7cc465e0da)
 它表示**四舍五入**，算法为 **Math.floor(x+0.5)**，即将原来的数字加上 0.5 后再向下取整，所以，Math.round(11.5) 的结果为12，Math.round(-11.5) 的结果为-11。 |

### Math 的 floor,round 和 ceil 方法实例比较
| 参数 | Math.floor | Math.round | Math.ceil |
| --- | --- | --- | --- |
| 1.4 | 1 | 1 | 2 |
| 1.5 | 1 | 2 | 2 |
| 1.6 | 1 | 2 | 2 |
| -1.4 | -2 | -1 | -1 |
| -1.5 | -2 | -1 | -1 |
| -1.6 | -2 | -2 | -1 |


---


### Java Character 类
char 的包装类型。
常用方法列表

| 序号 | 方法与描述 |
| --- | --- |
| 1 | [isLetter()](https://www.nowcoder.com/tutorial/10001/1ccb60366b4c4d10959c1c0ff2a4a453)
 是否是一个字母 |
| 2 | [isDigit()](https://www.nowcoder.com/tutorial/10001/8e10850c3fdb455c98ab25fc2130467b)
 是否是一个数字字符 |
| 3 | [isWhitespace()](https://www.nowcoder.com/tutorial/10001/e135e36371ee48aeaf4b569ca5060e3d)
 是否是一个空白字符 |
| 4 | [isUpperCase()](https://www.nowcoder.com/tutorial/10001/bee3924c8bdd4f88aeb49bc634693417)
 是否是大写字母 |
| 5 | [isLowerCase()](https://www.nowcoder.com/tutorial/10001/c8122b918e644359bec6225380129976)
 是否是小写字母 |
| 6 | [toUpperCase()](https://www.nowcoder.com/tutorial/10001/c3a92288941e46c3bd5a22e104caf159)
 指定字母的大写形式 |
| 7 | [toLowerCase()](https://www.nowcoder.com/tutorial/10001/8e083e0a61824ea7a1f8e2aef250761f)
 指定字母的小写形式 |
| 8 | [toString()](https://www.nowcoder.com/tutorial/10001/a098f57023914bf093d33ef8d3b2a830)
 返回字符的字符串形式，字符串的长度仅为1 |

完整的列表可以查阅官方的JDK开发手册。
### Java String类
一个非常常用的类。

- **格式化字符串**

String 类的静态方法 format() 能用来创建可复用的格式化字符串，而不仅仅是用于一次打印输出。
这一点在我其他博客【牛客社区开发笔记中有用到】

- **常用方法列表**
| 序号 | 方法描述 |
| --- | --- |
| 1 | [char charAt(int index)](https://www.nowcoder.com/tutorial/10001/57420436c55040b2bae47f61e307bc28)
 返回指定索引处的 char 值。 |
| 2 | [int compareTo(Object o)](https://www.nowcoder.com/tutorial/10001/9f204dbf94a144e49e2a1aea761335d7)
 把这个字符串和另一个对象比较。 |
| 3 | [int compareTo(String anotherString)](https://www.nowcoder.com/tutorial/10001/9f204dbf94a144e49e2a1aea761335d7)
 按字典顺序比较两个字符串。 |
| 4 | [int compareToIgnoreCase(String str)](https://www.nowcoder.com/tutorial/10001/86b49fd9311045bab91d58ec15ff683f)
 按字典顺序比较两个字符串，不考虑大小写。 |
| 5 | [String concat(String str)](https://www.nowcoder.com/tutorial/10001/abb27a6c3f5c425e9988d6646df98675)
 将指定字符串连接到此字符串的结尾。 |
| 6 | [boolean contentEquals(StringBuffer sb)](https://www.nowcoder.com/tutorial/10001/f2301f9c3c0c457e8694dc9baf0b09e2)
 当且仅当字符串与指定的StringBuffer有相同顺序的字符时候返回真。 |
| 7 | [static String copyValueOf(char[]data)](https://www.nowcoder.com/tutorial/10001/68c65730913a47b7be2eda197c193455)
 返回指定数组中表示该字符序列的 String。 |
| 8 | [static String copyValueOf(char[]data, int offset, int count)](https://www.nowcoder.com/tutorial/10001/68c65730913a47b7be2eda197c193455)
 返回指定数组中表示该字符序列的 String。 |
| 9 | [boolean endsWith(String suffix)](https://www.nowcoder.com/tutorial/10001/727ec08e7ef54143be8d61ca13152119)
 测试此字符串是否以指定的后缀结束。 |
| 10 | [boolean equals(Object anObject)](https://www.nowcoder.com/tutorial/10001/416c763de4fa49b6a3b4940f4e6c3727)
 将此字符串与指定的对象比较。 |
| 11 | [boolean equalsIgnoreCase(String anotherString)](https://www.nowcoder.com/tutorial/10001/b6775e64f52d420dba7ecccc515b6d66)
 将此 String 与另一个 String 比较，不考虑大小写。 |
| 12 | [byte[]getBytes()](https://www.nowcoder.com/tutorial/10001/35a74216bb2c4817b59885987244f2e3)
 使用平台的默认字符集将此 String 编码为 byte 序列，并将结果存储到一个新的 byte 数组中。 |
| 13 | [byte[]getBytes(String charsetName)](https://www.nowcoder.com/tutorial/10001/35a74216bb2c4817b59885987244f2e3)
 使用指定的字符集将此 String 编码为 byte 序列，并将结果存储到一个新的 byte 数组中。 |
| 14 | [void getChars(int srcBegin, int srcEnd, char[]dst, int dstBegin)](https://www.nowcoder.com/tutorial/10001/082e32c35f2042bd9daa5006deacf8ea)
 将字符从此字符串复制到目标字符数组。 |
| 15 | [int hashCode()](https://www.nowcoder.com/tutorial/10001/bd6c0aa7f00e4f6fbd3518eaf8d52b71)
 返回此字符串的哈希码。 |
| 16 | [int indexOf(int ch)](https://www.nowcoder.com/tutorial/10001/22c16f81651c41b8aefd9ce815881357)
 返回指定字符在此字符串中第一次出现处的索引。 |
| 17 | [int indexOf(int ch, int fromIndex)](https://www.nowcoder.com/tutorial/10001/22c16f81651c41b8aefd9ce815881357)
 返回在此字符串中第一次出现指定字符处的索引，从指定的索引开始搜索。 |
| 18 | [int indexOf(String str)](https://www.nowcoder.com/tutorial/10001/22c16f81651c41b8aefd9ce815881357)
 返回指定子字符串在此字符串中第一次出现处的索引。 |
| 19 | [int indexOf(String str, int fromIndex)](https://www.nowcoder.com/tutorial/10001/22c16f81651c41b8aefd9ce815881357)
 返回指定子字符串在此字符串中第一次出现处的索引，从指定的索引开始。 |
| 20 | [String intern()](https://www.nowcoder.com/tutorial/10001/5351fc0462964dceb67bea2968f10612)
 返回字符串对象的规范化表示形式。 |
| 21 | [int lastIndexOf(int ch)](https://www.nowcoder.com/tutorial/10001/727e8ca880dc4f2c9475b7120232ba8a)
 返回指定字符在此字符串中最后一次出现处的索引。 |
| 22 | [int lastIndexOf(int ch, int fromIndex)](https://www.nowcoder.com/tutorial/10001/727e8ca880dc4f2c9475b7120232ba8a)
 返回指定字符在此字符串中最后一次出现处的索引，从指定的索引处开始进行反向搜索。 |
| 23 | [int lastIndexOf(String str)](https://www.nowcoder.com/tutorial/10001/727e8ca880dc4f2c9475b7120232ba8a)
 返回指定子字符串在此字符串中最右边出现处的索引。 |
| 24 | [int lastIndexOf(String str, int fromIndex)](https://www.nowcoder.com/tutorial/10001/727e8ca880dc4f2c9475b7120232ba8a)
 返回指定子字符串在此字符串中最后一次出现处的索引，从指定的索引开始反向搜索。 |
| 25 | [int length()](https://www.nowcoder.com/tutorial/10001/df47315427264f6a8125911bde82e62c)
 返回此字符串的长度。 |
| 26 | [boolean matches(String regex)](https://www.nowcoder.com/tutorial/10001/0a6d84ac7b16496da8a19d274c42bb48)
 告知此字符串是否匹配给定的正则表达式。 |
| 27 | [boolean regionMatches(boolean ignoreCase, int toffset, String other, int ooffset, int len)](https://www.nowcoder.com/tutorial/10001/434414e45e8b4174b4cfe7428981c75c)
 测试两个字符串区域是否相等。 |
| 28 | [boolean regionMatches(int toffset, String other, int ooffset, int len)](https://www.nowcoder.com/tutorial/10001/434414e45e8b4174b4cfe7428981c75c)
 测试两个字符串区域是否相等。 |
| 29 | [String replace(char oldChar, char newChar)](https://www.nowcoder.com/tutorial/10001/e685c458cd8941e38ad7e289c36ab13a)
 返回一个新的字符串，它是通过用 newChar 替换此字符串中出现的所有 oldChar 得到的。 |
| 30 | [String replaceAll(String regex, String replacement)](https://www.nowcoder.com/tutorial/10001/d2c4bcab7cee44d9bbb01afff83578d8)
 使用给定的 replacement 替换此字符串所有匹配给定的正则表达式的子字符串。 |
| 31 | [String replaceFirst(String regex, String replacement)](https://www.nowcoder.com/tutorial/10001/3d5d53674c6e440485539f7ef9aa48e2)
 使用给定的 replacement 替换此字符串匹配给定的正则表达式的第一个子字符串。 |
| 32 | [String[]split(String regex)](https://www.nowcoder.com/tutorial/10001/84aa81e9342b43c29787cd6bea756b8e)
 根据给定正则表达式的匹配拆分此字符串。 |
| 33 | [String[]split(String regex, int limit)](https://www.nowcoder.com/tutorial/10001/84aa81e9342b43c29787cd6bea756b8e)
 根据匹配给定的正则表达式来拆分此字符串。 |
| 34 | [boolean startsWith(String prefix)](https://www.nowcoder.com/tutorial/10001/9136e0b21b264725949734623c59cf9d)
 测试此字符串是否以指定的前缀开始。 |
| 35 | [boolean startsWith(String prefix, int toffset)](https://www.nowcoder.com/tutorial/10001/9136e0b21b264725949734623c59cf9d)
 测试此字符串从指定索引开始的子字符串是否以指定前缀开始。 |
| 36 | [CharSequence subSequence(int beginIndex, int endIndex)](https://www.nowcoder.com/tutorial/10001/0a5d73cbeec84057a81d3dc2457cad2a)
 返回一个新的字符序列，它是此序列的一个子序列。 |
| 37 | [String substring(int beginIndex)](https://www.nowcoder.com/tutorial/10001/eb8b6ed9247e4255b5945a4d0fd1dda8)
 返回一个新的字符串，它是此字符串的一个子字符串。 |
| 38 | [String substring(int beginIndex, int endIndex)](https://www.nowcoder.com/tutorial/10001/eb8b6ed9247e4255b5945a4d0fd1dda8)
 返回一个新字符串，它是此字符串的一个子字符串。 |
| 39 | [char[]toCharArray()](https://www.nowcoder.com/tutorial/10001/5db0efd2e8704988ab7610e5e4d4e314)
 将此字符串转换为一个新的字符数组。 |
| 40 | [String toLowerCase()](https://www.nowcoder.com/tutorial/10001/954a2d3e8049414286bf16f4583decdd)
 使用默认语言环境的规则将此 String 中的所有字符都转换为小写。 |
| 41 | [String toLowerCase(Locale locale)](https://www.nowcoder.com/tutorial/10001/954a2d3e8049414286bf16f4583decdd)
 使用给定 Locale 的规则将此 String 中的所有字符都转换为小写。 |
| 42 | [String toString()](https://www.nowcoder.com/tutorial/10001/806cd8280f124065a54d262ed4b04468)
 返回此对象本身（它已经是一个字符串！）。 |
| 43 | [String toUpperCase()](https://www.nowcoder.com/tutorial/10001/335b543bb6e547cb8c20eb670cf6aedc)
 使用默认语言环境的规则将此 String 中的所有字符都转换为大写。 |
| 44 | [String toUpperCase(Locale locale)](https://www.nowcoder.com/tutorial/10001/335b543bb6e547cb8c20eb670cf6aedc)
 使用给定 Locale 的规则将此 String 中的所有字符都转换为大写。 |
| 45 | [String trim()](https://www.nowcoder.com/tutorial/10001/46b58aa6dab648aca6d14291e4f3c761)
 返回字符串的副本，忽略前导空白和尾部空白。 |
| 46 | [static String valueOf(primitive data type x)](https://www.nowcoder.com/tutorial/10001/344e1dc1dbe2430f8626efb75a3db807)
 返回给定data type类型x参数的字符串表示形式。 |

### StringBuffer类
## StringBuffer 方法
以下是 StringBuffer 类支持的主要方法：

| 序号 | 方法描述 |
| --- | --- |
| 1 | public StringBuffer append(String s) 将指定的字符串追加到此字符序列。 |
| 2 | public StringBuffer reverse() 将此字符序列用其反转形式取代。 |
| 3 | public delete(int start, int end) 移除此序列的子字符串中的字符。 |
| 4 | public insert(int offset, int i) 将 **int** 参数的字符串表示形式插入此序列中。 |
| 5 | replace(int start, int end, String str) 使用给定 **String** 中的字符替换此序列的子字符串中的字符。 |

下面的列表里的方法和 String 类的方法类似：

| 序号 | 方法描述 |
| --- | --- |
| 1 | int capacity() 返回当前容量。 |
| 2 | char charAt(int index) 返回此序列中指定索引处的 **char** 值。 |
| 3 | void ensureCapacity(int minimumCapacity) 确保容量至少等于指定的最小值。 |
| 4 | void getChars(int srcBegin, int srcEnd, char[] dst, int dstBegin) 将字符从此序列复制到目标字符数组 **dst**。 |
| 5 | int indexOf(String str) 返回第一次出现的指定子字符串在该字符串中的索引。 |
| 6 | int indexOf(String str, int fromIndex) 从指定的索引处开始，返回第一次出现的指定子字符串在该字符串中的索引。 |
| 7 | int lastIndexOf(String str) 返回最右边出现的指定子字符串在此字符串中的索引。 |
| 8 | int lastIndexOf(String str, int fromIndex) 返回 String 对象中子字符串最后出现的位置。 |
| 9 | int length() 返回长度（字符数）。 |
| 10 | void setCharAt(int index, char ch) 将给定索引处的字符设置为 **ch**。 |
| 11 | void setLength(int newLength) 设置字符序列的长度。 |
| 12 | CharSequence subSequence(int start, int end) 返回一个新的字符序列，该字符序列是此序列的子序列。 |
| 13 | String substring(int start) 返回一个新的 **String**，它包含此字符序列当前所包含的字符子序列。 |
| 14 | String substring(int start, int end) 返回一个新的 **String**，它包含此序列当前所包含的字符子序列。 |
| 15 | String toString() 返回此序列中数据的字符串表示形式。 |

### Java正则表达式

- **正则表达式语法**

在其他语言中，**\** 表示：**我想要在正则表达式中插入一个普通的（字面上的）反斜杠，请不要给它任何特殊的意义。**
在 Java 中，**\** 表示：**我要插入一个正则表达式的反斜线，所以其后的字符具有特殊的意义。**
所以，在其他的语言中（如Perl），一个反斜杠 **** 就足以具有转义的作用，而在 Java 中正则表达式中则需要有两个反斜杠才能被解析为其他语言中的转义作用。也可以简单的理解在 Java 的正则表达式中，两个 **\_* 代表其他语言中的一个 ***_，这也就是为什么表示一位数字的正则表达式是 **\d**，而表示一个普通的反斜杠是 **\\**。

| 字符 | 说明 |
| --- | --- |
| \\ | 将下一字符标记为特殊字符、文本、反向引用或八进制转义符。例如，"n"匹配字符"n"。"\\n"匹配换行符。序列"\\"匹配""，"("匹配"("。 |
| ^ | 匹配输入字符串开始的位置。如果设置了 **RegExp** 对象的 **Multiline** 属性，^ 还会与"\\n"或"\\r"之后的位置匹配。 |
| $ | 匹配输入字符串结尾的位置。如果设置了 **RegExp** 对象的 **Multiline** 属性，$ 还会与"\\n"或"\\r"之前的位置匹配。 |
| * | 零次或多次匹配前面的字符或子表达式。例如，zo* 匹配"z"和"zoo"。* 等效于 {0,}。 |
| + | 一次或多次匹配前面的字符或子表达式。例如，"zo+"与"zo"和"zoo"匹配，但与"z"不匹配。+ 等效于 {1,}。 |
| ? | 零次或一次匹配前面的字符或子表达式。例如，"do(es)?"匹配"do"或"does"中的"do"。? 等效于 {0,1}。 |
| {_n_} | _n_ 是非负整数。正好匹配 _n_ 次。例如，"o{2}"与"Bob"中的"o"不匹配，但与"food"中的两个"o"匹配。 |
| {_n_,} | _n_ 是非负整数。至少匹配 _n_ 次。例如，"o{2,}"不匹配"Bob"中的"o"，而匹配"foooood"中的所有 o。"o{1,}"等效于"o+"。"o{0,}"等效于"o*"。 |
| {_n_,_m_} | _m_ 和 _n_ 是非负整数，其中 _n_ <= _m_。匹配至少 _n_ 次，至多 _m_ 次。例如，"o{1,3}"匹配"fooooood"中的头三个 o。'o{0,1}' 等效于 'o?'。注意：您不能将空格插入逗号和数字之间。 |
| ? | 当此字符紧随任何其他限定符（_、+、?、{*n_}、{_n_,}、{_n_,_m_}）之后时，匹配模式是"非贪心的"。"非贪心的"模式匹配搜索到的、尽可能短的字符串，而默认的"贪心的"模式匹配搜索到的、尽可能长的字符串。例如，在字符串"oooo"中，"o+?"只匹配单个"o"，而"o+"匹配所有"o"。 |
| . | 匹配除"\\r\\n"之外的任何单个字符。若要匹配包括"\\r\\n"在内的任意字符，请使用诸如"[\\s\\S]"之类的模式。 |
| (_pattern_) | 匹配 _pattern_ 并捕获该匹配的子表达式。可以使用 ![](https://cdn.nlark.com/yuque/0/2023/svg/35164588/1676292311669-eb81ae38-5726-45a7-a8c3-906901336575.svg#clientId=u959a413f-46fb-4&from=paste&id=u3b7686cd&originHeight=20&originWidth=38&originalType=url&ratio=1.5&rotation=0&showTitle=false&status=done&style=none&taskId=u6e7a8619-c457-476e-b95d-ef080049352&title=)**9** 属性从结果"匹配"集合中检索捕获的匹配。若要匹配括号字符 ( )，请使用"("或者")"。 |
| (?:_pattern_) | 匹配 _pattern_ 但不捕获该匹配的子表达式，即它是一个非捕获匹配，不存储供以后使用的匹配。这对于用"or"字符 (&#124;) 组合模式部件的情况很有用。例如，'industr(?:y&#124;ies) 是比 'industry&#124;industries' 更经济的表达式。 |
| (?=_pattern_) | 执行正向预测先行搜索的子表达式，该表达式匹配处于匹配 _pattern_ 的字符串的起始点的字符串。它是一个非捕获匹配，即不能捕获供以后使用的匹配。例如，'Windows (?=95&#124;98&#124;NT&#124;2000)' 匹配"Windows 2000"中的"Windows"，但不匹配"Windows 3.1"中的"Windows"。预测先行不占用字符，即发生匹配后，下一匹配的搜索紧随上一匹配之后，而不是在组成预测先行的字符后。 |
| (?!_pattern_) | 执行反向预测先行搜索的子表达式，该表达式匹配不处于匹配 _pattern_ 的字符串的起始点的搜索字符串。它是一个非捕获匹配，即不能捕获供以后使用的匹配。例如，'Windows (?!95&#124;98&#124;NT&#124;2000)' 匹配"Windows 3.1"中的 "Windows"，但不匹配"Windows 2000"中的"Windows"。预测先行不占用字符，即发生匹配后，下一匹配的搜索紧随上一匹配之后，而不是在组成预测先行的字符后。 |
| _x_&#124;_y_ | 匹配 _x_ 或 _y_。例如，'z&#124;food' 匹配"z"或"food"。'(z&#124;f)ood' 匹配"zood"或"food"。 |
| [_xyz_] | 字符集。匹配包含的任一字符。例如，"[abc]"匹配"plain"中的"a"。 |
| [^_xyz_] | 反向字符集。匹配未包含的任何字符。例如，"abc"匹配"plain"中"p"，"l"，"i"，"n"。 |
| [_a-z_] | 字符范围。匹配指定范围内的任何字符。例如，"[a-z]"匹配"a"到"z"范围内的任何小写字母。 |
| [^_a-z_] | 反向范围字符。匹配不在指定的范围内的任何字符。例如，"a-z"匹配任何不在"a"到"z"范围内的任何字符。 |
| \\b | 匹配一个字边界，即字与空格间的位置。例如，"er\\b"匹配"never"中的"er"，但不匹配"verb"中的"er"。 |
| \\B | 非字边界匹配。"er\\B"匹配"verb"中的"er"，但不匹配"never"中的"er"。 |
| \\c_x_ | 匹配 _x_ 指示的控制字符。例如，\\cM 匹配 Control-M 或回车符。_x_ 的值必须在 A-Z 或 a-z 之间。如果不是这样，则假定 c 就是"c"字符本身。 |
| \\d | 数字字符匹配。等效于 [0-9]。 |
| \\D | 非数字字符匹配。等效于 0-9。 |
| \\f | 换页符匹配。等效于 \\x0c 和 \\cL。 |
| \\n | 换行符匹配。等效于 \\x0a 和 \\cJ。 |
| \\r | 匹配一个回车符。等效于 \\x0d 和 \\cM。 |
| \\s | 匹配任何空白字符，包括空格、制表符、换页符等。与 [ \\f\\n\\r\\t\\v] 等效。 |
| \\S | 匹配任何非空白字符。与  \\f\\n\\r\\t\\v 等效。 |
| \\t | 制表符匹配。与 \\x09 和 \\cI 等效。 |
| \\v | 垂直制表符匹配。与 \\x0b 和 \\cK 等效。 |
| \\w | 匹配任何字类字符，包括下划线。与"[A-Za-z0-9_]"等效。 |
| \\W | 与任何非单词字符匹配。与"A-Za-z0-9_"等效。 |
| \\x_n_ | 匹配 _n_，此处的 _n_ 是一个十六进制转义码。十六进制转义码必须正好是两位数长。例如，"\\x41"匹配"A"。"\\x041"与"\\x04"&"1"等效。允许在正则表达式中使用 ASCII 代码。 |
| _num_ | 匹配 _num*，此处的 *num_ 是一个正整数。到捕获匹配的反向引用。例如，"(.)\\1"匹配两个连续的相同字符。 |
| _n_ | 标识一个八进制转义码或反向引用。如果 _n_ 前面至少有 _n_ 个捕获子表达式，那么 _n_ 是反向引用。否则，如果 _n_ 是八进制数 (0-7)，那么 _n_ 是八进制转义码。 |
| _nm_ | 标识一个八进制转义码或反向引用。如果 _nm_ 前面至少有 _nm_ 个捕获子表达式，那么 _nm_ 是反向引用。如果 _nm_ 前面至少有 _n_ 个捕获，则 _n_ 是反向引用，后面跟有字符 _m_。如果两种前面的情况都不存在，则 _nm_ 匹配八进制值 _nm*，其中 *n_ 和 _m_ 是八进制数字 (0-7)。 |
| \\nml | 当 _n_ 是八进制数 (0-3)，_m_ 和 _l_ 是八进制数 (0-7) 时，匹配八进制转义码 _nml_。 |
| \\u_n_ | 匹配 _n_，其中 _n_ 是以四位十六进制数表示的 Unicode 字符。例如，\\u00A9 匹配版权符号 (©)。 |

_根据 Java Language Specification 的要求，Java 源代码的字符串中的反斜线被解释为 Unicode 转义或其他字符转义。因此必须在字符串字面值中使用两个反斜线，表示正则表达式受到保护，不被 Java 字节码编译器解释。例如，当解释为正则表达式时，字符串字面值 "\b" 与单个退格字符匹配，而 "\b" 与单词边界匹配。字符串字面值 "(hello)" 是非法的，将导致编译时错误；要与字符串 (hello) 匹配，必须使用字符串字面值 "\(hello\)"。_
## File
Java.io包下的类。
不能访问文件内容。
### 常用方法
File类中一些常用的操作。

- 创建文件
```
file = new File("E:/Javas/demoFile/1.txt");
file.createNewFile();
```

- 删除文件

file.delete()

- 改名

file.renameTo(new File("E:/Javas/demoFile/2.txt"));

- 一些判断操作
```
System.out.println("是否存在："+file.exists());
System.out.println("是否文件："+file.isFile());
System.out.println("是否可读："+file.canRead());
System.out.println("是否可写："+file.canWrite());
System.out.println("绝对路径："+file.isAbsolute());
```
查看File的实现源码可知，上述几个方法的返回值都是bool类型。

- 一些访问方法

对文件一些属性的访问方法
```
System.out.println("文件名称："+file.getName());
System.out.println("文件路径："+file.getPath());
System.out.println("绝对路径："+file.getAbsolutePath());
System.out.println("上级目录："+file.getParent());
System.out.println("文件长度："+file.length());
System.out.println("最后修改时间："+new SimpleDateFormat("yyyy-MM-dd HH:mm:ss").format(file.lastModified()));
```
对于目录操作，上述大部分的方法也是适用的，自查Java的手册即可，具体不再一一赘述。其中，创建目录的方法为：
```
file = new File("E:/Javas/demoFile/a");
 //创建目录
 file.mkdirs();
```

- 列举目录下的所有文件

System.out.println(Arrays.toString(file.listFiles()));

- 列举上级目录所有内容

 System.out.println(Arrays.toString(file.getParentFile().listFiles()));
listFiles()方法的返回值为数组。

---


### 过滤文件
**File**类的**listFiles()**方法可以接受一个参数，用于在列举文件时对其进行过滤，该参数为一个**接口**。
先看一下过滤器的两个接口：

- FileFilter()

![image.png](https://cdn.nlark.com/yuque/0/2023/png/35164588/1676292321210-b5ff675d-6ca0-41cf-a73a-7cc439da8351.png#averageHue=%23232933&clientId=u959a413f-46fb-4&from=paste&id=u4427f944&name=image.png&originHeight=485&originWidth=824&originalType=url&ratio=1.5&rotation=0&showTitle=false&size=209323&status=done&style=none&taskId=uacd481b8-0a0b-41e5-b790-e548988cd14&title=)
可以看到，接口中就定义了一个accept方法，用于过滤实现。方法接受一个File类型的文件。

- FilenameFilter()

![image.png](https://cdn.nlark.com/yuque/0/2023/png/35164588/1676292322056-e337a2eb-3722-4e42-ac4a-a2bb5040b0be.png#averageHue=%23252b36&clientId=u959a413f-46fb-4&from=paste&id=u1aaadbf4&name=image.png&originHeight=529&originWidth=1019&originalType=url&ratio=1.5&rotation=0&showTitle=false&size=629063&status=done&style=none&taskId=uddbb8b81-9581-4359-a1be-c09fe51339b&title=)
这个方法和上面的差不多，主要在于参数的区别，方法接受一个目录（既是我觉的一个上级目录），一个字符串类型的文件名（可以是一个文件名，也可以是文件夹名称）作为过滤方法的两个参数。
**简单使用**
为了方便演示，就不再对接口进行单独的实现，均以匿名实现的方式进行演示。

- FileFilter()的使用
```
files = dir.listFiles(new FileFilter() {
  @Override
  public boolean accept(File pathname) {
                if(pathname.getName().endsWith(".txt")){
                    return true;
                }
                return false;
            }
        });
```
过滤所有后缀名为非.txt的文件。

- FilenameFilter()的使用
```
files = dir.listFiles(new FilenameFilter() {
   @Override
   public boolean accept(File dir, String name) {
                if(name.endsWith(".java")){
                    return true;
                }
                return false;
            }
        });
```
过滤所有后缀为非.java的文件。

---


### 综合小案例

- 需求概述

请实现一个方法，方法传入一个目录，将该路径下的所有文件/文件夹进行指定的层次关系进行缩进格式展示(包含子目录)。

- 测试用例
```
javas
  .idea
     + .gitignore
     + .name
    inspectionProfiles
       + Project_Default.xml
     + misc.xml
     + modules.xml
     + workspace.xml
   + abc.txt
  demoFile
     + 1.txt
     + 2.txt
    a
     + Demo1.java
   + JavaBases.iml
  out
    production
      JavaBases
        File
           + Demo1.class
           + Demo2$1.class
           + Demo2$2.class
           + Demo2.class
           + Demo3.class
  src
    File
       + Demo1.java
       + Demo2.java
       + Demo3.java
```
如果目录里面有文件，需要在文件名之前加上“+”符，对于每一级目录，根据目录级数在前面添加两个空格作为缩进，以上规则对子目录适用。

- 需求实现

主要考察File类的基本使用和对递归思想的理解。详情见代码。
```
public static void printFile(String filePath,int depth){
        File file =  new File(filePath);
        if(!file.exists()){
            throw new IllegalArgumentException("文件不存在！");
        }
        //打印缩进
        for(int i=0;i<depth; i++){
            System.out.print("  ");
        }
        //打印名字
        if(file.isFile()){
            System.out.print(" + ");
        }
        System.out.println(file.getName());
        //对目录递归
        if(file.isDirectory()){
            File[] files = file.listFiles();
            for (File f : files) {
                printFile(f.getPath(),depth+1);
            }
        }
    }
```

---


## IO流
IO即**Input Output**，用于实现对数据的输入输出操作。
Java将不同的输入输出源(键盘、文件、网络等)抽象表述为流(Stream)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/35164588/1676292327979-85bc7a7b-3301-4a98-924e-c7208e226e1c.png#averageHue=%23111311&clientId=u959a413f-46fb-4&from=paste&id=u697995a4&name=image.png&originHeight=1500&originWidth=1000&originalType=url&ratio=1.5&rotation=0&showTitle=false&size=1379617&status=done&style=none&taskId=ue6a5bb46-933b-4a4c-a9f3-53242957397&title=)
### 流的分类
按照流的【方向】、【数据】、【功能】可以分为三类。

- 输入输出流
   - 输入流只能读取数据
   - 输出流只能写入数据
- 字节流和字符流
   - 字节流操作的数据单元为8个字节
   - 字符流操作的数据单元为16个字符
- 节点流和处理流
   - 节点流可以直接从或者向一个特定的IO设备读/写数据，也称为低级流
   - 处理流是对节点流的连接或封装，用于简化数据读/写功能、提高效率，也称为高级流
### 流的模型
![image.png](https://cdn.nlark.com/yuque/0/2023/png/35164588/1676292328131-a8794b8c-b56b-4fbb-ab8c-8c53a628b118.png#averageHue=%23e7e5e4&clientId=u959a413f-46fb-4&from=paste&id=u902fabb6&name=image.png&originHeight=703&originWidth=1425&originalType=url&ratio=1.5&rotation=0&showTitle=false&size=155020&status=done&style=none&taskId=uccbe014b-8762-4a57-a4e7-7f96d9df522&title=)
### 输入流
#### FileInputStream
| 方法 | 方法描述 |
| --- | --- |
| int read() | 读取下一个字节 |
| int read(byte[] b) | 读取下一批字节，将其存入数组，返回读取的字节数 |
| int read(btye[] b,int off,int len) | 从off开始最多读取len个字节，将其存入数组，返回读取的字节数 |

#### Reader
| 方法 | 方法描述 |
| --- | --- |
| int read() | 读取下一个字符 |
| int read(char[] c) | 读取下一批字符，将其存入数组，返回读取的字符数 |
| int read(char[] c,int off,int len) | 从off开始最多读取len个字符，将其存入数组，返回读取的字符数 |

### 输出流
#### OutputStream
| 方法 | 方法描述 |
| --- | --- |
| void write(int b) | 输出指定的字节 |
| void write(byte[] b) | 输出指定的字节数组 |
| void write(byte[] b,int off,int len) | 输出指定的字节数组，从off开始最多输出len个字节 |

#### Writer
| 方法 | 方法描述 |
| --- | --- |
| void write(int c) | 输出指定的字符 |
| void write(char[] c) | 输出指定的字符数组 |
| void write(char[] c,int off,int len) | 输出指定的字符数组，从off开始最多输出len个字符 |
| void write(String str) | 输出指定的字符串 |
| void write(String str,int off,int len) | 输出指定的字符串，从off开始最多输出len个字符 |

【注意】：

- 上述四个都是抽象类，不能直接实例化。
- 都定义了**close()**方法，需要在使用之后调用该方法将其关闭。
- 无论是否发生异常，使用后都要尝试关闭它，因此通常在finally中关闭流。
- 都实现了**Closeable**接口，可以在try()中创建流，以便于自动关闭。、

---


### 文件流
| 分类 | 字节输入流 | 字节输出流 | 字符输入流 | 字符输出流 |
| --- | --- | --- | --- | --- |
| 抽象基类 | InputStream | OutputStream | Reader | Writer |
| 访问文件 | FileInputStram | FileOutputStream | FileReader | FileWriter |

这四个类都是节点流，即会直接和指定的文件关联，实例化时需要传入文件路径。
#### 练习案例
利用文件流中的字节流与字符流两种方式实现文件的拷贝。

- 字节流实现
```
/**
     * 字节流实现文件拷贝
     * @param srcFilePath 来源文件
     * @param destFilePath 目标文件
     */
    public static void copyFile(String srcFilePath,String destFilePath){
        try (FileInputStream fis = new FileInputStream(srcFilePath);
            FileOutputStream fos = new FileOutputStream(destFilePath);
        ){
            byte[] bytes = new byte[128];
            //实际读取的字节数
            int len = 0;
            //到文件末尾时len==-1
            while ((len=fis.read(bytes,0,128))>0){
                fos.write(bytes,0,len);
            }
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
```
**注意**：使用字节流处理文件时，其处理能力很强，但由于过程是以字节的方式读写文件数据,因此认为查看数据比较困难，没有下面的字符流方便。

- 字符流实现
```
/**
     * 字符流实现文件拷贝
     * @param srcFilePath 源文件
     * @param destFilePath 拷贝文件
     */
    public static void copyTextFile(String srcFilePath,String destFilePath){
        try(
                FileReader fr  = new FileReader(srcFilePath);
                FileWriter fw =  new FileWriter(destFilePath);
                ){
            char[] chars = new char[128];
            int len = 0;
            while((len = fr.read(chars,0,128))>0){
                /*将该字符数组从0开始，读取len个字符，并将其转为字符串*/
                //System.out.print(String.valueOf(chars,0,len));
                fw.write(chars, 0, len);
            }

        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
```
**注意**：字符流相比于字节流的优点在于其在处理文件数据的过程是以字符的形式，因此如果想查看其中的处理数据，打印即可，直接就是人们能阅读的字符，不足之处在于它不能处理字节类型的数据，比如处理图片等。

---


### 缓冲流
| 分类 | 字节输入流 | 字节输出流 | 字符输入流 | 字符输出流 |
| --- | --- | --- | --- | --- |
| 抽象基类 | InputStream | OutputStream | Reader | Writer |
| 缓冲流 | BufferedInputStream | BufferedOutputStream | BufferedReader | BufferedWriter |

**注意：**

1. 这四个类都是处理流，需要关联对应的节点流，即实例化时需要传入节点实例。
2. 缓冲流内部维护了一个缓冲区，通过与缓冲区得交互，减少与设备得交互次数。
3. 使用缓冲流时，它每次会读取一批数据将缓冲区填满，每次调用读取方法并不是直接从设备取值，而是从缓冲区取值，当缓冲区为空时，它会再一次读取数据，将缓冲区填满。
4. 使用缓冲输出流时，每次调用写入方法并不是直接写入到设备，而是写入到缓冲区，当缓冲区填满时它会自动刷入设备，也可以调用flush()方法触发刷入(关闭流时会自动调用它)。
```
public static void copyFile(String srcFilePath,String destFilePath){
        try(
                BufferedInputStream bis = new BufferedInputStream(new FileInputStream(srcFilePath));
                BufferedOutputStream bos = new BufferedOutputStream(new FileOutputStream(destFilePath));

        ){
        byte[] bytes = new byte[128];
        int len = 0;
        while((len=bis.read(bytes,0,128))>0){
            bos.write(bytes,0,len);

            }
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
```
基于缓冲流实现的copy方法。在处理比较大的文件时会占优势。

---


### 转换流
| 分类 | 字节输入流 | 字节输出流 | 字符输入流 | 字符输出流 |
| --- | --- | --- | --- | --- |
| 抽象基类 | InputStream | OutputStream | Reader | Writer |
| 转换类 |  |  | InputStreamReader | OutputStreamWriter |

将字节流转为字符流。
2个类都是处理流，需要关联对应的节点流，即实例化时需要传入节点流实例。
**Scanner**所提供的输入方法，其底层实现就是**InputStreamReader**类。
**PrintStream**所提供的输出方法，其底层实现就是**OutputStreamWriter**类。
基本使用：
```
public static void main(String[] args) {
        try(
            InputStreamReader r = new InputStreamReader(System.in);
            BufferedReader br = new BufferedReader(r);
                ){
            String line = null;
            while ((line= br.readLine())!=null){
                if(line.equalsIgnoreCase("exit")){
                    break;
                }
                System.out.println(line);
            }
        }catch (IOException e) {
            e.printStackTrace();
        }
    }
```

---


### 打印流
| 分类 | 字节输入流 | 字节输出流 | 字符输入流 | 字符输出流 |
| --- | --- | --- | --- | --- |
| 抽象基类 | InputStream | OutputStream | Reader | Writer |
| 打印流 |  | PrintStream |  | PrintWriter |

2个类都是处理流，需要关联对应的节点流，即实例化时需要传入节点流实例。
System.out就是**PrintStream**类型。
**PrintStream**、**PrintWriter**的功能和方法基本相同，后者的设计更合理。

---


- 使用示例：
```
public static void main(String[] args) {
        //testPrintStream();
        testprintWriter();
    }

    public static void testPrintStream(){
        try(
                FileOutputStream fos = new FileOutputStream("E:/Javas/demoFile/2.txt");
                PrintStream ps = new PrintStream(fos);
        ){
            //输出到文件
            ps.println("白日依山尽");
            ps.println("黄河入海流");
            ps.println("欲穷千里目");
            ps.println("更上一层楼");

        }catch (Exception e) {
            e.printStackTrace();
        }
    }

    public static void testprintWriter(){
        try (
                FileWriter fw = new FileWriter("E:/Javas/demoFile/3.txt");
                PrintWriter pw = new PrintWriter(fw);
                ){
            //输出到文件
            pw.println("白日依山尽");
            pw.println("黄河入海流");
            pw.println("欲穷千里目");
            pw.println("更上一层楼");
        }catch (Exception e) {
            e.printStackTrace();
        }
    }
```
![image.png](https://cdn.nlark.com/yuque/0/2023/png/35164588/1676292329507-e621f62d-95bc-47b9-9d31-2552d976acd7.png#averageHue=%232b2722&clientId=u959a413f-46fb-4&from=paste&id=u7b655ea6&name=image.png&originHeight=488&originWidth=1565&originalType=url&ratio=1.5&rotation=0&showTitle=false&size=187873&status=done&style=none&taskId=u28edf7e6-cf85-46a5-9139-4191e4b45ca&title=)

---


### 重定向
在Java中：

1. **System.in**代表标准输入，默认情况下代表键盘。
2. **System.out**代表标准输出，默认情况下代表显示器。

System类提供三个重定向方法。用于修改标准输入、输出、错误的目标设备。

- **public static void setIn(InputStream in)**
- **public static void setOut(PrintStream in)**
- **public static void setErr(PrintStream err)**
```
public static void testRedirectOutput(){
        try(
                PrintStream ps = new PrintStream(
                        new FileOutputStream("E:/Javas/demoFile/out.txt")
                )
                ){
            System.setOut(ps);
            System.out.println("生存还是死亡");
            System.out.println("这是一个问题");
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        }
    }

    public static void testRedirectInput() {
        try(
                FileInputStream fis = new FileInputStream("E:/Javas/demoFile/out.txt");
        ) {
            System.setIn(fis);
            Scanner scanner = new Scanner(System.in);
            while (scanner.hasNext()){
                System.out.println(scanner.next());
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
```

---


### RandomAccessFile
以下简称RAF

- RAF支持随机访问文件，即程序可以跳到文件任意位置来访问文件。
- RAF包含了丰富的功能，支持读取文件内容、支持向文件输出数据。
- RAF允许自由定位文件指针，该指针既可以向前移动，也可以向后移动。
   - long getFilePointer(),返回文件指针当前所指的位置。
   - void seek(long pos),将文件指针定位到指定位置(pos)。
- RAF包含输入和输出的方法，与**InputStream**和**OutputStream**类似。

简单使用
```
public static void main(String[] args) {
    try (
            //rw：读写模式
            RandomAccessFile raf = new RandomAccessFile("E:/Javas/demoFile/out.txt","rw");
            ){
        //定位到末尾
        raf.seek(raf.length());
        raf.write("欲穷千里目,\n".getBytes());
        raf.write("更上一层楼,\n".getBytes());
        //定位到开头
        raf.seek(0);
        String line = null;
        while ((line=raf.readLine())!=null){
            //String->bytes(UTF-8)
            //bytes->String(ISO8859-1)
            //String->bytes(ISO8859-1)
            //bytes->String(UTF-8)
            byte[] bytes = line.getBytes("ISO8859-1");
             line = new String(bytes, "UTF-8");
            System.out.println(line);
        }
    } catch (FileNotFoundException e) {
        e.printStackTrace();
    } catch (IOException e) {
        e.printStackTrace();
    }
    }
```

---


### 序列化
序列化机制可以将对象转为字节序列，这些字节可以保存在磁盘上。也可以在网络中传输，并允许程序将这些字节序列再次恢复成原来的对象。
#### 支持序列化

1. 若对象需要支持序列化机制，则它的类需要实现Serializable接口
2. 该接口时一个标记接口，它没有提供任何方法，只是标明该类可以序列化
3. Java的很多类以及实现了Serializable接口，如包装类、String、Date等。
#### 实现序列化
使用对象流ObjectInputStream和ObjectOutputStream（处理流）
##### 序列化
```
1. 创建ObjectOutputStream对象。
1. 调用该对象的writeObject()方法，以输出对象序列。
```
##### 反序列化

1. 创建ObjectInputStream对象。
2. 调用该对象的readObject()方法，将对象序列恢复为对象。
##### 练习

- 创建一个类实现Serializable接口。
```
class Car implements Serializable {
    private String brand;
    private String color;
    private int maxSpeed;

    public Car(String brand, String color, int maxSpeed) {
        this.brand = brand;
        this.color = color;
        this.maxSpeed = maxSpeed;
    }

    public String getBrand() {
        return brand;
    }

    public void setBrand(String brand) {
        this.brand = brand;
    }

    public String getColor() {
        return color;
    }

    public void setColor(String color) {
        this.color = color;
    }

    public int getMaxSpeed() {
        return maxSpeed;
    }

    public void setMaxSpeed(int maxSpeed) {
        this.maxSpeed = maxSpeed;
    }

    @Override
    public String toString() {
        return "Car{" +
                "brand='" + brand + '\'' +
                ", color='" + color + '\'' +
                ", maxSpeed=" + maxSpeed +
                '}';
    }
}
```

- 实现序列化
```
public static void testSerialize(){
        try (
                ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream("E:/Javas/demoFile/car.txt"));
        ){
            oos.writeObject(new Car("路虎","黑色",1000));
            oos.writeObject(new Car("奔驰","白色",1000));
            oos.writeObject(new Car("法拉利","黄色",1000));
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
```
执行之后的结果
![image.png](https://cdn.nlark.com/yuque/0/2023/png/35164588/1676292329433-8e1b364a-907e-41c5-be1e-04e4157846cc.png#averageHue=%23fbfccc&clientId=u959a413f-46fb-4&from=paste&id=u9ef33022&name=image.png&originHeight=410&originWidth=687&originalType=url&ratio=1.5&rotation=0&showTitle=false&size=40628&status=done&style=none&taskId=u60fc442f-5f41-4cce-a0c9-317001e31cb&title=)

- 实现反序列化
```
/**
     * 反序列化
     */
    public static void testDeserialize(){
        try (
                ObjectInputStream ois = new ObjectInputStream(new FileInputStream("E:/Javas/demoFile/car.txt"));
        ){
            System.out.println(ois.readObject());
            System.out.println(ois.readObject());
            System.out.println(ois.readObject());
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        } catch (ClassNotFoundException e) {
            e.printStackTrace();
        }
    }
```
执行之后的结果，将之前的乱码(相对是乱码)数据会重新还原。
![image.png](https://cdn.nlark.com/yuque/0/2023/png/35164588/1676292329584-77ed5f20-2dfb-45c5-a460-03373f4f4eaa.png#averageHue=%23222932&clientId=u959a413f-46fb-4&from=paste&id=u93bde7a9&name=image.png&originHeight=232&originWidth=1628&originalType=url&ratio=1.5&rotation=0&showTitle=false&size=253012&status=done&style=none&taskId=u2d88b691-8349-42ab-9ee6-d2cc02f49d8&title=)
#### 序列化规则
序列化的目的是将对象中的数据(成员变量)转为直接序列，和成员方法无关，为了正确的序列化某个对象，这个对象以及它对应的类需要符号如下规则：

- 该对象中引用类型的成员变量必须是可序列化的。
- 该类的直接或间接的父类，要么具有无参构造，要么也是可序列化的；
- 一个对象只会被序列化一次，再次序列化时仅仅输出它的**序列号**而已（会在序列化之前进行检查）。
#### 序列化版本

- 一个常见的场景

程序中以及定义了某个类：

1. 创建该类的实例，并将这个实例序列化，保存在磁盘上。
2. 升级这个类，例如增加、删除、修改这个类的成员变量。
3. 反序列化该类的实例，即从磁盘上恢复之前保存的数据。

定义类的序列化版本，在反序列化时，只要对象中所存的版本和当前类的版本一致，就允许做恢复数据的操作，否则会抛出序列化版本不一致的错误。

- Java允许以下形式来定义序列化版本：

private static final long serialVersionUID = ...;
如果没有显式的定义**serialVersionUID**,则JVM会根据类的信息自动计算出它的值，由于升级前后类的内容发生了变化，该值的计算结果通常不同，这回导致反序列化失败。所以如果有序列化的需求，最好显示的定义**serialVersionUID**的值。

- 演示

暂无！！！！

---


### Transient关键字
transient关键字用于修饰成员变量，表示序列化时将会忽略它。
transient关键字只能修饰成员变量，不能修饰成员变量，不能修饰类中的其他内容。

- 应用场景举例

在某些场景里，不希望序列化某个成员变量：

1. 该成员时敏感信息，如用户密码、银行账号等。
2. 该成员变量时引用类型，但他没有实现序列化接口。

    private transient String password;
### 自定义序列化
自定义序列化，可以让程序自主控制序列化以及反序列化成员变量的方式，可以通过在类中定义如下具有特殊签名的方法进行实现。

- 写入对象的成员变量

private void writeObject(ObjectOutputStream out) throws IOExecption;

- 恢复对象的成员变量
```
private void readObject(ObjectInputStram in)
throws IOException,ClassNotFountException;
```
## NIO
**NIO(New IO**)是Java从4开始陆续增加的IO处理的新功能。这些类都被放在java.nio包及其子包下，并且该包中很多类也以NIO为基础进行了改写。
NIO采用内存映射文件的方式来处理输入和输出，它将文件或文件的一段区域映射到内存中，这样就可以像访问内存一样来访问文件了，比传统的输入输出的方式要高效很多。
**Channel和Buffer是NIO的两个核心对象**：

- Channel(通道)是对传统的输入/输出系统的模拟，所有数据都要通过通道传输；
- Buffer(缓冲)是一个容器(数组)，是程序与Channel沟通的桥梁，程序向Channel写入的数据都要先放到Buffer中，程序从Channel中读取的数据也会被放到Buffer中。
### Buffer
**抽象类，它有如下子类：**

- ByteBuffer
- CharBuffer
- ShortBuffer
- IntBuffer
- LongBuffer
- FloatBuffer
- DoubleBuffer

**只能通过静态方法实例化Buffer:**
public static CharBuffer allocate(int capacity);
**Buffer的核心是4个成员变量：**

- 容量(capacity):可以存储的最大数据量，该值不可改变。
- 界限(limit)：Buffer中可以读/写数据的边界，limit之后的数据不能访问。
- 位置(position):下一个可以被读写的数据的位置(索引)
- 标记(mark):Buffer允许将位置直接定位到该标记处，这是一个可选的属性。

【注意】上述变量满足如下关系:
**0<=mark<=position<=limit<=capacity**

---



---


## 线程

- 进程

处于运行过程中的程序，具有独立的功能，是系统进行资源分配和调度的独立单位。
**独立性**
进程是系统中独立存在的实体，它拥有自己独立的资源，每一个进程都拥有自己独立的私有的地址空间，在没由经过进程本身允许的情况下，一个进程不能直接访问其他进程的地址空间。
**动态性**
进程是一个在系统中活动的指令集合，包含了事件的概念，具有自己的生命周期和状态。
**并发性**
在单个处理器上，多个进程可以并发的执行，并且执行时他们彼此之间不会互相影响。

- 并发和并行的区别

**并行**
在同一时刻，有多条指令在多个处理器上同时执行。
**并发**
在同一时刻，某一个处理器只能执行一条指令。
多个进程的指令可以被快速的轮换执行，使得宏观上具有多个进程同时执行的效果。

- 线程

线程扩展了进程的概念，使得同一个进程可以同时并发处理多个任务。
线程时进程的组成部分，一个进程可以拥有多个线程，一个线程必须有一个父进程。
线程不拥有系统资源，它与父进程里的一些其他线程共享父进程所拥有的全部系统资源。
_系统可以同时执行多个任务，每个任务就是进程_
_进程可以同时执行多个任务，每个任务就是线程_

- 线程的优点

**容易共享内存**
进程之间不能共享内存，但线程之间可以还很容易，因为与分隔的进程相比，线程之间的隔离程度要小，他们共享内存、文件句柄、其他每个进程应有的状态。
**运行效率高**
系统创建进程时要为其分配系统资源，但创建线程不需要，所以线程的运行效率更高。
**编程方式简单**
Java内置了多线程功能的支持，并不是简单的对操作系统底层进行调度，编程更方便。

---


### 线程的创建方式

- **Java的线程模型**
1. 使用Thread类代表线程，所有的线程对象都必须时Thread类或其子类的实例。
2. 线程用于完成一定的任务(执行一段程序流)，Java使用线程执行体来代表这段程序流。
3. 线程的使用过程：定义线程执行体>创建线程对象>调用对象的方法以启动线程。

对应上述过程，定义线程体的逻辑比较多，而后两者的步骤相对固定。

---


### 三种实现方式

- **继承Thread类**
1. 定义Thread类的子类，并重写该类的run()方法（线程体）。
2. 创建Thread类的子类的实例，即创建线程对象。
3. 调用线程对象的start()方法，即启动这个线程。
- **实现Runnable接口**
1. 定义Runnable接口的实现类，并实现该接口的run()方法（线程体）。
2. 创建Runnable实现类的实例，并以此作为target来创建Thread对象。
3. 调用Thread对象的start()方法来启动线程。
- **实现Callable接口**
1. 定义Callable接口的实现类，并实现该接口的call()方法（线程体）。
2. 创建Callable接口的实例，并使用Future接口来包装Callable对象，最后使用Future对象(线程的返回值)作为target来创建Thread对象。
3. 调用Thread对象的start()方法来启动线程。
4. 调用Future对象的get()方法获取线程的返回值。

---


### 三种方式的比较

- **继承父类的方式**

优点：编程比较简单；
缺点：线程类已经继承了Thread类，所以不能再继承其他的父类。

- **实现接口的方式**

优点：线程只实现了接口，还可以继承于其他的父类；
缺点：编程比较麻烦。

- **建议**

一般建议实现Runnable接口的方式，若需要获取返回值则采用实现Callable接口的方式。

---


### 简单演示
```
package Thread;

import java.util.concurrent.Callable;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.Future;
import java.util.concurrent.FutureTask;

/**
 * @author: Tisox
 * @date: 2022/2/23 16:05
 * @description:
 * @blog:www.waer.ltd
 */
public class Demo1 {
    public static void main(String[] args) throws ExecutionException, InterruptedException {
        //1.
//        new First().start();
//        new First().start();
        //2.
//        new Thread(new Second()).start();
//        new Thread(new Second()).start();
        //3.
        FutureTask<String> task0 = new FutureTask<String>(new Third());
        FutureTask<String> task1 = new FutureTask<String>(new Third());
        new Thread(task0).start();
        new Thread(task1).start();
        //阻塞方法
        System.out.println("返回值-0：\t"+task0.get());
        System.out.println("返回值-1：\t"+task1.get());

        //main默认为主线程
    }

    /**
     * 第一种实现方式
     */
    private static class First extends Thread{
        @Override
        public void run() {
            for(int i=0;i<10;i++){
                System.out.println(Thread.currentThread().getName() + "\t" + i);
            }
        }
    }

    /**
     * 第二种实现方式
     */
    private static class Second implements Runnable {
        @Override
        public void run() {
            for(int i=0;i<10;i++){
                System.out.println(Thread.currentThread().getName() + "\t" + i);
            }
        }
    }

    /**
     * 第三种实现方式
     */
    private static class Third implements Callable {
        @Override
        public String call() throws Exception {
                for(int i=0;i<10;i++){
                    System.out.println(Thread.currentThread().getName() + "\t" + i);
                }
            return Thread.currentThread().getName();
        }
    }
}
```

---


### 线程的生命周期
当线程被创建后，他不会立刻进入运行状态，也不会一直处于运行状态。
在线程的生命周期中，需要经过如下5种状态。

1. 新建(New)
2. 就绪(Ready)
3. 运行(Running)
4. 阻塞(Blocked)
5. 死亡(Dead)

![image.png](https://cdn.nlark.com/yuque/0/2023/png/35164588/1676292333084-fbf05ff5-d290-416b-bc03-8a86873688e8.png#averageHue=%23f8f8f8&clientId=u959a413f-46fb-4&from=paste&id=udf73cc77&name=image.png&originHeight=1072&originWidth=2535&originalType=url&ratio=1.5&rotation=0&showTitle=false&size=215416&status=done&style=none&taskId=uc96c11a2-c8c6-4f4f-b798-147b083facd&title=)

---


### 控制线程
#### 线程休眠

- **Thread**提供的休眠方法，可以让当前线程暂停一段时间。

```
static void sleep(long millis)
static void sleep(long millis,int nanos)
```

- **sleep()**VS**yield()**

前者会让线程进入阻塞状态，而后者会让线程进入就绪状态。另外，**sleep()**会给其他线程运行的机会，不理会其他线程的优先级，**yield()**考虑线程的优先级，只会给优先级相同，或者优先级更高的线程执行机会。
#### 等待线程
**Thread**类提供的等待方法， 可以调用方法等待该线程直它死亡。
```
void join()
void join(long millis)
void join(long millis,int nanos)
```

#### 后台线程
也叫守护线程，或者精灵线程；
它运行在后台，它的任务是为其他线程提供服务。
如果所有的前台线程都死亡了，则后台线程也会自动死亡。
线程默认是前台线程，Thread类提供如下方法来设置后台线程。
```
//设置为后台线程
void setDaemon(boolean on)
```
前台线程都死亡后，JVM会通知后台线程死亡，但是这个过程(从接收指令到做出响应)需要一定的时间。
#### 线程的优先级

1. 线程运行时拥有优先级，优先级高的线程则拥有较多的运行机会。
2. 线程默认的优先级与它的父线程相同，而主线程具有普通优先级。
3. **Thread**类提供了如下的成员，来处理线程的优先级。
```
static int MAX_PRIORITY;//10
static int MIN_PRIORITY;//1
static int NORM_PRIORITY;//5
int getPriority()//获取线程优先级
void setPriority(int newPriority)//设置一个新的优先级
```
线程的优先级需要操作系统的支持，尽管**Java**支持**10**中优先级，但是操作系统支持的优先级可能少于**10**中，所以最好不要通过具体数值的形式指定线程的优先级，而是通过采用静态变量来指定。
#### 示例
```
package Thread;

/**
 * @author: Tisox
 * @date: 2022/2/27 14:53
 * @description: 演示控制线程方式
 * @blog:www.waer.ltd
 */
public class Demo3 {
    public static void main(String[] args) throws InterruptedException {
       // testJoinThread();
        //testDaemonThread();
        testThreadPriroity();
    }
    private static class JoinThreadTask implements Runnable {
        @Override
        public void run() {
            for(int i = 0; i <30;i++){
                System.out.println(Thread.currentThread().getName() + "\t"+i);
            }
        }
    }

    /**
     * 线程等待
     * @throws InterruptedException ex
     */
    public static void testJoinThread() throws InterruptedException {
        //启动线程
        new Thread(new JoinThreadTask()).start();
        for (int i = 0; i < 30; i++) {
            System.out.println(Thread.currentThread().getName() + "\t\t"+i);
            if(i==10){
                //th0
                Thread thread = new Thread(new JoinThreadTask());
                thread.start();
                //main线程会等待th1线程执行结束之后再继续执行。
                thread.join();
            }
        }
    }

    /**
     * 演示后台线程
     */
    private static class  DeamdomThreadTask implements Runnable {
        @Override
        public void run() {
            for (int i = 0; i < 100; i++) {
                System.out.println(Thread.currentThread().getName() + "\t"+i);
            }
        }
    }

    /**
     * 测试后台线程
     */
    public static void testDaemonThread(){
        //后台线程
        Thread thread = new Thread(new DeamdomThreadTask());
        //注意：需要先设置为后台线程，再进行start()
        thread.setDaemon(true);
        thread.start();
        for (int i = 0; i < 10; i++) {
            System.out.println(Thread.currentThread().getName() + "\t\t"+i);
        }
    }

    private static class PriorityThreadtask implements Runnable {
        @Override
        public void run() {
            for (int i = 0; i < 10000; i++) {
                System.out.println(Thread.currentThread().getName() + "\t"+i);
            }
        }
    }

    public static void testThreadPriroity(){
        Thread thread0 = new Thread(new PriorityThreadtask());
        Thread thread1 = new Thread(new PriorityThreadtask());

//        System.out.println(Thread.currentThread().getPriority());
//        System.out.println(thread0.getPriority());
//        System.out.println(thread1.getPriority());
        thread0.setPriority(Thread.MAX_PRIORITY);
        thread0.start();
        thread1.setPriority(Thread.MIN_PRIORITY);
        thread1.start();
    }
}
```

---


### 解决线程安全问题
#### 线程同步

- 同步

对再一个系统中所发生的事件之间进行协调，再时间上出现一致性与统一化的现象。

- 加锁
- 加锁>修改>解锁
- 加锁机制可保障再任意时刻只有一个线程可以进入共享资源的代码区(临界区)
- synchronized
- 同步代码块

**synchronized(obj){....}**
**obj**代表锁定的目标(同步监视器)，它可以是任意的对象，考虑到它的作用，建议采用并发访问资源作为同步监视器。

- 同步方法

public synchronized void fun(){...}
无需显式指定同步监视器，再成员方法中它默认为this，在静态方法中它默认为当前的类。
**在同步代码块、同步方法执行结束，或者异常终止时，当前线程会自动解锁。**

- **synchronized的缺点**
1. 将加锁及解锁的过程固化了，便捷性有余，但灵活性不足。
2. 某个线程在访问同步代码时被阻塞了，其他线程只能等待，影响程序的性能。
3. 在访问共享资源时，对多个线程同时读的场景，实际不会产生任何冲突，但是**synchronized**不会区分这种场景，依然做加锁处理，还是会影响程序的执行效率。
#### Lock
| Lock(接口) |  |
| --- | --- |
| **void lock()** | 获取锁 |
| **void unlock()** | 释放锁 |
| **boolean tryLock(long time,TimeUnit unit)** | 获取锁，若超时则返回**false** |

| ReadWriteLock(接口) |  |
| --- | --- |
| **Lock readLock()** | 返回用于读取的锁 |
| **Lock writeLock()** | 返回用于写入的锁 |

**ReentrantLock**、**ReentrantReadWriteLock**分别是**Lock**和**ReadWriteLock**接口的常用实现类；
**ReentrantLock（重入锁）**,支持重新进入的锁，表示该锁可以支持一个线程对资源重复加锁。
**代码示例**

- 同步代码块
```
//通过校验，成功购票
            synchronized (this){
                this.amount -= amount;
                String name = Thread.currentThread().getName();
                System.out.println(name+"购买成功，剩余数量："+this.amount);
            }
```

- 同步方法
```
/*买票*/
        public synchronized void buy(int amount){
            if(this.amount<amount){
                throw new IllegalArgumentException("余票不足！");
            }
            //模拟数据校验花费的时间
            try {
                Thread.sleep(1);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            //通过校验，成功购票
            this.amount -= amount;
            String name = Thread.currentThread().getName();
            System.out.println(name+"购买成功，剩余数量："+this.amount);

        }
```

- 同步锁
```
private Lock lock = new ReentrantLock();
  public void buy(int amount){
            if(this.amount<amount){
                throw new IllegalArgumentException("余票不足！");
            }
            //模拟数据校验花费的时间
            try {
                Thread.sleep(1);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            lock.lock();
            try {
                //通过校验，成功购票
                this.amount -= amount;
                String name = Thread.currentThread().getName();
                System.out.println(name+"购买成功，剩余数量："+this.amount);
            }finally {
                lock.unlock();
            }
```
## 死锁
两个线程互相等待对方释放同步监视器时就会发生死锁，应该避免这种情况的发生。

- 避免多次锁定

尽量避免同一个线程对多个同步监视器进行锁定。

- 按相同的顺序加锁

如果多个线程需要对多个同步监视器加锁，则应该保证他们以相同的顺序请求加锁。

- 使用可以超时释放的锁

调用**Lock**对象的tryLock(time,unit)方法，当超过指定时间后它会自动释放锁。
**代码示例**
```
package Thread;

/**
 * @author: Tisox
 * @date: 2022/2/27 16:55
 * @description: 演示死锁
 * @blog:www.waer.ltd
 */
public class Demo5 {
    public static void main(String[] args) {
        String a = "A";
        String b = "B";
        new Thread(new FirstTask(a,b)).start();
        new Thread(new SecondTask(a,b)).start();
    }
    private static class FirstTask implements Runnable {
        private Object a;
        private Object b;

        public FirstTask(Object a, Object b) {
            this.a = a;
            this.b = b;
        }

        @Override
        public void run() {
            synchronized (a){
                try{
                    //do something
                    Thread.sleep(10);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }

                synchronized (b){
                    System.out.println("First");
                }
            }
        }
    }


    private static class SecondTask implements Runnable {
        private Object a;
        private Object b;

        public SecondTask(Object a, Object b) {
            this.a = a;
            this.b = b;
        }

        @Override
        public void run() {
            synchronized (b){
                try{
                    //do something
                    Thread.sleep(10);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }

                synchronized (a){
                    System.out.println("Second");
                }
            }
        }
    }
}
```
## 线程通信

1. 在某些业务中，A线程负责修改数据，B线程负责使用数据。
2. 在数据修改之前，B线程处于等待状态，直到得到A线程的通知
3. 在修改数据之后，A线程通过某种机制，通知B线程去使用数据。

线程通信的前提是要支持并发读写数据，所以线程通信前必须对共享资源进行加锁。

- **synchronized(obj)**下的实现
| Object |  |
| --- | --- |
| void wait() | 调用该方法的线程进入“等待”状态，并释放此对象的锁。 |
| void wait(long timeMillis) | 同上，但是最长等待**timeMillis**毫秒 |
| void notify() | 通知一个在此对象上等待的线程，使其从wait()返回 |
| void notifyAll() | 通知所有在对象上等待的线程，使其从wait()返回 |

```
package Thread;

/**
 * @author: Tisox
 * @date: 2022/2/27 17:36
 * @description: 演示线程通信[synchronized]：秒杀场景
 * @blog:www.waer.ltd
 */
public class Demo6 {
    public static void main(String[] args) throws InterruptedException {
        Product product = new Product(0);
        for (int i = 0; i < 100;i++) {
            new Thread(new BuyTask(product),"顾客"+i).start();
        }
        Thread.sleep(3000);
        new Thread(new SellTask(product),"卖家").start();
    }

    private static class Product{
        private  int amount;

        public Product(int amount) {
            this.amount = amount;
        }

        public int getAmount() {
            return amount;
        }

        public void setAmount(int amount) {
            this.amount = amount;
        }
    }

    private static class BuyTask implements Runnable {
        private Product product;

        public BuyTask(Product product) {
            this.product = product;
        }

        @Override
        public void run() {
            synchronized (product){
                String name = Thread.currentThread().getName();
                while (product.getAmount()==0){
                    try {
                        System.out.println(name+"已经做好装备，等待抢购....");
                        product.wait();
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                }
                product.setAmount(product.getAmount()-1);
                System.out.println(name+"抢到了一件商品，剩余库存,"+product.getAmount());
            }
        }
    }

    private static class SellTask implements Runnable {
        private Product product;

        public SellTask(Product product) {
            this.product = product;
        }

        @Override
        public void run() {
            synchronized (product){
                product.setAmount(10);
                String name  = Thread.currentThread().getName();
                System.out.println(name+"上架了10件商品，剩余库存"+product.getAmount());
                //通知所有买方
                product.notifyAll();
            }
        }
    }
}
```

- **Lock**下的实现

Condition condition = lock.newCondition();

| Condition(接口) |  |
| --- | --- |
| void await() | 调用该方法的线程进入“等待”状态 |
| void await(long time,TimeUnit unit) | 同上，但最长等待time时间，unit为时间单位 |
| void signal() | 唤醒一个在此Condition上等待的线程 |
| void signalAll() | 唤醒所有一个在此Condition上等待的线程 |

```
package Thread;

/**
 * @author: Tisox
 * @date: 2022/2/27 17:36
 * @description: 演示线程通信[synchronized]：秒杀场景
 * @blog:www.waer.ltd
 */
public class Demo6 {
    public static void main(String[] args) throws InterruptedException {
        Product product = new Product(0);
        for (int i = 0; i < 100;i++) {
            new Thread(new BuyTask(product),"顾客"+i).start();
        }
        Thread.sleep(3000);
        new Thread(new SellTask(product),"卖家").start();
    }

    private static class Product{
        private  int amount;

        public Product(int amount) {
            this.amount = amount;
        }

        public int getAmount() {
            return amount;
        }

        public void setAmount(int amount) {
            this.amount = amount;
        }
    }

    private static class BuyTask implements Runnable {
        private Product product;

        public BuyTask(Product product) {
            this.product = product;
        }

        @Override
        public void run() {
            synchronized (product){
                String name = Thread.currentThread().getName();
                while (product.getAmount()==0){
                    try {
                        System.out.println(name+"已经做好装备，等待抢购....");
                        product.wait();
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                }
                product.setAmount(product.getAmount()-1);
                System.out.println(name+"抢到了一件商品，剩余库存,"+product.getAmount());
            }
        }
    }

    private static class SellTask implements Runnable {
        private Product product;

        public SellTask(Product product) {
            this.product = product;
        }

        @Override
        public void run() {
            synchronized (product){
                product.setAmount(10);
                String name  = Thread.currentThread().getName();
                System.out.println(name+"上架了10件商品，剩余库存"+product.getAmount());
                //通知所有买方
                product.notifyAll();
            }
        }
    }
}
```
## 阻塞队列

- 某个模块负责生产数据，另一个模块负责处理数据。
- 产生数据的模块称为生产者，另一个称为消费者。
- 需要一个缓冲区位于生产者与消费者之间，作为沟通的桥梁。
- 生产者只负责把数据放入缓冲区，而消费者从其中取出数据。

**解决**

- BlockkingQueue

**Queue**的子接口。
有如下两个支持阻塞的方法
```
//尝试把元素e放入队列中，如果该队列元素已满，则阻塞该线程。
void put(E e)
```

## 线程组
**ThreadGroup**类代表线程组，它包含一批线程， 并对这些线程进行统一的管理
每个线程都有对应的线程组，若程序未显式的指定线程组，则该线程属于默认线程组。
默认情况下，子线程与它的父线程属于同一个线程组，而main线程则归属于main线程组。
一旦线程加入某个线程组，则该线程将一直属于这个线程组，中途不允许修改为其他线程组
### 创建线程组

- **ThreadGroup**的构造器
```
public ThreadGroup(String name)
public ThreadGroup(ThreadGroup parent,String name)
```

- **thread**的构造器
```
public Thread(ThreadGroup group,String name)
public Thread(ThreadGroup group,Runnable target)
public Thread(ThreadGroup group,Runnable target,String name)
```

- **ThreadGroup**中常用的处理线程的方法包括
1. 返回线程组名称
2. 返回当前线程组的父线程组
3. 中断此线程组中所有的线程
4. 设置(返回)线程组的最高优先级
5. 设置(返回)线程组为后台线程组

**UncaughtExceptionHandler**接口代表异常处理器，**Thread**类提供了set方法来指定该线程的异常处理器；
**ThreadGroup**类默认以及实现了这个异常处理接口，当一个线程抛出异常时，JVM会先查找该线程对应的异常处理器，若能找到则进行异常处理，否则JVM将调用该线程所属的线程组的方法来处理这个异常。
```
package Thread;

/**
 * @author: Tisox
 * @date: 2022/2/27 19:15
 * @description: 线程组
 * @blog:www.waer.ltd
 */
public class Demo8 {
    public static void main(String[] args) throws InterruptedException {
        //主线程的线程组
        ThreadGroup g = Thread.currentThread().getThreadGroup();
        System.out.println(g.getName()+","+g.isDaemon()+","+g.activeCount());
        //列出所有线程
        g.list();
        //子线程组
        Thread thread = new Thread(new ThreadTask());
        thread.start();
        System.out.println(thread);
        //自定义线程组
        g = new ThreadGroup("TEST");
        g.setDaemon(true);
        thread = new Thread(g,new ThreadTask());
        thread.start();
        System.out.println(thread);
        //销毁的后台线程组
        Thread.sleep(1000);
        System.out.println(g.isDestroyed());
        //异常处理器
        Thread.setDefaultUncaughtExceptionHandler(
                new Thread.UncaughtExceptionHandler(){
                    @Override
                    public void uncaughtException(Thread t, Throwable e) {
                        System.out.println(t+"->"+e);
                    }
                }
        );
        System.out.println(6/0);
    }

    private static  class ThreadTask implements Runnable {
        @Override
        public void run() {
            System.out.println(System.currentTimeMillis());
        }
    }
}
```

---


## 线程池
启动线程的成本相对较高，而通过线程池可以实现线程的复用，从而提高性能。
线程池可以控制程序中的线程的数量，避免超出系统负荷，导致系统崩溃。 

1. 创建线程池之后，它会自动创建一批空闲的线程。
2. 程序将线程体传给线程池，他就会启动一个空闲的线程来执行该线程体
3. 当线程体执行结束之后，该线程并不会死亡，而是变回空闲状态继续使用。
### 创建线程池

1. **ExecutorService**接口代表线程池；
2. **ScheduledExecutorService**是其子接口，代表可执行定时任务的线程池/
3. **Executors**是一个工厂类，该类包含了若干个静态方法，用来创建线程池：
```
ExecutorService newFixedthreadPool(int nThreads)
    ScheduleExecutorService newScheduleThreadPool(int corePoolSize)
```
### 使用线程池

- **ExecutorService**
- **ScheduledExecutorService**
```
package Thread;

import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.ScheduledExecutorService;
import java.util.concurrent.TimeUnit;

/**
 * @author: Tisox
 * @date: 2022/2/28 10:47
 * @description: 线程池
 * @blog:www.waer.ltd
 */
public class Demo9 {
    private static ExecutorService threadPool = Executors.newFixedThreadPool(3);
    private static ScheduledExecutorService scheduledPool = Executors.newScheduledThreadPool(3);

    public static void main(String[] args) {
        Runnable threadTask = new Runnable() {
            @Override
            public void run() {
                System.out.println(Thread.currentThread().getName() + "execute a thread task.");
            }
        };
        for (int i = 0; i < 10;i++) {
            threadPool.submit(threadTask);
        }

        Runnable schecduledTask = new Runnable() {
            @Override
            public void run() {
                System.out.println(Thread.currentThread().getName() + "execute a schecduledTask task.");
            }
        };
        //首次延迟5s,之后时间间隔3执行一次，时间间隔秒
        for (int i=0;i<5;i++){
            scheduledPool.scheduleAtFixedRate(schecduledTask,5,3, TimeUnit.SECONDS);
        }
    }
}
```
## ForkJoinPool

- **fork/join**是一种思想，旨在充分利用多核资源，用于执行并行任务。
- **ForkJoinPool**是**ExecutorService**的实现类，是上述思想的实现；
- 它的做法是，将一个大的任务分割为若干个小任务，最终汇总每一个小任务结果，从而得到大任务的结果。
### 创建**ForkJoinPool**

- 常用方法

public <T> ForkJoinTask<T> submit(ForkJoinTask<T> task){}

- **ForkJoinTask**
1. 代表一个可以执行的任务，是**Future**的实现类；
2. **RecursiveAction、RecuriveTask**是它的子类。
3. **RecursiveAction**代表没有返回值的任务，**RecursiveTask**代表有返回值的任务；
```
package Thread;

import java.util.concurrent.*;

/**
 * @author: Tisox
 * @date: 2022/2/28 11:33
 * @description:
 * @blog:www.waer.ltd
 */
public class Demo10 {
    public static void main(String[] args) throws ExecutionException, InterruptedException {
        int[] nums = new int[100];
        for(int i = 1;i<=100;i++){
            nums[i-1] = i;
        }
        ForkJoinPool pool  = new ForkJoinPool();
       Future<Integer> future =  pool.submit(new Fjtask(nums,0,nums.length-1));
        System.out.println(future.get());
    }

    private static class Fjtask extends RecursiveTask<Integer>{
        //拆解阈值
        private static final int THRESHOLD = 10;
        private int[] nums;
        private int start,end;

        public Fjtask(int[] nums, int start, int end) {
            this.nums = nums;
            this.start = start;
            this.end = end;
        }

        @Override
        protected Integer compute() {
            System.out.printf("%-25s\t%d,%d\n",Thread.currentThread().getName(),start,end);
            Integer sum = 0;
            if(end-start<THRESHOLD){
                for(int i = start;i<=end; i++){
                    sum += nums[i];
                }
            }else {
                int middle = (start+end)/2;
                Fjtask left = new Fjtask(nums,start,middle);
                Fjtask right = new Fjtask(nums,middle+1,end);
                left.fork();
                right.fork();
                sum = left.join()+right.join();
            }
            return sum;
        }
    }
}
```
## ThreadLocal
**ThreadLocal**是一个工具类，可以将数据绑定到当前线程之上，从而实现线程间数据的隔离；

- 将数据绑定当前线程之上

public void set(T value);

- 返回当前线程已经绑定的数据

public T get(){}

- 删除当前线程已绑定的数据

public void remove(){}

---


## 网络编程
### InetAddress类

- 获取本机InetAddress对象**getLocalHost**
- 根据指定的主机名或者域名获取ip地址对象**getByName**
- 获取**InetAddress**对象的主机名**gerHostName**
- 获取**InetAddress**对象的地址**getHostAddress**
```
// 代码演示
/*本机InetAddress对象*/
InetAddress localHost = InetAddress.getLocalHost();
/*沉迷代码日渐消瘦/192.168.74.48*/
System.out.println(localHost);

/*根据指定的主机名获取InetAddress对象*/
InetAddress host1 = InetAddress.getByName("沉迷代码日渐消瘦");
System.out.println("沉迷代码日渐消瘦的[InetAddress]对象："+host1);

/*根据域名返回InetAddress对象*/
InetAddress inetAddress = InetAddress.getByName("www.waer.ltd");
System.out.println("域名[www.waer.ltd]的[InetAddress]对象:"+inetAddress);

/*通过InetAddress对象获取对应的地址*/
String hostAddress = inetAddress.getHostAddress();
System.out.println("host2对应的[IP]："+hostAddress);

/*通过InetAddress获取主机名或者域名*/
String hostName = inetAddress.getHostName();
System.out.println("host2对应的主机名或者域名:"+hostName);
```
![image.png](https://cdn.nlark.com/yuque/0/2023/png/35164588/1676292333087-4d79cf52-506f-4cef-be74-02bac8813ab9.png#averageHue=%2324313d&clientId=u959a413f-46fb-4&from=paste&id=u701481b3&name=image.png&originHeight=177&originWidth=860&originalType=url&ratio=1.5&rotation=0&showTitle=false&size=235078&status=done&style=none&taskId=u94331359-bb79-4029-bc5b-5e93f2e6856&title=)

### socket的基本理解

- 套接字再开发网络应用程序中被广泛的使用，以至于称为了事实上的标准。
- 通信的两端都要有**socket**，。是两台及其间通信的断点。
- **socket**允许程序把网络连接当成一个流，数据再两个**socket**之间通过IO传输，
- 一般主动发起通信的应用程序属于客户端，等待响应的一端为服务端。

![image.png](https://cdn.nlark.com/yuque/0/2023/png/35164588/1676292338670-33a5e1a2-9204-4c64-9368-f3473857e423.png#averageHue=%23f9f7f7&clientId=u959a413f-46fb-4&from=paste&id=ub00056e1&name=image.png&originHeight=640&originWidth=1169&originalType=url&ratio=1.5&rotation=0&showTitle=false&size=136261&status=done&style=none&taskId=u45bd6d0c-d443-4e11-92bb-297e066ee8d&title=)
在两端的**socket**中都存在有
```
socket.getOutPutStream()
socket.getInputStream()
```
方法，当主机之间有数据传输需求时，会调用各自对应的输出或者输入流进行读写交互，完成数据的交流。
#### TCP网络通信编程-1

- 基于客户端-服务端的网路通信
- 底层使用的是TCP/IP协议
- 基于**Socket**的**TCP**编程
#### 应用案例

1. 编写一个服务端(A)和一个客户端(B)
2. 服务端监听9999端口
3. 客户端连接到服务器端，发送**hello ,server**，然后退出
4. 服务端接收到客户端发送的信息并输出该消息，退出。

**A端思路**

- 连接服务端(**IP**,端口)
- 生成**socket**,通过**socket.OutPutStream()**写入数据

**B端思路**

- 在本机的9999端口监听，等待连接
- 当没有接收到客户端连接时，程序阻塞，处于连接等待的状态。
- 通过**socket.getInPutStream()**读取客户端写入的(发送过来)的数据并显示。
#### 实现
**B端实现**
```
public static void main(String[] args) throws IOException {
    /*监听9999端口，等待连接，请确保该端口号没有被占用*/
    ServerSocket serverSocket = new ServerSocket(9999);
    System.out.println("服务B端在[9999]端口监听，等待连接...");
    /*如果有连接，返回socket对象，程序继续，否则阻塞*/
    Socket socket = serverSocket.accept();

    System.out.println("服务端[B]socket:"+socket.getClass());

    /*读取数据*/
    InputStream inputStream = socket.getInputStream();
    /*IO读取*/
    byte[] buf = new byte[1024];
    int len = 0;
    while ((len = inputStream.read(buf))!=-1){
        System.out.println(new String(buf,0,len));
    }
    /*关闭流*/
    inputStream.close();
    socket.close();
    serverSocket.close();
}
```
**A端实现**
```
public static void main(String[] args) throws IOException {
    /*连接本机9999端口*/
    Socket  socket = new Socket(InetAddress.getLocalHost(),9999);
    System.out.println("客户端[socket]返回:"+socket.getClass());

    /*写入数据*/
    OutputStream outputStream = socket.getOutputStream();
    outputStream.write("hello,server".getBytes());
    /*关闭资源*/
    outputStream.close();
    socket.close();
}
```
#### 案例扩展-1
在上面基础案例的基础之上，新建一个需求：当服务端接收到客户端消息时，应该给客户端一个回复内容，也就是完成一个交流的过程。
**B端实现**
```
public static void main(String[] args) throws IOException {
    /*监听9999端口，等待连接，请确保该端口号没有被占用*/
    ServerSocket serverSocket = new ServerSocket(9999);
    System.out.println("服务B端在[9999]端口监听，等待连接...");
    /*如果有连接，返回socket对象，程序继续，否则阻塞*/
    Socket socket = serverSocket.accept();

    System.out.println("服务端[B]socket:"+socket.getClass());

    /*读取数据*/
    InputStream inputStream = socket.getInputStream();
    /*IO读取*/
    byte[] buf = new byte[1024];
    int len = 0;
    while ((len = inputStream.read(buf))!=-1){
        System.out.println(new String(buf,0,len));
    }

    /*向客户端回复消息*/
    OutputStream outputStream = socket.getOutputStream();
    outputStream.write("hello,client".getBytes());
    socket.shutdownOutput();

    /*关闭流*/
    inputStream.close();
    outputStream.close();
    socket.close();
    serverSocket.close();
}
```
**A端实现**
```
public static void main(String[] args) throws IOException {
    /*连接本机9999端口*/
    Socket  socket = new Socket(InetAddress.getLocalHost(),9999);
    System.out.println("客户端[socket]返回:"+socket.getClass());

    /*写入数据*/
    OutputStream outputStream = socket.getOutputStream();
    outputStream.write("hello,server".getBytes());
    /*结束标记*/
    socket.shutdownOutput();
    /*接收来自服务端回复的消息*/
    InputStream inputStream = socket.getInputStream();
    byte[] buf = new byte[1024];
    int len = 0;
    while((len = inputStream.read(buf))!=-1){
        System.out.println(new String(buf,0,len));
    }
    /*关闭资源*/
    outputStream.close();
    inputStream.close();
    socket.close();
}
```
**注意点：**
在上面的程序中，如果我们不在数据读取和写入之后对服务的状态进行标识，此时双端都会出现一个等待的状态，而不是自动结束。所以需要加上:
```
socket.getOutputStream();
socket.getInputStream();
```
以保证程序正常运行。
#### 案例扩展-2
在前面的基础上，这里将字节流换为字符流进行读写数据。实现和扩展-1相同的功能。
**B端实现**
```
public static void main(String[] args) throws IOException {
    /*监听9999端口，等待连接，请确保该端口号没有被占用*/
    ServerSocket serverSocket = new ServerSocket(9999);
    System.out.println("服务B端在[9999]端口监听，等待连接...");
    /*如果有连接，返回socket对象，程序继续，否则阻塞*/
    Socket socket = serverSocket.accept();

    System.out.println("服务端[B]socket:"+socket.getClass());

    /*读取客户端法来的数据*/
    InputStream inputStream = socket.getInputStream();
    BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(inputStream));
    String s = bufferedReader.readLine();
    System.out.println(s);

    /*向客户端回复消息*/
    OutputStream outputStream = socket.getOutputStream();
    BufferedWriter bufferedWriter = new BufferedWriter(new OutputStreamWriter(outputStream));
    bufferedWriter.write("[字符流]hello,client,我是服务端啊");
    /*插入一个换行符，标识回复内容结束*/
    bufferedWriter.newLine();
    /*需要手动flush，否则可能无法将数据写入传输通道*/
    bufferedWriter.flush();

    /*关闭流:先打开的后关闭*/
    bufferedWriter.close();
    bufferedReader.close();
    socket.close();
}
```
**A端实现**
```
public static void main(String[] args) throws IOException {
    /*连接本机9999端口*/
    Socket  socket = new Socket(InetAddress.getLocalHost(),9999);
    System.out.println("客户端[socket]返回:"+socket.getClass());

    /*写入数据*/
    OutputStream outputStream = socket.getOutputStream();
    BufferedWriter bufferedWriter = new BufferedWriter(new OutputStreamWriter(outputStream));
    bufferedWriter.write("[字符流]hello,server.我是客户端啊");
    bufferedWriter.newLine();
    bufferedWriter.flush();
    /*结束标记*/
    socket.shutdownOutput();
    /*接收来自服务端回复的消息*/
    InputStream inputStream = socket.getInputStream();
    BufferedReader bufferedReader= new BufferedReader(new InputStreamReader(inputStream));
    String s = bufferedReader.readLine();
    System.out.println(s);
    /*关闭资源*/
    bufferedReader.close();
    bufferedWriter.close();
    socket.close();
}
```
**注意点:**
我们需要将从socket得到的输入输出流通过**InputStreamReader**或者**OutputStreamWriter**转换流进行转换之后放入**BufferedReader/Writer**字符流
在使用完毕之后需要对打开的资源进行关闭处理，遵循[**先打开的后关闭**]原则
### TCP网络通信编程-2
#### 应用案例

- 同样是编写两个端:服务端[B],客户端[A]
- 服务端在8888端口监听
- 客户端连接服务端，发送一张图片
- 服务端接收到客户端法来的图片并保存到src下的文件夹
- 客户端接收服务端发送的文本[收到图片]后退出
- 使用自定义工具类**StreamUtils.java**

**思路分析**

- 客户端从磁盘里通过输入流读取图片数据，
- 将图片数据以字节数组的方式写入数据通道
- 将数据发送到服务端
- 服务端通过socket得到一个输入流，将图片数据转为字节数组。
- 再将该数组通过输出流写入到目标路径即可。

**B端实现**

```java
public static void main(String[] args) throws IOException {
    //1.监听8888端口
    ServerSocket serverSocket = new ServerSocket(8888);
    System.out.println("[服务端]等待连接中.....");
    //2.接收连接
    Socket accept = serverSocket.accept();
    //通过socket得到输入流
    BufferedInputStream bis = new BufferedInputStream(accept.getInputStream());
    byte[] bytes = StreamUtils.streamToBytesArray(bis);
    //将得到的bytes数组写入到指定的路径，就可以得到一个文件了
    String destFilePath = "src\\可怜.jpg";
    BufferedOutputStream bos = new BufferedOutputStream(new FileOutputStream(destFilePath));
    bos.write(bytes);
    bos.close();
    /*向客户端回复"收到图片"*/
    BufferedWriter writer = new BufferedWriter(new OutputStreamWriter(accept.getOutputStream()));
    writer.write("我是[服务端]已收到图片!");
    writer.flush();
    accept.shutdownOutput();
    //关闭其他资源
    writer.close();
    bis.close();
    accept.close();
    serverSocket.close();
}
```

**A端实现**
```
public static void main(String[] args) throws IOException {
    //客户端连接服务端 8888，得到Socket对象
    Socket socket = new Socket(InetAddress.getLocalHost(), 8888);
    //创建读取磁盘文件的输入流
    //String filePath = "e:\\qie.png";
    String filePath = "e:\\temp\\可怜.jpg";
    BufferedInputStream bis  = new BufferedInputStream(new FileInputStream(filePath));

    //bytes 就是filePath对应的字节数组
    byte[] bytes = StreamUtils.streamToBytesArray(bis);

    //通过socket获取到输出流, 将bytes数据发送给服务端
    BufferedOutputStream bos = new BufferedOutputStream(socket.getOutputStream());
    bos.write(bytes);//将文件对应的字节数组的内容，写入到数据通道
    bis.close();
    socket.shutdownOutput();//设置写入数据的结束标记

    //=====接收从服务端回复的消息=====

    InputStream inputStream = socket.getInputStream();
    //使用StreamUtils 的方法，直接将 inputStream 读取到的内容 转成字符串
    String s = StreamUtils.streamToString(inputStream);
    System.out.println(s);


    //关闭相关的流
    inputStream.close();
    bos.close();
    socket.close();
}
```
## Java泛型
### 问题引入

1. 集合元素类型没有任何限制，可能不小心存入一个你并不期望的类型的数据，这会导致程序运行错误。
2. 当对象存入集合之后，集合丢失了对象的类型信息，统一的当作**Object**来处理，经常需要作强制类型转换。
3. 比如你需要往集合中存入一个**Dog**对象，当对象放入集合之后，再取出来就会被自动转为**Object**，从而丢失了原先的对象类型。
### 解决方案
为例解决上面的问题，从**Java5**之后，引入了**参数化类型**的概念。这种参数化类型被称为**泛型**
泛型允许在创建集合时指定集合元素的类型，则集合中只能保存这种类型的对象。
```
//Java5
List<String> list = new ArrayList<String>();
Map<String,Integer> map = new HashMap<String,Integer>();
//Java7之后
List<String> list = new ArrayList<>();
Map<String,Integer> map = new HashMap<>();
```
可以看到，上面两种方式都是泛型的表现形式，在**Java5**的版本中，使用泛型时必须在集合类型后面的**<>**中也指定相同
的类型参数。
而在**Java7**中去除了这一要求，只需要在开始的**<>**中进行参数类型的指定即可。这种新的方式被称为**菱形语法**。通过这种方式，就可以解决上面的问题了，我们需要什么类型就写什么类型，当再次取出时，类型不会被抹改。
### 代码demo
```
List<String> list  =   new ArrayList<>();
list.add("hello！");
//这里会报错，我们传入的泛型类型参数为String，而下面的尝试添加一个整型的元素，会报一个类型不兼容的异常。
list.add(3);
//会报错
java: 不兼容的类型: int无法转换为java.lang.String
```
当然，除了上面演示的**ArrayList**之外，其他类型的集合用法也是一样的。
```
Map<String,Integer> map = new HashMap<>();
Vector<Double> vector = new Vector<>();
Set<Float> set = new HashSet<>();
LinkedHashSet<String> linkedHashSet = new LinkedHashSet<>();
.....
```
### 泛型的定义
下面看一下**List**集合中泛型的定义是什么样的。
```
public interface List<E> extends Collection<E> {
 	boolean add(E e);
    Interator<E> iterator();
}
```
定义中，**List<E>**，传入的类型的一个**E**，这表示可以传入任意类型，**E**在这里仅仅是作为一个标识而已，具体的类型需要从我们实际的应用中去决定。同样，它里面的方法，比如**add()**和**iterator()**的定义也是类似的方式。
再看一下**Map**中的定义如下：
```
public interface Map<K, V> {
    	 V put(K key, V value);
		Set<Map.Entry<K, V>> entrySet();
}
```
同样这里也使用了类似上面的**E**的**K,V**来代表一个通用的类型参数。比如**put()**方法的返回值**V**，当我们给**Map**传入一个具体的类型的时候，这个**V**就会被具体的类型所替换。
### 自定义泛型类或接口
```
class Foo<T>{
    private T data;
    public Foo(T data) {
        this.data = data;
    }
    public T getData() {
        return data;
    }
}
```
如上，我们可以再定义类的时候通过一个通用标识来指定改类的泛型参数，比如这里用了**<T>**类型来代表该类可以支持传入任意类型的数据作为实参，也就是将参数从一中具象化转到抽象、笼统的层面。
通过这种方式声明的类型参数，可以在对应的类或者接口、方法中当作普通的类型来使用。类型形参将在声明变量、创建对象、调用方法时动态的指定。
为泛型定义子类时，不能在父类上包含类型形参，但可以包含类型实参，因为这种情况下，我们不是在定义父类，而是在使用父类，既然是使用，就需要传入实参。
```
//错误用法:这里的类型T应该传入一个具体的实际参数，而不是继续使用形参。
class Son extends Father<T>{}
```
```
//子类中T都将被替换成String类型
class Son extends Father<String>{}
```
```
//可以允许不为类型形参传入实参
class Son extends Father{}
```
注意这里这种方式，如果不指定实实参，参数类型会默认为**Object**。一切回到解放前。
注意泛型不是一个真实的类型，只是告诉编译器编译时需要检查<>中是什么类型的参数。本质还是一个基本的集合类型，并没有产生新的类型。
```
List<String> list1  =   new ArrayList<>();
List<Double> list2  =   new ArrayList<>();
//返回true
System.out.println(list1.getClass()==list2.getClass());
```
**String**是**Object**的子类，但**List<String>**不是**List<Object>**的子类。
这种关系其实本质还是**List**类型，并不是父子类的关系，也就还是回到上面提到的结论:**泛型不是真实的类型**。
### 类型形参的上限
上面已经知道，在传入类型参数的时候，我们可以通过一些通用的类型来标识它为一个泛型类型来表示可以传入任意类型的实参，比如**T**、**E**等等。但这里的**任意**些类型可以不是无限范围的,而是有一定规范的上限。
#### 类型形参的上限
class Foo<T extends Number>{}
上面的声明表示，我们传入的类型实参要么是**Number**类型，要么是该类型的子类，而不是任意类型。
#### 代码demo
```
package 泛型;

/**
 * @author: Tisox
 * @date: 2022/3/27 22:17
 * @description:
 * @blog:www.waer.ltd
 */
public class demo_3 {
    public static void main(String[] args) {
	//下面这一句代码将会报错
        First<String> first2 = new First("hello");
        First<Double> first3 = new First(100);

    }
}

class First<T extends Number>{
    private T data;

    public First(T data) {
        this.data = data;
    }

    public T getData() {
        return data;
    }

    public void setData(T data) {
        this.data = data;
    }

    @Override
    public String toString() {
        return "First{" +
            "data=" + data +
            '}';
    }
}
//异常信息
java: 类型参数java.lang.String不在类型变量T的范围内
```
#### 类型形参的下限
### 类型通配符
问号（**?**）在编程中被称为通配符。它代表一种未知的类型。通配符可以在各种情况下使用，如参数、字段或局部变量的类型；有时作为返回类型。与数组不同，泛型的不同实例之间是不兼容的，甚至不明确。如果**?**被用作实际的类型参数，这种不相容性可能会被通配符所缓和。
#### 通配符的上限
当你想放宽对一个变量的限制时，可以使用这些通配符。例如，假设你想写一个对List < Integer >、List < Double >和List < Number >起作用的方法，你可以用一个上界通配符来实现。要声明一个有上界的通配符，需要使用通配符('?')，后面是extends关键字，然后是它的上界。
public static void add(List<? extends Number> list)
看一个具体的例子：
```
import java.util.Arrays;
import java.util.List;

class WildcardDemo {
    public static void main(String[] args)
    {

        // Upper Bounded Integer List
        List<Integer> list1 = Arrays.asList(4, 5, 6, 7);

        // printing the sum of elements in list
        System.out.println("Total sum is:" + sum(list1));

        // Double list
        List<Double> list2 = Arrays.asList(4.1, 5.1, 6.1);

        // printing the sum of elements in list
        System.out.print("Total sum is:" + sum(list2));
    }

    private static double sum(List<? extends Number> list)
    {
        double sum = 0.0;
        for (Number i : list) {
            sum += i.doubleValue();
        }

        return sum;
    }
}
//输出
Total sum is:22.0
Total sum is:15.299999999999999
```
在上面的程序中，list1 和 list2 是 List 类的对象。 list1 是 Integer 的集合，list2 是 Double 的集合。它们都被传递给方法 sum，该方法有一个扩展为 Number 的通配符。这意味着传递的列表可以是该字段的任何字段或子类。就像这里，Integer 和 Double 是 Number 类的子类一样。
### 通配符的下限
使用通配符('**?**')表示，后面是super关键字，再后面是其下限。如**<? super A>**。
```
// Java program to demonstrate Lower Bounded Wildcards

import java.util.Arrays;
import java.util.List;

class WildcardDemo {
    public static void main(String[] args)
    {
        // Lower Bounded Integer List
        List<Integer> list1 = Arrays.asList(4, 5, 6, 7);

        // Integer list object is being passed
        printOnlyIntegerClassorSuperClass(list1);

        // Number list
        List<Number> list2 = Arrays.asList(4, 5, 6, 7);

        // Integer list object is being passed
        printOnlyIntegerClassorSuperClass(list2);
    }

    public static void printOnlyIntegerClassorSuperClass(
        List<? super Integer> list)
    {
        System.out.println(list);
    }
}
//输出
[4, 5, 6, 7]
[4, 5, 6, 7]
```
这里的参数可以是整数或整数的超类（即Number）。方法 printOnlyIntegerClassorSuperClass 将只接受 Integer 或其超类对象。但是，如果我们传递一个 Double 类型列表，那么我们将得到一个编译错误。这是因为只能传递 Integer 字段或其超类。 Double 不是 Integer 的超类。
注意：当你想从一个结构中取值时，请使用**extends**通配符；当你把数值放入一个结构中时，请使用**super**通配符。当你在一个结构中获取和放置值时，不要使用通配符。你可以为通配符指定一个上限，也可以指定一个下限，但你不能同时指定。
参考文章：[Wildcards in Java](https://www.geeksforgeeks.org/wildcards-in-java/)
### 泛型方法
就是在声明法时定义一个或多个类型形参：
修饰符 <S,T>返回值类型 方法名 (参数列表){...}

- 类型形参的声明放在方法修饰符和返回值类型之间；
- 类型形参的声明放在尖括号**<>**内，多个类型形参之间以逗号分隔；
- 调用方法时，无需显式的传入类型实参，编译器可以根据参数值自动推断。

考虑编写一这样一个方法，方法接受一个对象数组和一个集合，将数组中的所有对象放入集合中。你可能会写出下面的代码：
```
static void fromArrayToCollection(Object[] a, Collection<?> c) {
    for (Object o : a) { 
        c.add(o); // 编译错误
    }
}
```
方法试图使用Collection<Object>作为集合参数的类型。你可能已经认识到，使用Collection<?>也是不行的。回想一下前面的内容，我们不能把对象塞进一个未知类型的集合。
处理这些问题的方法是使用泛型方法。就像类型声明一样，方法声明也可以是泛型的，也就是说，通过一个或多个类型参数进行参数化。
```
static <T> void fromArrayToCollection(T[] a, Collection<T> c) {
    for (T o : a) {
        c.add(o); // 正确
    }
}
```
我们可以用任何一种元素类型为数组类型的超类型的集合来调用这个方法。
```
package 泛型;

import java.util.ArrayList;
import java.util.Collection;

/**
 * @author: Tisox
 * @date: 2022/3/28 9:39
 * @description: 泛型方法演示
 * @blog:www.waer.ltd
 */
public class GenericMethodTest {

    /**
     * 声明一个泛型方法，该方法中带一个T类型的参数
     * @param a a
     * @param c c
     * @param <T> T
     */
    static <T> void fromArrayToCollection(T[] a, Collection<T> c){
        for (T o : a) {
            c.add(o);
        }
    }

    public static void main(String[] args) {
        Object[] oa = new Object[100];
        Collection<Object> co  = new ArrayList<>();
        //自动推断T为Object类型
        fromArrayToCollection(oa,co);

        String[]  sa = new String[100];
        Collection<String> cs = new ArrayList<>();
        //自动推断T为String类型
        fromArrayToCollection(sa,cs);

        //自动推断T为Object
        fromArrayToCollection(sa,co);

        Integer[] ia = new Integer[100];
        Float[] fa = new Float[100];
        Number[] na = new Number[100];
        Collection<Number> cn = new ArrayList<>();

        //自动推断T为Number
        fromArrayToCollection(ia,cn);

        //自动推断T为Number
        fromArrayToCollection(na,cn);

        //自动推断T为Object
        fromArrayToCollection(na,co);

        //编译错误
        fromArrayToCollection(na,cs);
    }
}
```

---


[原文](https://www.nowcoder.com/tutorial/10001/f823027377ad4f4ea6b36fb9658b065b)

 
