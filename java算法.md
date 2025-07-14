### 发现环(二维数组)

```java
import java.util.Scanner;
import java.util.LinkedList;
import java.util.*;
// 1:无需package
// 2: 类名必须Main, 不可修改

public class Main {
    public static void main(String[] args){
        Scanner scan = new Scanner(System.in);

        int N = scan.nextInt();
        // 用于记录某节点连接的所有节点
        ArrayList<Integer>[] edges = new ArrayList[N+1];
        // 记录每个节点的入度
        int[] degrees = new int[N+1];
        // 对边进行初始化
        for(int i = 1; i <= N; i++){
            edges[i] = new ArrayList<Integer>();
        }
        for(int i = 1 ; i <= N; i++){
            // 第一个节点值
            int from = scan.nextInt();
            // 第二个节点值
            int to = scan.nextInt();
            // 无向图，两边同时更新
            edges[from].add(to);
            edges[to].add(from);
            // 更新两边的入度
            degrees[from]++;
            degrees[to]++;
        }
        // 用于辅助遍历的队列
        LinkedList<Integer> queue = new LinkedList<>();
        for(int i = 1; i < degrees.length; i++){
            if(degrees[i] == 1) queue.offer(i);
        }
        while(!queue.isEmpty()){
            // 入度最小的元素出队
            int temp = queue.poll();
            // 更新相邻节点的入度
            for(Integer in : edges[temp]){
                degrees[in]--;
                if(degrees[in] == 1) queue.offer(in);
            }
        }

        ArrayList<Integer> ans = new ArrayList<>();
        // 剩余入度为2的点则为成环节点
        for(int i = 1; i < degrees.length; i++){
            if(degrees[i] == 2) ans.add(i);
        }
        // 对节点进行排序，按序输出
        Collections.sort(ans);
        for(Integer in : ans){
            System.out.print(in + "\t");
        }
        scan.close();
    }
}
```



### **3. 字符串和其他数据类型之间的转换**

Java 提供了工具类来帮助进行字符串和其他基本数据类型之间的转换。

#### **字符串转换为基本数据类型**

- **字符串转换为整数**：

  java复制

  ```java
  String str = "123";
  int num = Integer.parseInt(str); // 将字符串转换为 int
  ```

- **字符串转换为浮点数**：

  java复制

  ```java
  String str = "123.45";
  double num = Double.parseDouble(str); // 将字符串转换为 double
  ```

- **字符串转换为布尔值**：

  java复制

  ```java
  String str = "true";
  boolean bool = Boolean.parseBoolean(str); // 将字符串转换为 boolean
  ```





####  在 Java 中，将数值转换成字符串可以通过多种方式实现，以下是一些常用的方法：

1. **使用 `String.valueOf()` 方法**

   java复制

   ```java
   int number = 123;
   String str = String.valueOf(number);
   ```

2. **使用 `Integer.toString()` 方法**

   java复制

   ```java
   int number = 123;
   String str = Integer.toString(number);
   ```

3. **使用 `String.format()` 方法**

   java复制

   ```java
   int number = 123;
   String str = String.format("%d", number);
   ```



#### 使用 Collections.sort 方法和自定义 Comparator 对 List 进行降序排序

```java
        // 使用 Collections.sort 方法和自定义 Comparator 对 List 进行降序排序
        Collections.sort(numbers, new Comparator<Integer>() {
            @Override
            public int compare(Integer o1, Integer o2) {
                return o2.compareTo(o1);
            }
        });
```



#### 读取空格分隔的输入用next(),读取换行分隔的用nextline()

