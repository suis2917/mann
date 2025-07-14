#### 	项目-模块-包-类(代码)

#### 方法区(类)  栈内存 堆内存

**this指针

指向当前对象地址,用于获取当前对象

**ctrl + mouse1 查看源码**

**右键+generater+getter and setter 为所有成员变量生成getset方法

**static修饰的变量在类中公用  修饰的函数则不需要实例访问(工具化/私有化)



### 继承 

**关键字extends**

子类可以继承父类的非私有成员

**修饰符权限:**
<img src="C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20241206175235213.png" alt="image-20241206175235213" style="zoom:80%;" />

不支持多继承但是支持多层继承    都继承了object类(祖宗)

先访问子类再访问父类(重名优先找子类) 用super.来选择父类

**@override 方法重写  名称 形参需与父类一致 访问权限需大于父类 返回类型不变/更小   私有/静态方法不能被重写**

调用子类构造器会先调用父类构造器再调用自己
this()可调用兄弟构造器 (必须放第一行)



### 多态  (多态的实现依赖于继承)

![image-20241206192957842](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20241206192957842.png)

调用方法重名优先找子类  局部变量则找父类了(构造的是animal实例)

多态下不能调用子类独有功能(看左边)

![image-20241208135157961](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20241208135157961.png)

![image-20241208135414173](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20241208135414173.png)



### Final修饰类

final修饰的类不能再被继承 常用于工具类  修饰变量则不能再被修改 

修饰stactic变量则变为常量(建议使用全大写+下划线)  类似define宏替换

修饰引用类型的变量(数组等)则地址不能修改,地址指向的地方仍然能修改(a[2]=1**√**)



### 单例设计模式  (懒汉/饿汉  提前创建/需要时创建)

![image-20241208142309870](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20241208142309870.png)





### 枚举类 

适合信息分类和标志

![image-20241208143627221](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20241208143627221.png)



### 抽象类abstruct  匿名内部类(简单重写抽象类来创造一个实例)

![image-20241208193000192](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20241208193000192.png)

![image-20241208192949568](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20241208192949568.png)

![image-20250121130621399](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20250121130621399.png)



### 接口interface

接口仅能定义常量和抽象方法  可省略public abstruct会自动补全

![image-20241208194429900](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20241208194429900.png)

**注意事项:**

![image-20241208204044255](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20241208204044255.png)

JDK8以后可以将方法用default private stastic修饰

![image-20241208203523172](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20241208203523172.png)



##### 抽象类是整个事物的抽象,接口是行为的抽象



### 代码块

![image-20241209195616079](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20241209195616079.png)



### 内部类(匿名内部类)

成员内部类 静态内部类 匿名内部类

![image-20241209195808169](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20241209195808169.png)

![image-20241209200134089](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20241209200134089.png)

![image-20241209200245321](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20241209200245321.png)

![image-20241210124443895](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20241210124443895.png)

 ### lambda及其语法简化

![image-20241210131924034](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20241210131924034.png)**lambda的简化:**

![image-20241210143049142](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20241210143049142.png)

![image-20241210142844593](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20241210142844593.png)

![image-20241210143417426](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20241210143417426.png)

![image-20241210143429465](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20241210143429465.png)

![image-20241210145705078](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20241210145705078.png)

![image-20241212165853212](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20241212165853212.png)

![image-20241212165911193](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20241212165911193.png)

![image-20241212165935142](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20241212165935142.png)

![image-20241212165949782](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20241212165949782.png)

### Arraylist(类vector)

![image-20241212170124925](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20241212170124925.png)



### 泛型

![image-20241219185138496](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20241219185138496.png)

**E T K V 指代 element return key value**

![image-20241219185052416](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20241219185052416.png)

![image-20241219185030278](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20241219185030278.png)



### 包装类(万物皆对象)

可将常数包装成对象 相同常数对象地址相同 已有便捷数字-127到127的对象

![image-20241219185200271](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20241219185200271.png)

![image-20241219185356431](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20241219185356431.png)

![image-20241219185824045](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20241219185824045.png)



### 集合 类STL

![image-20241219185847949](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20241219185847949.png)

![image-20241219185900502](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20241219185900502.png)

#### 遍历方法

![image-20241219190640085](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20241219190640085.png)

![image-20241219190656809](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20241219190656809.png)

#### 增删并发修改异常

remove会使后面元素接上去,导致正常思想的遍历出现并发异常问题

解决方法:删除元素的同时i--  or倒着遍历  or基于迭代器it.remove() 



### List容器

Arraylist底层是数组(初始化数组大小为10,超出10则每次添加与原来相关的数,非线性)

Linkedlist底层是链表

![image-20241219200703976](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20241219200703976.png)

### Set 

Hashset底层是红黑树(排序)+数组+链表

Linkedhashset底层则多了一个双向链表使其有序  

Treeset需要排序函数(内置在类中)   可排序不重复无索引

![image-20241222154456216](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20241222154456216.png)

封装好的:

![image-20241222154905536](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20241222154905536.png)



### map

![image-20250116092407852](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20250116092407852.png)

![image-20250116092538005](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20250116092538005.png)

#### 遍历

用entry对象存key+value

![image-20250116100215952](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20250116100215952.png)

或lambda遍历:

![image-20250116100743321](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20250116100743321.png)

### Stream流

类似传送带方便遍历

![image-20250127190507579](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20250127190507579.png)

![image-20250203204435303](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20250203204435303.png)

![image-20250203205048121](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20250203205048121.png)

#### 常用方法

![image-20250203205557540](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20250203205557540.png)
