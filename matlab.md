## ```matlab```笔记



- 变量赋值、运算同其他语言   clear清屏
- 注释为%    故取模需要用mod函数
- ```disp()```显示输出结果



- rand(m,n'数据类型‘)生成伪随机数m行n列矩阵  ```randn```同上并生成正态分布的伪随机数
- ```randi```([范围],m,n)可标定范围的随机矩阵



- 元胞数组(类对象) cell(行,列)      **下标从一开始**

  

- magic(n)生成n阶幻方

- 结构体struct(类python字典)

- ```matlab
  books = struct('name',{{'machine learning','data mining'}},'price',[30,40])
  book.name//提取字典值
  book.name(1)//取出的是cell'machine learning'
  book.name[1]//取出的是字符串machine learning
  ```



- 矩阵定义与构造

- ```matlab
  A = [1 2 3 4]
  B = 1:2:9 //1到9间隔2取值 B = 1 3 5 7 9 
  C = repmat(矩阵,行,列) //重复矩阵 行重复&列重复
  D = ones(2,4) //生成两行四列 所有值都为1
  A'  %矩阵转置
  A.*B%对应项相乘
  A./B%对应项相除
  inv(A)%矩阵求逆
  [D,V] = eig(A) %求特征值和特征向量
  C = A*B  %矩阵乘法
  C = A.*B  %按位乘
  X = A\B   %A的逆矩阵乘B,常用于求解AX=B
  %乘法符合广播原理
  ```
  
- 其他加减乘除相同



- 矩阵的下标
- 所有语言中冒号:为取得全部(python c++遍历)
``` matlab
 B = A(3:)
 [m,n] = find(A>20)   %找到分别的索引值(m,n)>20
```



- 遍历     **要写end**

  ```matlab
  for n = 1:5
  	sum = sum + n^2
  	end
  while n<=10
  	...
  	end
  if ...
  	...
  	else
  	...
  end
  ```
  



- 绘图

  hold on保存当前图像供后续修改  hold off不保存
  
  ```matlab
  figure %建立一个幕布
  plot(x,y) %绘制一个二维平面图
  title('加入标题')
  xlaber('x')
  ylabel('y')  %加入xy标签
  xlimit([左边界 右边界])  %加入范围
  使用set()可设置图线颜色,样式
  ```
  
- 三维立体绘图

  ```matlab
  plot3(三个参数)
  label设置同上
  grid on %加入网格线
  axis square %将轴变为正方形
  ```



- 图形的保存与导出

  编辑-->复制粘贴图形

  编辑-->导出(可选格式)-->导出设置-->设置长宽(可做到小图清晰)

<img src="C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20241130161050317.png" alt="image-20241130161050317" style="zoom:67%;" />
